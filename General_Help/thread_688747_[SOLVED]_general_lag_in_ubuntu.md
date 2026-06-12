---
title: "[SOLVED] general lag in ubuntu"
date: 2008-02-05
forum: General Help
---

### Post by alejo0823 on 2008-02-05
Hi everyone, I'm having a bit of problem with ubuntu and I would like some help.
I have a good pc and ubuntu its not responding very well to it, I have some general lag in the windows when I drag or scroll (especially firefox) I have compiz active, but apparently for some reason beyond me it actually makes the lag decrease. From this I get that its not a hardware issue but from software also to back this up vista and xp are running perfectly.
I have.
athlon 64 x2 6000 (I don't know if my cpu could be the problem, in xp Installed a program from amd to improve performance maybe ubuntu need it too) 
3 GB of ram
nvidia 8600gt (this card its giving some people trouble maybe drivers are the cause of my trouble?)
ubuntu 32 (I don't know if upgrading to 64 its going to solve this or make it worse)

I'm sorry I cant give more information about the problem but it seems as a very general problem to me. I mean its not triggered or application specific, is the whole system that lags. I know this one its hard to solve and I really don't expect a solution, but I would really like to hear some ideas. 
remember I'm a noob so please don't be too technical.
thanks

---

### Post by prince_niceguy on 2008-02-05
open a terminal and put the following command

```
$ top
```

now drag firefox, if it is xorg then probably it would be good to remove compiz and be without effects. Also, just to confirm are you using the ubuntu nvidia drivers or the nvidia drivers from net?

---

### Post by alejo0823 on 2008-02-06
Ok I did top, the process that seems to be hinger in cpu usage is trackerd, then it drops and ntfs.mount starts going up. I think this is the tracker doing its stuff and its not nice to my cpu, do you think this could be my problem. Also xorg and comiz.real stay very low alwas below 10%, while trackerd sometimes goes to 90% or even 99% is there a way to deactivate the tracker or fix it??
Im using the drivers ubuntu installs automatic when you click on restricted drivers
Thanks.

---

### Post by prince_niceguy on 2008-02-06
Well you can disable tracker if you are not using it. 

You can do so in the system --> preferences --> indexing option. 

Uncheck both enable indexing and enable watching. 

That should fix the tracker. If you want to use it then just ensure that in the performance tab of the indexing option you make it slower and minimize its memory usage. 

Still tracker tackes lot of time then just disable it.

I personally use beagle, and have tracker disabled.

---

