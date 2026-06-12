---
title: "Gurb error 22"
date: 2007-11-02
forum: General Help
---

### Post by Iamshiznaki on 2007-11-02
*Grub   I spelled it wrong

I'm a total linux noob, and I figured a great starting place would be ubuntu. Following the release of 7.10 I used a live CD to install. I've had nothing but trouble since.

I had problems with a disk partition earlier, and opted to partition my 60gb hard drive with 15g set apart for the file system. Then I had trouble accessing the drive, it said only root could access it, and I just gave up. So then I went for a full reinstall, using the entire 60gb. I told install to write over all the partitions, just use the entire drive. 

Now I get the grub 22 error upon power up. Following this I can't do anything, nothing works, I can't type, nothing. 

What the hell is going on?

---

### Post by Pumalite on 2007-11-02
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
You might have a laptop and Grub installed itself in first partition that it's usually a 'recovery' partition.
Boot from Live CD and from Terminal, post the output of:
sudo fdisk -lu

---

