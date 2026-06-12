---
title: "Ubuntu repair, how to?"
date: 2008-04-16
forum: General Help
---

### Post by rafacanob on 2008-04-16
Hello, I need some help with my Ubuntu installation. 

My PC has a dual installation WXP-Ubuntu 7.10. Some days ago, It suddenly crashed (and hanged) but although I restarted It didn't recover. 

Al first, grub couldn't run sometimes, but other it loaded ok. However, when loaded, Windows couldn't complete loading and so did Ubuntu desktop. Trying Ubuntu recovery mode worked, but I'm not very expert with Linux and I don't know which commands (besides of fsck) could help me.

Unexplainablely, Windows recovered Itself (I don´t know what I did), also grub and now both work always, but Ubuntu safe mode died too.

My question is, what can I do to restore Ubuntu files? I have a System Rescue CD, I tried fsck but It has not found anything. Which other commands are avaiable?


Thanks in advance.
Rafa

---

### Post by phidia on 2008-04-16
Trying to boot a damaged filesystem can cause further problems and you should never run fsck on a mounted parition either.
Maybe a livecd, the ubuntu desktop cd is one, could help? At very least you can run the livecd and see if your home directory is there (and back up files if you need to). 

You can also see if the boot directory is intact-although I realize you need to know what a working boot directory looks like.
When you say "safe mode died" that doesn't provide much information. What error does grub give when you select ubuntu? 

If there are no errors be very specific, please, about what occurs after you select ubuntu in grub.

---

### Post by rafacanob on 2008-04-17
No, grub works fine. It loads every option without problem, but while Windows runs ok, Ubuntu loading stops after some seconds (progress bar stops at 1/3 or 1/4), and in recovery mode can't reach prompt, either. I think there's a SO corruption more than a filesystem corruption, but I cant assure it.

I run fsck from a livecd, but doesn't find anything (suggest any -x option?). Fortunately, I've been able to backup everything (and no file read errors). Now I'm interested in knowing which tools can I run to check the SO.

Another symptom: The small text "loading..." that appears before starting loading Ubuntu normally fades quickly, but now takes some seconds.

Any Ideas?
Thanks.

---

