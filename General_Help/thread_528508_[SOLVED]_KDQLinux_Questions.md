---
title: "[SOLVED] KDQ/Linux Questions"
date: 2007-08-17
forum: General Help
---

### Post by Road_kill on 2007-08-17
First, sorry I spelled KDE as KDQ. I don't know how to change it.
Now to my questions:

Hello guys, I had certain questions I wanted to ask which I could not find online.

1. What is the benefit of applications made for KDE? Eg. what is the difference between KOffice and OpenOffice.
Are the KDE applications faster or something?

2. I find that the readability in Firefox/Konquerer is far less in KDE than GNOME. Everything seems so small in its default condition and jaggy. Does anyone else feel this? Is there any solution aside from going to configure each application?
I like the default Sans Serrif with size 9, but in web browsers, it doesn't use that Sad

3. I have a network drive which is Windows based. I currently only have a link that goes to it. However, is it possible to "mount" it?
For example, at the moment to get to it, I do the following. smb://192.168.1.101
Is there anyway to make it like a real drive, like Windows and its network drive mapping?

Thank you for your help in advance.

---

### Post by der_joachim on 2007-08-18
> **Road_kill said:**
> 
1. What is the benefit of applications made for KDE? Eg. what is the difference between KOffice and OpenOffice.
Are the KDE applications faster or something?


Some people seem to think that QT apps are prettier. QT is the underlying graphical library for KDE, just as GTK is the underlying graphical library for Gnome and XFCE. QT apps are somewhat faster in KDE, while GTK apps work better in Gnome. Of course you can run KDE apps in Gnome and vice versa. 

> 
2. I find that the readability in Firefox/Konquerer is far less in KDE than GNOME. Everything seems so small in its default condition and jaggy. Does anyone else feel this? Is there any solution aside from going to configure each application?
I like the default Sans Serrif with size 9, but in web browsers, it doesn't use that Sad


If there is a way to render your fonts legibilly, please let me know. I use Opera or Konqueror, but at work I am forced to use Fx. Konq renders well though. You may consider increasing your font DPI in the control center, if you haven't done so already. 

> 
3. I have a network drive which is Windows based. I currently only have a link that goes to it. However, is it possible to "mount" it?
For example, at the moment to get to it, I do the following. smb://192.168.1.101
Is there anyway to make it like a real drive, like Windows and its network drive mapping?


External and removable drives are generally mounted in the /media folder. Try [this howto]("http://ubuntuforums.org/showthread.php?t=288534&highlight=cifs") . It helped me a lot.

---

### Post by Road_kill on 2007-08-19
Thank you for your help.
It was very useful :)

---

