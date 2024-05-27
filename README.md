![robot picture](/images/robot.png#pic_center)
# 企业级辅助编程开发机器人  
## 一、机器人使用方法:blush:  

![coze picture](/images/coze.png)

1、访问Coze国际版：www.coze.com  
:blush:
2、注册登录Coze平台  
:sunny:
3、在机器人商店Bot Store中搜索 BUG-Killer  
:cat:
4、点击机器人即可展开对话:blush:  
![UI picture](/images/UI.png)

5、直接在输入框输入要和机器人聊天的内容，生成代码，报错信息。  

6、界面下方提供了快捷键，可以一键查天气，查询论文和代码等。  

## 二、搭建方法
1、注册账号，登录  
2、创建机器人  
3、编写提示词  
4、添加插件  
5、设计工作流（可选）  
6、添加知识库（可选）  
7、添加数据库（可选）  
8、设置背景图片（可选）  
9、设置AI语音（可选）  
10、发布机器人  
11、添加机器人到聊天软件（可选，需要API）  

## 工作流中代码节点使用举例
对于如下一个查询论文的工作流：  
![code picture](/images/code.png)
其中```python```代码实现的细节如下：  
```python
async def main(args: Args) -> Output:
    params = args.params
    input0=params['input'][0]
    paper_title=input0['title']
    PDF_link=input0['resources'][0]['link']
    conf_title=input0['resources'][0]['title']
    cited_total=input0['inline_links']['cited_by']['total']
    summary=input0['publication_info']['summary']
    main_web=input0['link']
    
    ret: Output = {
        "key0":params['input'],
        "res":{
        "paper_title": paper_title,
        "conf_title":conf_title,
        "PDF_link":PDF_link,
        "main_web":main_web,
        "cited_total":cited_total, 
        "summary":summary,    
        },
    }
    return ret
```
实现的功能是过滤返回信息中的主要信息。
