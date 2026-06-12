---
title: "Ubuntu is freezing again"
date: 2007-06-01
forum: General Help
---

### Post by sheine on 2007-06-01
Several months ago, when Ubuntu was still beta, I asked for help because Ubuntu froze on me after an hour or so of use. I solved the problem by making pclinuxos my primary OS.

When the final version of Ubuntu became available, I again made it my primary OS. Now after a couple of weks without trouble, the freezing problem is back.

During the previous thread others acknowledged the same problem. Several said that they had solved the problem by removing the package beagle. I have just looked and the beagle package is not installed and therefore is not the cause.

There is no other conclusion than that there is a serious bug in Ubuntu. If somebody knows how to correct it, please tell me. Otherise it is back to pclinuxos.

---

### Post by eyelessfade on 2007-06-01
you need to post your hardware spec here or our guess is as good as yours :)
also the content of lspci and dmesg can help :)

---

### Post by sheine on 2007-06-01
Many of us have gone through the standard diagnostics. Below is a quick sample of posts with the issue. There are many more. This did not happen with edgy. It is time to locate the basic problem and fix it. On the same computer this does not happen with pclinuxos or simply mepis. It is an ubuntu problem.


DrSkeezix  
First Cup of Ubuntu

 
Join Date: May 2007
Beans: 4
 Ubuntu 7.04 randomly freezes 

I can run Ubuntu 6.06 non-stop, but as soon as I install 7.04, I get random freezes. Sometimes the mouse works, sometimes not, but nothing else. no HDD running or anything.

can happen after 2 hours or 2 seconds.

And I would like to use 7.04.
__________________


Digitallysick  
Way Too Much Ubuntu

 
Join Date: Apr 2005
Location: The worst place
Beans: 265
 feisty fawn freeze ! driving me insane 

feisty fawn keeps freezing on me, at first i thought it was FF causeing the issue. But now i have tried opera and it still happens, at random. Mostly when it freezes i can still move the mouse, but thats it. Today it froze with the screen saver (gnome feet). How can i tell what is causing this? would it be in the system logs? i can't take it much longer
__________________


professor_chaos  
Quad Shot of Ubuntu

 
Join Date: Apr 2005
Location: 127.0.0.1
Beans: 430
Ubuntu 6.06 User
Re: feisty fawn freeze ! driving me insane 

This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/ubuntu/+s....20/+bug/64587](https://bugs.launchpad.net/ubuntu/+s....20/+bug/64587) 
---------------------------- 


Im having similar problems on a new Darter Ultra that I upgraded to feisty from edgy.
My system is freezing every few minutes sometimes.

[http://system76.com/forums/viewtopic.php?t=1375](http://system76.com/forums/viewtopic.php?t=1375)

Elcoco  
5 Cups of Ubuntu

 
Join Date: Mar 2005
Beans: 17
Re: feisty fawn freeze ! driving me insane 

Im having the same problem, so far it happens when i use the desktop effects or beryl my video card is good enough to handle beryl since i used it all the time in edgy. After i made a fresh feisty install i started having problems with the effects. i tried the changes to the .conf that where sugested but the xserver didnt even want to start up with them. ill include my .conf file incase any of you want to take a look
  #19      
 April 22nd, 2007 
Vashu  
5 Cups of Ubuntu

 
Join Date: Aug 2006
Bean Count Hidden 
Re: feisty fawn freeze ! driving me insane 

Same problem here. Its really a issue.
It seems to be triggered by something with the mouse but i could be wrong. I also upgraded from edgy to feisty and keep getting these freezes constantly. I even accessed my machine (hp nw9440 laptop) from another pc in the network via ssh and it worked fine in console mode, ran a top and everything seemed fine.

astronutties  
First Cup of Ubuntu

 
Join Date: Apr 2007
Beans: 3
Ubuntu 7.04 Feisty Fawn User
Re: feisty fawn freeze ! driving me insane 

I've been having the same problems. I just did a fresh install of Feisty last night. Unfortunately, I am new to all of this and don't really understand how to do a lot of the suggestions made to fix my problem.

What I have noticed is that it seems to happen when I run a lot of programs all at once. It seems to only happen when my memory becomes full with cache. I have only noticed this because I have a system monitor showing my memory usage.

---

