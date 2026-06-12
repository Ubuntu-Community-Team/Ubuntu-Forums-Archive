---
title: "The Problem with this Picture"
date: 2006-08-25
forum: General Help
---

### Post by jimmygoon on 2006-08-25
This is now the 3rd time I've reloaded because when I upgrade my kernel my wireless stops working. This is getting very annoying and I would not like to have to reload this time.

Dapper, linux-686 with linux-386 still installed.

---

### Post by peabody on 2006-08-25
?????  Make and model of your wireless adapter ?????

I feel your pain, but you gotta give us something ;) .

It's probably due to the kernel update.  Do you use ndiswrapper to get your wireless working?

---

### Post by jimmygoon on 2006-08-26
No. It works out of box. So I loaded up Synaptic... searched for "686" and then installed everything I could that had the words "linux, 686, modules" and some with the words "restricted" in it.... and then rebooted and it worked.

Whatever the process... it needs to be automated. I have an Atheros card... integrated.... This is a serious problem... I would contend moreso than Xserver problems because I can't DL new packages without internet...

---

### Post by yatt on 2006-08-26
> **jimmygoon said:**
> No. It works out of box. So I loaded up Synaptic... searched for "686" and then installed everything I could that had the words "linux, 686, modules" and some with the words "restricted" in it.... and then rebooted and it worked.

Whatever the process... it needs to be automated. I have an Atheros card... integrated.... This is a serious problem... I would contend moreso than Xserver problems because I can't DL new packages without internet...

Install the package Linux-686 and it will be automated.

---

### Post by peabody on 2006-08-26
If it works out of the box with the old kernel I'd use that kernel for now.  If you've installed a new kernel, you can get to the kernel boot menu in grub by hitting escape just as the computer is about to boot.

As for trouble shooting the problem, when you are booted in the new kernel, what is the output of the lsmod command?  Post it here.

Edit: okay I'm confused...are you still having problems, or did you fix the problem?

---

### Post by jimmygoon on 2006-08-26
> **yatt said:**
> Install the package Linux-686 and it will be automated.

no. I already had linux-686 installed and when it got upgraded, the proper packages weren't also upgraded/installed.

[b]Its fixed now, but this happens every time I upgrade my kernel and its annoying as all get out... I'm using a few unofficial repos but just compiz-quinn stuff... nothing that would affect my kernel... oh well.... At least I kinda know what I'm doing with these packages

---

### Post by peabody on 2006-08-27
> **jimmygoon said:**
> no. I already had linux-686 installed and when it got upgraded, the proper packages weren't also upgraded/installed.

[b]Its fixed now, but this happens every time I upgrade my kernel and its annoying as all get out... I'm using a few unofficial repos but just compiz-quinn stuff... nothing that would affect my kernel... oh well.... At least I kinda know what I'm doing with these packages

Kernel upgrades make issues for everyone, that's why they get announced around here.  kernel modules for video cards need to be recompiled, etc.  If you end up getting the kernel upgrade, make sure you get the lates version of the linux-restricted-modules.

---

### Post by MarinaraOfDeath on 2006-08-27
> **yatt said:**
> Install the package Linux-686 and it will be automated.

This needs to be qualified. When the torrent up ungrades started, I had to manually install the restricted modules for kernel upgrade but the last. During the last kernel upgrade the restricted modules got installed because I had learned that the meta package was required for them to be automatically upgraded, verified that it was installed, then * reinstalled the package*. Whatever the problem had been, that fixed it, but it irks me to keep hearing this when a number of threads on this forum have asked about why it didn't do its job. 

Also, I guess one benefit of only having Matlab in XP is that I haven't been booted into Ubuntu for the last two weeks except twice. Hopefully things will be fixed by the time I'm done generating statistics and can go back to my beloved multiple desktops.

(I started with Kubuntu Dapper and quickly installed ubuntu-dekstop, so I can't tell if the problem arose from some arcane optimization.)

---

