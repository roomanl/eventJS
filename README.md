# eventJS
使用JS在多个页面之间互相通信和调用。<br> 
iframe与iframe之间的页面可以互相通信调用。浏览器每个标签页之间的页面也可以互相通信调用。

## 需求：
例如：打开了A,B,C三个标签页，我在C页面把数据修改了，我要通知A,B两个页面的数据也要更新到最新修改的数据。

## 用法：
1、在A,B,C三个页面引入event.js <br> 
2、然后在A,B页面添加监听事件 <br> 

```JavaScript
    Evt.addEvent('addUser',function(key,data){
        console.log(data);
    });
    Evt.addEvent('deleUser',function(key,data){
        console.log(data);
    });
```
3、C页面对数据进行了修改后就发一个通知给A,B页面，让A,B页面进行相应的操作 <br> 

```JavaScript
    Evt.sendEvent('addUser','新增了一个用户');
    Evt.sendEvent('deleUser','删除了一个用户');
 ```
## 注意：
1、 互相通信调用之间的几个页面要放在服务器环境，例如放在IIS或者tomcat之类的服务容器里。<br> 
2、 打开的几个页面要是同源页面，也就是几个页面之间IP相同，端口相同。<br> 
3、 打开的几个页面必须是在同一个浏览器。<br> 
4、 发送通知传的参数现在还只能是字符串，如果要传JSON类型，请先在C页面转字符串，在A,B接收到通知后，再把字符串转回JSON。<br> 
5、 同一个页面接收不到同一个页面发送的通知，当然谁也不会做这种事，在同一个页面接收同一个页面发送的通知。