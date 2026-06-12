---
title: "Beryl installing = Ubuntu fails yet again."
date: 2006-10-24
forum: General Help
---

### Post by jimhaddon on 2006-10-24
Hi, yet again, Ubuntu has failed, and I bet I will have to re-install the whole thing to get it working again, YET AGAIN. I have been told to ask more questions though, so here goes:

I tried to install Beryl on my machine and when i rebooted like the tutorial said, ubuntu will no longer start. X-server fails to load, saying x-org required version xxxxxx current: xxxxxx.

Any ideas? or is another clean install needed.

this is the tutorial in question:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

---

### Post by jimhaddon on 2006-10-24
Does anyone have an answer before I remove ubuntu forever?

---

### Post by beerorkid on 2006-10-24
well I am no expert, but i can give you a few pointers.

!. there are bunches of beryl/xgl threads already, heck the big ol sticky on the top of every general help page would be a great place to start.

2. you provided very little information on what happened besides saying X wont start.

3. blaming this on ubuntu is not really fair.  beryl is not ubuntu's doing and is in development and unstable.  It is a risk and it is made apparent in most tutorials.

not trying to be a jerk, I know it can be frustrating.  You can find your answers you need if you look in the right places.  post in the threads where people are eagerly waiting to help you.

I am not too sure but I think that wiki you followed might be a little out dated.  A great place to start is on the beryl forums themselves [the howto section](http://forum.beryl-project.org/forum-5-howto)

Also the good howto's on this forum.  Tell them your issue and provide your xorg.conf the community will help you.

---

### Post by jimhaddon on 2006-10-24
Since i cant start ubuntu, i cant get the xorg.conf and havent got the time to wait. So really, what you're saying is just do a clean install.

Everything in Ubuntu is always the same when installing software.

In windows, you double click the installer, then click next, next, i agree, next, finish. - no problems.

In Ubuntu its - tar-cnfsd -df -f \etc\whatever....
./configure
/gker0tgerg whatever
done.  - Reboot - ubuntu no longer works. Ask forum for answers. No-one knows, no choice but to go back to good old windows.

---

### Post by beerorkid on 2006-10-24
did you happen to make a backup of your xorg.conf?  that is always a good thing to do.

hang on a second and I will find the command to rewrite it for ya
 that should save you the trouble of reinstalling.

---

### Post by ~LoKe on 2006-10-24
Open up the virtual terminal and type...
```
cat /var/log/Xorg.0.log
```
And paste the last 10-15 lines.  

If you want to just try reconfiguring...
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jimhaddon on 2006-10-24
I did make a backup of my xorg.conf. I replaced the modified one with the backup (i think) by using the cp command, and still nothing.

Iv tried the reconfigure too, and again it makes no difference.

---

### Post by beerorkid on 2006-10-24
dpkg-reconfigure xserver-xorg

might have to sudo it

sudo dpkg-reconfigure xserver-xorg

---

### Post by jimhaddon on 2006-10-24
As i said, Iv tried the reconfigure

---

### Post by smartalecks on 2006-10-24
try this.

```

sudo /etc/init.d/gdm start
```

what happens?

The problem is also that the tutorial is not the one you should have been following. Its for Dapper with AIGLX, which you don't need, and is probably why your system is messed up. Edgy will include AIGLX, and using AIGLX with Dapper is iffy at best (better off using XGL, which Beryl does support). This is the tutorial you wanted:

[http://forum.beryl-project.org/topic-4861-howto-install-beryl-dapper-nvidia-using](http://forum.beryl-project.org/topic-4861-howto-install-beryl-dapper-nvidia-using)

---

### Post by ~LoKe on 2006-10-24
> **jimhaddon said:**
> As i said, Iv tried the reconfigure

Can we get those logs?

---

### Post by beerorkid on 2006-10-24
> **jimhaddon said:**
> I did make a backup of my xorg.conf. I replaced the modified one with the backup (i think) by using the cp command, and still nothing.

Iv tried the reconfigure too, and again it makes no difference.

ooh that prob not good.  i am not familiar with aglix and it looks as if it installs some new X server (called xserver-xorg-air):  not to sure about what that is.

possibly try and remove all the stuff you installed via apt.  I am not really sure if this would help, so do it at your own risk.  so:

```
sudo apt-get remove xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`
```

and possibly:

```
sudo apt-get remove beryl emerald-themes
```

I tried aglix on my laptop but it was a different howto than the one you posted, it had nothing about the xserver-xorg-air-core, but it did not work, really crappy vid card.

Good luck.

---

### Post by jimhaddon on 2006-10-24
Ive just tried the gdm start command. It just says failed in red.

in teh x server log this is what it says:

X mismatch - detected x.org 7.1.1.0, required 7.0.1-8.
Failed to load module fglrx (module require mismatch)
No drivers available.
Fatal: no screens found.


This equals format+fresh install right?

---

### Post by ~LoKe on 2006-10-24
Sounds like you're trying to use an old version of the fglrx in Edgy.

---

### Post by beerorkid on 2006-10-24
> **jimhaddon said:**
> Ive just tried the gdm start command. It just says failed in red.

in teh x server log this is what it says:

X mismatch - detected x.org 7.1.1.0, required 7.0.1-8.
Failed to load module fglrx (module require mismatch)
No drivers available.
Fatal: no screens found.


This equals format+fresh install right?

unfortunately a reinstall might be your best option.  it is pretty quick to reinstall.  Then you can follow the proper howto and get it working all nice and stuff.

Don't give up on ubuntu just yet.  When you get the beryl kicking you are gonna love it.

---

