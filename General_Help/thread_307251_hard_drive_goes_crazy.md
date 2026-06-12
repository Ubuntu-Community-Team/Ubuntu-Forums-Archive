---
title: "hard drive goes crazy"
date: 2006-11-26
forum: General Help
---

### Post by ronniet on 2006-11-26
Hi all!   :KS 

Been having this problem for a while now and just can't solve it...   :mad: 

At random times **_K_ubuntu** (Dapper) will become a bit slow, i can feel this by some lag in the mouse pointer movement. This has become a tell tale sign of impending doom in that my hard drive will then go crazy and the entire computer will slow to a crawl (ie: move the mouse and wait about 30secs for the pointer to respond and jump across the screen) and eventually I need to press the reset button on my case since I can't intervene. Even leaving it for hours, the hard drive whirrs like mad. It's almost as though its accessing a humungous file or something. I've no idea what is causing this to happen.   :confused: 

Any help would be greatly appreciated!  :cool:

---

### Post by zgornel on 2006-11-26
Check /var/log/messges for suspicious errors/warnings. Do you have swap enabled ? (check it: free -m).

---

### Post by taurus on 2006-11-26
What's the spec of your machine, especially the amount of RAM?

---

### Post by ronniet on 2006-11-26
> **zgornel said:**
> Check /var/log/messges for suspicious errors/warnings. Do you have swap enabled ? (check it: free -m).

I get:

             total       used       free     shared    buffers     cached
Mem:           503        500          3          0          2        155
-/+ buffers/cache:        341        162
Swap:            0          0          0

As far as I remember the machine has 512mb of RAM with a CPU of 2.2ghz...

---

### Post by zgornel on 2006-11-26
There it is. You have no swap - huge performance hit. Do you have a swap partition or a swap file ? If you do try *swapon -a* If it does not work, create a swap partition using gparted or a swapfile.

---

### Post by taurus on 2006-11-26
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by ronniet on 2006-11-26
> **zgornel said:**
> There it is. You have no swap - huge performance hit. Do you have a swap partition or a swap file ? If you do try *swapon -a* If it does not work, create a swap partition using gparted or a swapfile.

I kinda thought that but wasn't sure if a swap file was just a Windows thing :???: 

I did the *swapon -a* then did the *free -m* again but for swap it still said 0

I have plenty of space on my ***hdb1***, how would I make a swap file for swapon to use? And how do i tell swapon where the swap file is? :confused: 

Sorry for all the questions, i only converted from the Dark Side a few months ago after ye**eeeea**rs of being, quite literally, in the dark... ](*,)

---

### Post by taurus on 2006-11-26
Well, you need to boot your machine with the LiveCD.  Then, use gparted on the LiveCD to resize your harddrive, leaving about 1GB at the end for swap.  You can either use gparted to convert that new 1GB partition to swap or you can do it from a command line and mount it permanently after you boot back into Ubuntu.

---

### Post by ronniet on 2006-11-26
> **taurus said:**
> Well, you need to boot your machine with the LiveCD.  Then, use gparted on the LiveCD to resize your harddrive, leaving about 1GB at the end for swap.  You can either use gparted to convert that new 1GB partition to swap or you can do it from a command line and mount it permanently after you boot back into Ubuntu.

Thanks matey! I'll give that a go tomorrow.

I assume (hope? PRAY?! :) ) that gparted won't destroy my data on hdb1?
Assuming I can have my swap on a different drive from Linux its self?

Your a :KS  :D 

**Thanks for the advice!**

---

### Post by taurus on 2006-11-26
Go Celtic or Rangers, whichever team you fancy, mate...

---

### Post by ronniet on 2006-11-26
> **taurus said:**
> Go Celtic or Rangers, whichever team you fancy, mate...

**Partick Thistle** actually...  ;) 

Nah, i'm not much of a football fan.
(football=soccer) :D

---

### Post by taurus on 2006-11-26
Not much of a football fan from Glasgow!!!  That's a first...  :shock:

---

### Post by ronniet on 2006-11-26
yeah, i'm whats known as 'a weirdo'  :D

... oh, will gparted destroy my data when I create the swap drive?...

---

### Post by taurus on 2006-11-26
Not if you do it right.  Therefore, I recommend you backup those important files first just in case but here are some screenshots that might help you...

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by ronniet on 2006-11-26
> **taurus said:**
> Not if you do it right.  Therefore, I recommend you backup those important files first just in case but here are some screenshots that might help you...

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

In other words; **back up!**   :D
With my luck it'll go _well_ pear-shaped. :rolleyes: 

Smashin'. T**hanks for all your help.**

No offence, but I hope you don't hear from me again.   :mrgreen:

---

### Post by taurus on 2006-11-26
Always backup and good luck...

p.s.  Know a mate in Montrose...  ;)

---

