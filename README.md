# #coding=utf-8
import re
import urllib
 
 
for j in range(22):
    if j==0:
        print('开始爬取图片..')
        url='http://www.woyaogexing.com/touxiang/z/ktkeai/index.html'
        print('******************************************')
        print('正在爬取第1页..')
    elif j==1:
       pass
    else:
        url='http://www.woyaogexing.com/touxiang/z/ktkeai/index_%d.html'%(j)
        print('******************************************')
        print('正在爬取第%d页..'%(j))
         
    page=urllib.request.urlopen(url)
    html=page.read().decode('utf-8')
    reg='''<img class="lazy" src="(.*?)"'''
    htmls=re.findall(reg,html) 
 
    for i in htmls:
        print('正在保存..%s'%i.split('/')[-1])
        urllib.request.urlretrieve(i,'%s'%i.split('/')[-1])
             
print('******************************************')
print('爬取完成..')
