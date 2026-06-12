---
title: "su login in terminal fails but causes Firefox to open!"
date: 2007-06-16
forum: General Help
---

### Post by imvik on 2007-06-16
I've suddenly got this weird problem with Feisty:
If I try to login as su or with a sudo command in a terminal, the login fails with "wrong password" but Firefox starts or opens a new window if already open!
This means that I just can't run any su commands in a terminal.

Any solutions?

Thanks.

---

### Post by AndyCooll on 2007-06-16
Is this a fresh install?

---

### Post by imvik on 2007-06-16
Yes, it's a fresh install. I had no problems like this until I installed Opera. Then when I wanted to sudo to move a file, the problem started. I uninstalled Opera but that didn't solve the problem.

Now I also notice that there other things that are behaving weird. I have French keyboard and to get zero I must press Shift+0. If Firefox happens to be open, this opens a new tab!

I tried to reinstall some components of Gnome (whatever seemed logical since I'm new to Linux) but it didn't help.

What is the best way of fixing all these? Will I have to reinstall Ubuntu? Can't the installation be repaired?

---

### Post by AndyCooll on 2007-06-18
My guess is you are going to need to reset your keyboard to the correct one System > Preferences > Keyboard  (IIRC, I'm at work at the moment and not in front of a Linux box).

This is likely to explain why you're typing the "wrong" password.

Not sure about the FF issue.

:cool:

---

### Post by imvik on 2007-06-20
I tried resetting the keyboard settings too but that didn't work.
The most annoying thing now is that I have to use the notebook's awkward number pad to type zero since I can't use the usual key.

If I can't find a solution, I'll have to reinstall Ubuntu. And unlike Windows, there's no option of repairing the installation.

Installing Ubuntu must be made a lot more simpler if more people are to use it. And considering most windows users who like linux usually have dual boot systems, that too must be made simpler.

Thanks

---

### Post by Flying George on 2007-06-20
I've had the su "Wrong password" error before and this is how I fixed it:

Go to system > administration > users and groups > select 'root' and set a unique password for root. Eg. different from your user.

But it never opened firefox for me o.O

---

### Post by imvik on 2007-06-21
Initially, Feisty was working fine. Then I installed some packages like Opera and some others. The problem started ever since. I tried removing Opera but that didn't help.

Is this problem unique to me? I don't think it has anything to do with the root password since I can login normally in the graphical login.

Is there no way to repair the Ubuntu installation?

I'm a newbie to Linux and I, like many others, find most of the text commands bewildering. It might as well be some sort of cryptic code! So I prefer, at least until I'm more conversant with the terminal commands, to work with Ubuntu graphically.

---

### Post by AndyCooll on 2007-06-21
Back to the keyboard settings, under layouts is your keyboard correct? Mine is "Generic 105-key (Intl) PC"

As for the dual-booting option, there's an excellent HOWTO link in my signature. And I must say that if it weren't for Linux the dual-booting situation would be even worse. Microsoft certainly don't make it easy to dual-boot two OS's!

:cool:

---

### Post by imvik on 2007-06-24
Yes, my keyboard is set to pc generic 105 keys. I did try the acer keyboards (I have an Acer Aspire 5632) but there was no difference.

I agree with you that it's thanks to linux that dual boot even works this well. But size wins here: linux will have to bend to suit Windows since the other way won't happen. I suppose it would be lot easier if Windows didn't treat the boot partition as its own fiefdom.

I actually did have a look at the links in your signature and found them interesting. But I'm a newbie to Linux and definitely not an expert at hardware or software and the task of reinstalling Linux is a bit daunting. And none of them have specific information on trouble-shooting problematic installs. Maybe it's because I found there are so many different ways to get into trouble!
I suppose I just got lucky with some educated guesses the first time when I installed Linux by myself!

---

