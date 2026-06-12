---
title: "Kubuntu - Resolution and Nvidia"
date: 2007-05-06
forum: General Help
---

### Post by LollYouSuckZor on 2007-05-06
We'll I had changed my video settings, but im not sure what kind of Nvidia video card I have.. ( A friend sold it to me. )   Before I changed these settings the resoloution was 1024 x 768, The way I like it.  
Now that I have changed it, the resoloution is somewhere around 640 x (xxx).  
Right now im on my laptop, because my computer dosent have an internet connection for a little bit.  What can I do?  I want the Nvidia Geforce 5200 card to work with the Kubuntu.. and I want my resooution back :(

---

### Post by ZeroWing on 2007-05-06
> **LollYouSuckZor said:**
> We'll I had changed my video settings, but im not sure what kind of Nvidia video card I have.. ( A friend sold it to me. )   Before I changed these settings the resoloution was 1024 x 768, The way I like it.  
Now that I have changed it, the resoloution is somewhere around 640 x (xxx).  
Right now im on my laptop, because my computer dosent have an internet connection for a little bit.  What can I do?  I want the Nvidia Geforce 5200 card to work with the Kubuntu.. and I want my resooution back :(

 Sold it to you... I want my money!

 try reconfiguring Xorg:

 ```
sudo dpkg-reconfigure xserver-xorg
```

 You need to type that in a terminal. Forgot where it was in Kubuntu.

---

### Post by LollYouSuckZor on 2007-05-06
W00t i have no idea what that is.

---

### Post by ZeroWing on 2007-05-06
> **LollYouSuckZor said:**
> W00t i have no idea what that is.

 Start menu ---> System ---> Terminal. Or konsole. Copy and paste that lettering in my last post in this topic.

---

### Post by LollYouSuckZor on 2007-05-06
Okay, Well I did that, but when it asks for my password, I cant put it in.  

YES My keyboard is plugged in.  But It wont let me type my pw in.

---

### Post by ZeroWing on 2007-05-07
> **LollYouSuckZor said:**
> Okay, Well I did that, but when it asks for my password, I cant put it in.  

YES My keyboard is plugged in.  But It wont let me type my pw in.

 Oh!

 Just type in your account password. It won't show anything, but it's being typed.

---

### Post by LollYouSuckZor on 2007-05-07
It still says


Debconf: dbdriver "config": /var/cache/debconf/config.dat is locked by another process


Ftw.

---

### Post by LollYouSuckZor on 2007-05-07
Should I just put the CD back in and basically Reinstall it?

---

### Post by Scheater5 on 2007-05-07
I wouldn't recommend that just yet, but that's a potential option.  Try it with the terminal again.  Kmenu->System->Konsole, and then enter the command ZeroWing gave you.  Make sure System Settings or KControl are not open (they could be using debconf).  It will prompt you for a password.  At this point when you type you won't see it, but it will still recognize that you are typing.

---

### Post by ZeroWing on 2007-05-07
> **Scheater5 said:**
> I wouldn't recommend that just yet, but that's a potential option.  Try it with the terminal again.  Kmenu->System->Konsole, and then enter the command ZeroWing gave you.  Make sure System Settings or KControl are not open (they could be using debconf).  It will prompt you for a password.  At this point when you type you won't see it, but it will still recognize that you are typing.

 Basically- talk to other people about Kubuntu-related stuff. I use GNOME, because it's easier to customize, in my opinion, and a good start for a desktop manager, also in my opinion.

---

