

## What is this for

利用ChatGPT，输入一个名称清单列表，自动生成多篇主题文章
【Using ChatGPT, enter a list of names and automatically generate multiple articles with given themes】

power by pyChatGPT: https://github.com/terry3041/pyChatGPT 


## How to prepare to use

At first, you should get the library `pyChatGPT` and `python-docx`. 
Second, you should find your token from your Chorme browser and copy it into file `token.txt`

You can choose any one of the fllowing way to get `pyChatGPT`

#### get the pychatGPT and python-docx from pip (recommended)

If you don't have Internet problem,just use  
`python -m pip install pychatGPT python-docx`

If you are in China with Internet problem, try the tips below:

常用的镜像地址有： 

1)http://mirrors.aliyun.com/pypi/simple/    阿里云

2)https://pypi.mirrors.ustc.edu.cn/simple/ 中国科技大学

3) http://pypi.douban.com/simple/    豆瓣

4) https://pypi.tuna.tsinghua.edu.cn/simple/   清华大学

5)  http://pypi.mirrors.ustc.edu.cn/simple/ 中国科学技术大学

--trusted-host pypi.douban.com    表示将指定网站设置为信任服务器

执行如下命令：
` python -m pip install -U pychatGPT python-docx -i http://pypi.douban.com/simple --trusted-host pypi.douban.com`



#### get pyChatGPT directly from github

* If you don't have Internet problem
  just use
  `git clone https://github.com/terry3041/pyChatGPT` to get the source code of pyChatGPT library.
* Tips for Chinese with Internet problem    
你需要一个科学的系统代理，如果还不行可以设置一下git
git config --global https.proxy http://127.0.0.1:7890
git clone https://github.com/terry3041/pyChatGPT 
git config --global --unset https.proxy

http协议则把上述的换成http即可



And then enter the pyChatGPT source code directory and install it
`python -m pip install . -i http://pypi.douban.com/simple --trusted-host pypi.douban.com`



### how to get token

在本项目目录下新建一个token.txt文件，打开浏览器登录进去chatgpt 然后 F12 -》应用-》 cookies -》 找到 __Secure-next-auth.session-token的值 -》复制到 token.txt
【Create a new token.txt file in this project directory, open the browser and log in to chatgpt, then do: F12 -> Application -> cookies -> Find the value of "__Secure-next-auth.session-token" -> Copy to token.txt】


## How to use

1. prepare a csv file with all your article titles (with id column), for example
>   id title
>   1  Helloworld
>   2  Today is a good day

2. set the necessary path

modified line 41:

```
baseoutput='./outputs'
titledir=opj(baseoutput,'任务单')

```
baseoutput means where do you want your output articles put.
**titledir means where do your title csv file put.**
By default, titledir in a sub dir '任务单' of baseoutput.


3. run

`python interface.py`

program will find the latest csv file, and produce articles in the dir of output dir named by date.

of cource you can change the prompts to make your style article, 
prompts in line 126:

```
try:
    resp = api1.send_message('请写一篇不少于800字的文章，但是内容形式和结构不要太单调，最好有一定的长度和深度，不要涉及政治。'
        '可以分小节论述，但是“小节一”、“小标题”之类的词语不要出现。'
        '不用说其他无关的话，大部分用中文，文章里不可以出现网址链接，如果写完了请在末尾加‘#123456’。'
        '文章的主题是: '+title)
```
you can change the descriptions.



