---
title: "Forget password"
date: 2014-12-16
forum: General Help
---

### Post by suen123 on 2014-12-16
Hi, 

I forget my user password, so I tried to reset it by using: 

1. recovery mood
2. root
3. mount -o rw, remount /

However when I typed ls /home/, instead of my user name, it showed "ubuntu". Can someone please teach me how to fix it? 

Thank you very much! 
Sally

---

### Post by CantankRus on 2014-12-16
Looks more like your booting with the live CD not to recovery mode.
Boot normally (without CD/usb) and at the grub screen choose **advanced options** then **recovery mode**.
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

Another link with pics...
[**_[COLOR="#B22222"]How to reset your password in Ubuntu[/COLOR]_**]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by suen123 on 2014-12-16
Hi CantankRus.

thanks for your quick reply. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) (Another link with pic) is the one I followed. But when I typed ls /home, only "Ubuntu" showed up, instead of my user name "suen". I attached the screenshots and hope this will help. 

Thanks!!! =) 
Sally


[ATTACH=CONFIG]258628[/ATTACH]

[ATTACH=CONFIG]258627[/ATTACH]

[ATTACH=CONFIG]258626[/ATTACH]

---

### Post by CantankRus on 2014-12-16
A live CD/usb uses an "**ubuntu**" home directory.
The **ls /home** command is how you find the user account folders if you can't remember username as well as password.
eg for me ...
```
[COLOR="#006400"]glen@Trusty:~$[/COLOR] **ls /home**
glen
```
 
Have you ever logged on to this account before or did you forget the 
password made during installation?
What iso did you use to install in virtual box?

---

### Post by suen123 on 2014-12-17
Hi CantankRus,

Thank you so much! I figured it out. It is a silly misunderstanding, my user acc is "Ubuntu", and "suen" is just a greeting name. So when I followed the website using "ubuntu" as my user account, I could change the password easily! Thanks for you help!! =) 

Sally

---

### Post by CantankRus on 2014-12-17
Ok, please mark solved in "Thread Tools" at top right.

---

