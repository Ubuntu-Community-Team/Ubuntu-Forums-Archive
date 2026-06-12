---
title: "Windows XP clone software"
date: 2007-03-21
forum: General Help
---

### Post by DapperMe17 on 2007-03-21
Hi,

I'd like to clone a HD that only has Windows installed. I plan to then send that image to an external HD for future install on a dual boot HD(Windows/Linux).

I see Partimage & ClonezillaLive out there, but can't tell if either will work on a Windows-only system?


Thanks for any input!

---

### Post by hikaricore on 2007-03-21
If I'm not mistaken, you can actually use **gparted** to copy and paste partitions.

I believe it will work for external drives as well, but I've only used it on internal.

If you can't launch it /w:

```
gparted
```

From a terminal, try running:

```
sudo apt-get install gparted
```

---

### Post by DapperMe17 on 2007-03-21
It's Windows-only machine right now...I don't have Ubuntu installed, yet.

---

### Post by hikaricore on 2007-03-21
You can run gparted from the livecd as well.  :)  Without installing anything.

Just open a terminal when it starts up and type:  **gparted**

Can't hurt to check it out, if I'm wrong you only wasted 5 minutes.  If I'm right you saved yourself some searching and possibly money.

---

### Post by DapperMe17 on 2007-03-21
Maybe I'm being unclear with my question.


Windows is the only OS I have on the computer hard drive, which is maxed out & has no more free space. 


I want to clone this hard drive to an external drive, so that I can install a new hard drive in the PC, then reinstall Windows as well as Ubuntu.


But, currently, the PC only has Windows, not Ubuntu. 


If I run Gparted from a live CD, are you saying that even though it's a Windows machine, that I should be able to copy the Windows image from the PC hard drive directly through the PC USB port & to the external hard drive?


Thanks for your patience!

---

### Post by chewearn on 2007-03-21
Yes, GParted LiveCD can run on machine with only Windows installed, because it is booted directly from CD without need for anything linux related on the harddisk.

However, to get right to your need, I recommend DriveImage XML
[http://www.runtime.org/dixml.htm](http://www.runtime.org/dixml.htm)

---

### Post by hikaricore on 2007-03-21
> **DapperMe17 said:**
> If I run Gparted from a live CD, are you saying that even though it's a Windows machine, that I should be able to copy the Windows image from the PC hard drive directly through the PC USB port & to the external hard drive?

As long as ubuntu recognizes your usb drive then yes, you'd be able to copy it with gparted (as far as I know, I can't personally test this at the moment but it does have a copy function).

But Astalavista's link may be of more assistance than gparted if it's more use friendly, I don't have time tonight to check.

Anyway, good luck,

--Aaron

---

### Post by DapperMe17 on 2007-03-21
Thanks for your time & great advice!


I am aware of the software you linked & I will look into Gparted as well.


Great information guys, 
Thanks

---

