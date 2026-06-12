---
title: "need help beryl ati aixgl"
date: 2007-03-31
forum: General Help
---

### Post by AlexenderReez on 2007-03-31
nasrol@fujitsu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)



this is what i got while try to run beryl on my ati redeon xpress 1150 card (laptop)...


hope anybody can help....:( :( :(

---

### Post by spankymasterc on 2007-04-01
Seems like you did not install your Drivers for your video card..? 

Did u get them from ati.?

did you edit the /etc/X11/xorg.conf / as instructed in the documentation ?

if u need personal help i will gladly assist u cant add me to msn [email]spankymasterc@hotmail.com[/email].....

Also take a look at this :

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

maybe u setup beryl incorrectly

and here is the site so u can setup your Ati graphics card :
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by AlexenderReez on 2007-04-01
i will try....and inform you later.....

---

### Post by daynah on 2007-04-01
I spent four hours trying to get my ATI working. Then I bought an nvidia card. Try and reinstall aixgl. If it doesn't work that one next time, just trust me and give it up. Learn from my mistakes. Go kiss your girlfriend, eat pizza with your friend.

Basically, the few ATI cards that'll do it right, it's easy enough for smart people like you and I to do it right the second time (gotta include one time to go, omg I brain farted that time). If you don't do it the second time, don't waste your life going to try 14 before you realize it's hopeless. The drivers just don't work fully on many cards, and if the driver isn't going to work, beryl can't work on your driver.

Good luck.

---

### Post by AlexenderReez on 2007-04-02
succeed!!!
thax for concern:KS

---

### Post by confuded92 on 2007-05-13
Heh, I am sorry for resurrecting this post, but I have the same problem. I have the same output and card as in 1st post. I have an Acer Ferrari 1000 with a ATI radeon express with Ubuntu 7.04 installed. I tried the edgy ati installation, but something didn't work (one of the commands). 

Why struggling with unsupported ATI card? I don't have money to buy another laptop, I can't get a new graphics card since it is integrated into the motherboard and mainly I want BERYL!!!! :(  Beryl is THE most awesome graphics on any OS I ever saw!!! 

I installed beryl, beryl-core (and everything that goes with it), beryl0manager. After installing beryl my title menus disappear, but I installed beryl-manager and everything is OK. BESIDES that beryl effects are not working at all!

I beg you pleas help! If the only solution is to learn C++ and code my own driver I will try my best! :)  Just get beryl working! Pleeeeeease!

---

### Post by IanW on 2007-05-13
As I understand it, the proprietory ATI driver (fglrx) does NOT support AIXGL. You need to use XGL instead.
This is purely the fault of ATI's Linux driver coding team, who need to get off the couch and DO SOME WORK!

---

### Post by confuded92 on 2007-05-13
XGL? Hmm...  Synaptic has no xgl... Ah, manual install! Hate it.. Ok Iwill try to mes around with xgl :P.

P.S. I am sort of a newb...

---

