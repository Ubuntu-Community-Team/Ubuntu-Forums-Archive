---
title: "Ubuntu will install, but it wont work."
date: 2019-05-06
forum: General Help
---

### Post by strawberryunicorn on 2019-05-06
Hi There.
So basically, I tried to revive this old PC by installing Kubuntu 18.04 in it. But the problem is, the thing wont just work.
Here's how I describe the problem with my inept english:
Whenever  I install Kubuntu, I noticed that there's this 'No irq handler for  vector' thingy popping up in the screen. It just shows up. That's the  only thing written on the screen. It seems no problem at all since after  its gone, I am presented with the installer. Then this weird thing  happens. I press 'try kubuntu', but when I do that, I guess it wont let  me try kubuntu at all. The splash screen with the circle loading screen  appears. Then next, the circle loading thing stops dead, everything  freezes. After a while, everything is black (Sometimes there will be  lines and patterns in each attempt to 'try' kubuntu, but most of the  time the screen is black). At this point, everything is dead. Cant use  my keyboard and do other things whatsoever. So I restarted, and I was  presented with the same problem.
I  proceeded to install Kubuntu. Everything goes smooth. The process of  installation was good. But after installing, after the restart, the  problem with the 'try kubuntu' stage appeared again, but this time I  wasn't 'trying kubuntu', it was the real deal. Sometimes I managed to  see the lockscreen, but then again, it will freeze and everything will  turn black.  Weird though the lockscreen background was all black.
**OTHER INFORMATION:**

[LIST]
[*]Tried switching hard drives, no hope. 
[*]Tried switching flash drives, still no hope. 
[*]Tried a different version like 19.04, no hope. 
[*]Tried another flavor like Ubuntu 16.04, still no hope. 
[*]This  PC had previously installed other flavors of Ubuntu, like Xubuntu and  Ubuntu itself. It also had windows 7-10 before the problem. 
[*]The  PC had Xubuntu in it before I considered going to Kubuntu. So far the  OS runs fine, the only problem is installing another OS. 
[*]Windows  will install fine. Only Ubuntu and its flavors wont install. Heck I am  actually writing this post with a newly installed Windows 7 in it. 
[*]I think the problem is the PC itself. 
[*][Here]("https://www.youtube.com/watch?v=wWHD-9Je5ZI&feature=youtu.be")  is the video. I really.. REALLY apologize because I filmed vertically.  Tried to filmed horizontally while recording, but I FU. Desktop users  might have to tilt their heads to 90 degrees lol. I am really sorry I  have no idea about video thingies. 
[/LIST]


What are your thoughts? What can I do to solve this problem? Thanks!  
  
EDIT: Forgot the speics

Specs:

[LIST]
[*]Emaxx MCP61M-iCafe Motherboard 
[*]AMD Athlon X2 240 
[*]4gb RAM 
[*]Samsung HD161HJ 160gb Hard Drive 
[*]No graphics card (It had a GT 630 before) 
[/LIST]
Its an old man. Almost 10 years and still kicking lol.

---

### Post by cruzer001 on 2019-05-06
Hello

This 4 year old post suggest your on board video (nVIDIA Geforce 6150SE) is not well supported by the ubuntu installer.
[https://askubuntu.com/questions/588538/whats-the-correct-driver-to-use-with-a-geforce-6150se-nforce-430-on-ubuntu-and](https://askubuntu.com/questions/588538/whats-the-correct-driver-to-use-with-a-geforce-6150se-nforce-430-on-ubuntu-and)

I would try nomodeset
[https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)

If this bug applies to you then may be better to get another video card.  I would think you could pick them up cheap.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1746638](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1746638)

---

