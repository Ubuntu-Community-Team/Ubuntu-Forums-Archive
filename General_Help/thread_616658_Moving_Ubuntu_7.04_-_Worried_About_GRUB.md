---
title: "Moving Ubuntu 7.04 - Worried About GRUB"
date: 2007-11-18
forum: General Help
---

### Post by aetherh4cker on 2007-11-18
Here is my situation:
My current XP machine has a 160GB hard drive, with 15GB of that partitioned for Ubuntu 7.04 linux.  What I did was installed Windows XP using all but that 15GB, then instructed Ubuntu during install to just use the remaining unallocated space.

I am *extremely* hard up for hard drive space, and just recently acquired an old 20GB hard drive from a friend.  What I wanted to do was copy my Ubuntu partition over to the second drive, and use the old space for Windows XP.

I plan to achieve such a feat with Hiren's Boot CD (I believe the program is Norton Ghost, but I'm not sure).

Here is where my questions and concerns come in.

1.  Windows XP just uses a boot.ini file in the root of the C drive, but where does GRUB put it’s file?

2.  How do I modify GRUB to point to the new location of Ubuntu?  This is what worries me the most.  I don’t want to lose my linux installation, and have to reinstall it all.

3.  To further squeeze all the space I can, I was also planning on putting the Windows XP paging file on it’s own partition on the second drive.  I assume I can just use GParted to make a small 1-2GB NTFS partition, and put Ubuntu on the rest of the drive.

I could really use all the help I can get to make sure this goes well.

Also, in an attempt to kill two birds with one post.  I have another question.

In GRUB it shows several installations of Ubuntu.  One is an older version that was there when I first installed, the recovery for the older version, and then one that is a newer version, and the recovery for the newer version.

Why does it keep the old version around?   The new one has been working fine for me, and I’d rather delete the old one all together.  I also don’t mean just deleting it out of GRUB, but wherever it points to in order to load that older version.  Seems like it is taking up unnecessary space to me.

Thanks in advance for any help.  I look forward to your replies.

---

### Post by Pumalite on 2007-11-18
You can move Ubuntu to new hard drive and then reinstall Grub. No problem at all:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by LaRoza on 2007-11-18
You might want to do a reinstall after making all the partitions they way you want them.

For the grub file, it is in /boot/grub/menu.lst.

Adding the page file to another partitions would make sense, and is easily done.

If you are pressed for space, you could do a minimal install of Ubuntu and then only add packages you want.

Furthermore, dual-booting when you are pressed for space doesn't make much sense. If you can use one OS for all your needs, I recommend doing it.

---

### Post by aetherh4cker on 2007-11-18
Alright, thanks for the help so far.

I'm actually dual booting for the learning experience.  The space is worth the education.

From the sounds of it, I'll move my Ubuntu over to the other drive, and then simply reinstall GRUB.  Sounds easy enough.

My only question is:  Is Norton Ghost the best way to move it?  I've never moved anything this large before, nor have I ever used Norton Ghost.

Also, if anyone has any awnsers to my the questions at the bottom of my post, that'd be cool too.

Thanks for your help, Pumalite and LaRoza.

---

### Post by Pumalite on 2007-11-18
To backup and restore, take your pick:

[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)

---

### Post by aetherh4cker on 2007-11-18
Isn't a typical Ubuntu installation divided into several partitions though?  I don't know what a typical Ubuntu installation looks like, but that was the impression that I got.

You've given me such a large list of programs, any specific ones you recommend?  Ones that can move several partitions?

Thanks again!

---

### Post by Pumalite on 2007-11-18
You have to read, learn and make your choice. That's Linux.

---

### Post by aetherh4cker on 2007-11-18
Well, it seems the GParted Live CD has Partimage in it, so I guess that's what I'll use.

Hopefully it will suit my needs.

If Ubuntu Linux itself is divided up into several partitons, will Ubuntu Linux be hurt by the move to another drive?  Like the swap partition, or something...

---

### Post by Pumalite on 2007-11-18
You want to move to another drive. That's fine. But if I were you I'd save /home and data and do a clean install.

---

### Post by aetherh4cker on 2007-11-18
> **aetherh4cker said:**
> In GRUB it shows several installations of Ubuntu.  One is an older version that was there when I first installed, the recovery for the older version, and then one that is a newer version, and the recovery for the newer version.

Why does it keep the old version around?   The new one has been working fine for me, and I’d rather delete the old one all together.  I also don’t mean just deleting it out of GRUB, but wherever it points to in order to load that older version.  Seems like it is taking up unnecessary space to me.

I might end up simply reinstalling.  Sounds easier anyway...

Can anyone answer the question?

---

