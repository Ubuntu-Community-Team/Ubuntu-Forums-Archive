---
title: "Ubuntu Installation freezes"
date: 2007-12-06
forum: General Help
---

### Post by nm329242 on 2007-12-06
Hi,

I have been using Ubuntu from a couple of months. Somthing went wrong and I was getting GRUB error 17, was not able to fix it so I  decided to format my hard disk. Using Knoppix I deleted the partitions and created new ones:

sda1          Boot       Primary              Linux                50MB
sda2                        Primary              Linux swap       600MB
sda3                        Primary              Linux                 60000MB

I tried to install Ubuntu again from the Live CD but it wont start it gave me error saying:
There was an error starting the GNOME setting daemon.
 
Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.                  

Nothing happens after this.

I thought something might have gone wrong with my CD so I downloaded Live CD and burned another CD.

Now, when I try to boot from this CD it hangs after:
Running local boot scripts (/etc/rc.local)

So I booted the CD in "safe graphics mode". 
Well the CD started anf after an hour of wait the installation window came up but hangs after step 1.

I have tried everything not sure what to do now.

Please help me.

---

### Post by soaringphx on 2007-12-12
try this thread [http://ubuntuforums.org/showthread.php?t=413975](http://ubuntuforums.org/showthread.php?t=413975)

---

### Post by Lostincyberspace on 2007-12-12
Boot needs too be 100MB for Ubuntu. That will fix your problem quick.

Maybe not It's not what I thought it was.

---

