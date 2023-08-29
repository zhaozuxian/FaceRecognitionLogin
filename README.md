# FaceRecognitionLogin
This project is used to achieve the function of users' login.
<center>
    <h1>web客户端人脸识别登录系统</h1>
</center>


## 思路

* 登录页面的html，css布局。

  * 登录(username、password两个输入框，video，canvas，登录按钮)

    * 账号登录（username、password两个输入框，登录按钮）   /userLogin
      * 通过与数据库里的username和password进行比对，来完成登录
    * 人脸登录                 /faceLogin
      * 通过浏览器相关api打开本地摄像头
      * 把视频流传给*video*标签播放出来
      * 通过canvas进行图片截取,不断生成图片
      * 将截取的图片发送给后端进行*人脸*比对
      * 登陆成功
  * 注册(username、password   confirmpwd三个输入框，video，canvas，打开摄像头按钮，拍照按钮，注册按钮)
  
    * 打开摄像头（用浏览器相关的api接口）
    * 进行拍照（用画布canavas）
    * 将照片以base64格式存入后端数据库
    * 向后端发送的数据用FormData进行封装post  /register    {username:' ',password:' ', img：' '}
    * 完成注册
  
* 后端（flask）

  * 建立数据库
    * 登录表（login）
      * username:string
      * password:string
      * imgPath: string

  *  接口   /register   post  
    * 将前端传来的数据信息保存在数据库里边   {username:' ',password:' ', img：' '}
    * 图片base64转换为jpg格式，并把图片路径存在数据库里
    * 完成注册功能（给前端返回注册成功的json请求）

  *  接口   /userLogin  post
    * 获取前端信息
    * 从数据库里获取相应的信息
    * 进行信息比对
    * 给前端发送json信息（登录成功、登录失败）

  * 接口     /faceLogin     post  
    * 将前端发送来的base64的图片信息jpg格式
    * 对人脸信息与所有的人脸图片进行比对 
    * 完成登录

* 图片的人脸识别（opencv）

  * 
  
  
  
  



## 前端环境

* tracking-min.js   
* face-min.js
* jquery-3.2.1.min.js





## 后端环境

* pip install Flask==1.1.4
* pip install pymysql==1.0.2
* pip install Flask-SQLAlchemy==2.5.1
* pip install markupsafe==2.0.1
* pip install SQLALchemy==1.4.32 
* pip install flask-cors==4.0.0  )(重点写)
* pip install opencv-contrib-python
* pip install  opencv-python 



## 问题

* flask解决跨域问题
