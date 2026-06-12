---
title: "Jquery Question"
date: 2019-01-15
forum: General Help
---

### Post by shane_faulkinbury2 on 2019-01-15
I just downloaded jQuery 3.3.1.js to my Downloads folder and I'm trying to install it.  I however am having a problem.  I look in the file, but there is no how to install it.  Can somebody help me out?


```
sup@sup-HP-Compaq-8200-Elite-SFF-PC:~$ cd Downloadssup@sup-HP-Compaq-8200-Elite-SFF-PC:~/Downloads$ ./jquery-3.3.1.js
bash: ./jquery-3.3.1.js: Permission denied
sup@sup-HP-Compaq-8200-Elite-SFF-PC:~/Downloads$ sudo su
[sudo] password for sup: 
root@sup-HP-Compaq-8200-Elite-SFF-PC:/home/sup/Downloads# ./jquery-3.3.1.js
bash: ./jquery-3.3.1.js: Permission denied



```

---

### Post by aktiwers on 2019-01-15
You don't install it. Include it in your html file and start using it [https://www.w3schools.com/jquery/jquery_get_started.asp](https://www.w3schools.com/jquery/jquery_get_started.asp)

---

### Post by shane_faulkinbury2 on 2019-01-17
Maybe I should have been clear, in the past I just installed it from Ubuntu Software, but since it's no longer available on there I went to their website and downloaded the package.  I know have the .js file and wish to install it.

---

### Post by aktiwers on 2019-01-17
What do you mean by "installing it" ?

It is a javascript library - you don't and can't install it. It is as is.

If you want it in another location, simply copy/paste the file to that location and start using it.

If you installed it from the software center in the past, it simply downloaded that javascript file and placed it in some location for you. Maybe in /var/www/html or something like that.

---

### Post by dragonfly41 on 2019-01-17
This might help .. [tutorial]("https://www.w3schools.com/jquery/jquery_intro.asp")

---

### Post by shane_faulkinbury2 on 2019-01-18
Thanks all.

---

