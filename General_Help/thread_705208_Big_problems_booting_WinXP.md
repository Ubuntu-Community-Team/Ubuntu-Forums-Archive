---
title: "Big problems booting WinXP"
date: 2008-02-23
forum: General Help
---

### Post by mnfl on 2008-02-23
Hi.

Yesterday I installed Ubuntu 7.10 but quickly understood that it was more then I needed. I did the "fixmbr" and thought that would do it. Let's say I screwed it.

To cut a long story short I wonder if it is possible to recover six months of work from the former partion now apparently lost. 

Whats the best way of doing this? It's all on a laptop so I cannot easily move the disk to my stationary.
Can I re-install XP and still use a recovery tool to find some of my stuff? 
Should I do a third partition when installing a new OS?

Any help would be grateful.

Best regards.

---

### Post by angrboda on 2008-02-23
Hi there,

your chances to boot XP and/or recover your data depend on how you intalled your Ubuntu. On most systems (especially with a pre-installed Windows (of whatever flavour)) the MS-Os will use all hard disk space. During install you would have been asked whether you wanted to keep the other OS and resize its partition to make room for Ubuntu or else let Ubuntu use the whole disk. If the first, you will only need to edit the /boot/grub/menu.lst to include XP ...  if the second I am sorry to say you lost your data for good... 
The way I understand your post you have a partition for XP, so unless you have formatted it XP and your data should still be there. If that be so add something like this to your menu.lst:

```
 title         Windows 95/98/NT/2000/XP
 root          (hd0,0)
 makeactive
 chainloader   +1
```

where (hd0,0) might have to be aadjusted to point to your Windows - partition

If XP is still there you should get a menuitem to boot it when pressing ESC on startup to bring up the grub menu...

---

### Post by mnfl on 2008-02-26
Thanks for your answer!

I tried the Ubuntu-thing, but with no success. Worth to mention is that the Ubuntu installer asked me how to deal with partitions this  second time, but certainly not the first time. Otherwise I would not be here at all. I hope everyone who's installing Ubuntu know about this disastrous bug.

Anyway, I eventually unmounted my laptop hard drive and plugged it in to my stationary and ran GetDataBack for NTFS. It was all there! I am currently copying the files to a brand new external HDD, later meant to act as a back-up machine. Oh-why did I had to learn why to back-up the hard way?! 

+ Fancy new HDD.
- $$$ GDB License.Feeling stupid not to back-up.

Best regards, 
Gustav

Stockholm

---

### Post by angrboda on 2008-02-27
Hi Gustav,

I am sorry to hear it didn't work.
The semi-bad news (at least in terms of money spent): If it was all there, it is very likely that with a little work it should have been possible to set up your system for dual boot...
To look at the bright side: an external hdd is a very good thing for backups - using DVD or (worse) CD media can be a right pain unless the system to backup is relatively small... and I guess you've just been taught (the hard way, unfortunately, as you said yourself) the value of a backup.
Don't fret, I dare say something like that happend to most of us at some point (though we would never openly admit it, of course ;-)  ) ... as humans we learn through error... just keep asking questions (that is what this whole forum is about, after all) and don't let any piece of machinery or software discourage you.
I hope this has not completely ruined the Linux/Ubuntu-experience for you.

Regards

---

### Post by mnfl on 2008-03-09
Hello again!

You may be right, but since 5-10% of my files from my win-partition is corrupt I feel a little sceptical. My version is that the Ubuntu installer did not recognize the other OS. But who knows. Anyway - thanks for caring! 

/G

---

