"""
网址:http://www.yidianqiuxun.com/?s=要搜索的东西
第一个歌谱的位置://*[@id="main"]/ul/li[2]/a
图片位置:/html/body/div[1]/div[2]/div[1]/main/article/div/div[2]/p/img
"""
from requests import *
from lxml import etree
response=get("http://www.yidianqiuxun.com/?s=%s"%input("请搜索歌谱>>>"))
song=[]
song_text=[]
html=etree.HTML(response.text)
html=html.xpath("//*[@id='main']/ul//li/a/@href")
for a in html:
       song.append(a)
html=etree.HTML(response.text)
html=html.xpath("//*[@id='main']/ul//li/a/text()")
n=1
for a in html:
       print(n,".",a)
       song_text.append(a)
       n+=1
number=int(input("请输入序号>>>"))-1
response=get(song[number])
html=etree.HTML(response.text)
get_img=html.xpath("/html/body/div[1]/div[2]/div[1]/main/article/div/div[2]/p/img/@src")
response=get(get_img[0])
with open("%s.jpg"%song_text[number],"wb")as image:
       image.write(response.content)

