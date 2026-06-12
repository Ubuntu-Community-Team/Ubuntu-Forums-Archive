---
title: "Some special settings for Ubuntu - for WordPress site?"
date: 2020-06-24
forum: General Help
---

### Post by dimonikolow133 on 2020-06-24
Hello, all!


I am going to install Ubuntu for first time on my own personal server.


According to this article -  [https://www.scalahosting.com/blog/nginx-vs-apache/](https://www.scalahosting.com/blog/nginx-vs-apache/)  - Ngnix is faster than Apache but for static content.


I am more familiar with Apache so I will use Ubuntu for one new WordPress site


WordPress  is dynamic web content platform, so in this case it never mind what kind of server you use /Ngnix or Apache/.  


As I said I am familiar with Apache server /hosting/ so I do this steps  to speed up the web-site:  



[LIST]
[*]Use .htaccess code to cache and gzip/deflate resources like .CSS .JS images icons etc. - no plugins needed (you can find such code with Google)
[*]Use proper image size, optimize them with Smush plugin or with Tiny JPG / PNG tool
[*]Clear all the comments in the HTML code, if possible
[/LIST]




I also found this article how to install Apache  properly on Ubuntu.


[https://ubuntu.com/tutorials/install-and-configure-apache#1-overview](https://ubuntu.com/tutorials/install-and-configure-apache#1-overview)




**My Question is - do I need some special settings so my WordPress website to work properly?**


Thank you in advance.

---

### Post by dragonfly41 on 2020-06-24
I find that [digitalocean is a good source of tutorials]("https://www.digitalocean.com/community/tutorials?q=wordpress").
You might explore the role of ansible scripts for deployment.

You do not write where you will host the server.

---

