---
title: "Segmentation Fault"
date: 2007-07-17
forum: General Help
---

### Post by PrimoTurbo on 2007-07-17
I tried 3 times already using Wubi-7.04.04, I defragmented and used scan disk before my installs. I tried ubuntu and ubuntu studio with no success. Everything goes fine, install is complete asks me to reboot and I do. I then get a selection for Windows or Ubuntu. I select Ubuntu, it tries loading stuff I see the terminal text and then it stops and I see.

[22.985741] Segmentation fault

sometimes the numbers are different, anyways I CANNOT find the solution anywhere. I found a bunch of other threads on here and on Google with people having the same problem. There is something flawed with wubi..

My specs are the following
Windows XP Pro
250GB WD
P4 1.6Ghz
768 DDR RAM
ATI 9700 Pro 128MB

Please help me out, my DVD drive is busted can't get Ubuntu installed :(

---

### Post by ago on 2007-07-17
Sometimes the hardware is not compatible. Try to boot the LiveCD, if that does not work, you are out of luck

---

### Post by PrimoTurbo on 2007-07-17
I have installed ubuntu about 50 times before and it works fine with my hardware, it's wubi that's not working. My DVD drive seems to be broken, I'm having problems ejecting stuff latley and any time I try to install Linux it hangs at some point.

Any more ideas?

---

### Post by ago on 2007-07-17
I'd need some more info to understand at what point exactly you have the crash. From how you put it, it looks like a kernel crash, that should not have much to do with wubi, since wubi code is not executed at that point.  Did you try Ubuntu with the kernel 6.20.15-generic?

---

### Post by PrimoTurbo on 2007-07-17
It's using which ever is the default kernel that comes with 7.04 as I have made no changes to anything. The reason why I don't think it's ubuntu because I have installed Ubuntu 7.04 off the sent cd and off the alternative cd which I burned before with no problems, same for Ubuntu Studio, Kubuntu & Xubuntu. My DVD drive is currently busted so I can't install it off the cd.

I appreciate your help btw :)

---

### Post by ago on 2007-07-17
Do you get a prompt or it just freezes?

---

### Post by PrimoTurbo on 2007-07-17
It doesn't freeze in fact I can even type but there is no response on the commands. I'm stuck in the terminal loading text screen, I can even switch workspaces with alt+f2 but can't type in the second one.

---

### Post by ago on 2007-07-17
is during installation, or after installation? do you see the blue screens or not? 
what do you get if you type something like "ls" after alt+f2? absolutely nothing?

---

### Post by PrimoTurbo on 2007-07-17
This is after the wubi installation, I reboot I get a selection Windows or Ubuntu. I select Ubuntu, it starts loading, there is no blue screen or anything. There is a black screen with text, then I see the error after a few minutes.

---

### Post by PrimoTurbo on 2007-08-30
So absolutely no fix for this? There is clearly a problem with Wubi causing this, many threads about it...

---

### Post by ago on 2007-08-30
> **PrimoTurbo said:**
> So absolutely no fix for this? There is clearly a problem with Wubi causing this, many threads about it...

Quite possible, but it's low priority at the moment, 

1) because I cannot reproduce that on my machine, which makes it very hard for me to debug
2) because we are working on the next version that uses a new kernel and that by itself might address the issue, hence there is little point to focus on kernel related issues of the old version

---

### Post by PrimoTurbo on 2007-08-31
When is the expected release date for the new kernel version?

---

### Post by floyd8 on 2007-09-19
I am having the exact same problem using the Wubi installer. Reboot, get the option for Ubuntu and then about 15 seconds later I get a seg fault. 

The line (or number) before the seg fault was: 32.360943 if that helps any.

---

### Post by ago on 2007-09-20
> **PrimoTurbo said:**
> When is the expected release date for the new kernel version?

It's already out and being tested by developers but at the moment it's a bumpy ride
If you want to have a go anyway: 

[http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/)

---

### Post by RomanIvanov on 2009-02-14
Run Coccinella from the sources ("tclsh8.5 ./Coccinella.tcl") or use [http://www.getdeb.net/app/Coccinella](http://www.getdeb.net/app/Coccinella)

---

