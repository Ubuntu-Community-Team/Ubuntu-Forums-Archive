---
title: "Acer E1-572 - No sound or ethernet"
date: 2014-06-16
forum: General Help
---

### Post by marc13 on 2014-06-16
Just purchased a new laptop, and after getting through the nightmare of installing Ubuntu while Windows 8 tried blocking me, I am finnally here. 

I however realized that certain things are not working. I cannot get ethernet cable to work and neither can I get the sound to work. There is just no sound, despite the fact that it shows the sound icon in the top of the Ubuntu screen. 

The best post so far has been this one: [http://ubuntuforums.org/showthread.php?t=2192280](http://ubuntuforums.org/showthread.php?t=2192280) 

I managed to get my touchpad to work, but the ethernet tutorial the guy is posting does not work. And there is also no guide for sound. 

I updated the kernel as well according to that post, but it did not do anything specific to help me with ethernet or sound. Obviously this computer is pointless without sound and ethernet, and since I just paid 400£ for it, I was hoping for some solutions. Hope someone can help me.

**EDIT:** Sound is now working, it was a matter of switching some things around under sound setting. However still no luck with ethernet.

**EDIT2: **More information about my system:

Looking into where tg3 is already loaded (adding ".ko" does nothing)
[PHP]
lsmod | grep tg3
tg3                   182824  0 
ptp                    18627  1 tg3

[/PHP]

My current kernel version
[PHP]
uname -a
Linux work-Aspire-E1-572 3.10.17-031017-generic #201310181435 SMP Fri Oct 18 18:36:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
[/PHP]

Still, cannot get ethernet to work. Hope someone has a solution to loading the tg3 file into the kernel.

**EDIT3**: Finally solved it by doing modprobe tg3 and then make install.

---

