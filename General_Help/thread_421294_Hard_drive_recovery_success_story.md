---
title: "Hard drive recovery success story"
date: 2007-04-24
forum: General Help
---

### Post by jakev383 on 2007-04-24
I've been working on a project involving WRAP.2C boards (embedded computers) that run off of compact flash (CF) cards. I've been working out some bugs and needed to reinstall Voyage Linux on the card. It was late, I was tired, and it had been a really log day. That's no excuse, but it's what I'm sticking to.
Anyway, I needed to reformat the CF card, so I issued the command:
mkfs.ext2 /dev/sda1

and ran through the install scripts as normal. Got it on the card, and still had issues, so I gave up for the night. The next morning I fired up my laptop to read my email. Nothing. Black screen with a flashing cursor. Thinking back, I had MEANT to:
mkfs.ext2 /dev/sdb1
NOT sda1!!!!! That's my laptop's HD! I dual boot this thing (actually haven't booted WinXP in 5 weeks now), but I had a LOT of programming code on there that I had not checked into my SVN yet, family pictures, emails, etc. Crap-ola. I get on my other computer and download SystemRescueCD ([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) and start to look at my drive.... Well, instead of 7 partitions now, it's 1. And ext2, whereas the other partitions were ext3, NTFS, FAT32.  I decided to try the testdisk program and see what it could do. Well, it found all my old partitions, so I wrote that to my disk. Now we're doing good. I can mount my old partitions now, and I proceeded to cp -R * dirs to my Samba share - just in case. The next day (lots of data), I reboot it. Still a black screen with a blinking cursor. Crap. Back to the RescueCD.  Seems all the partitions are there, and the first partition is bootable.... I find a /boot partition on my / partition, so I copy the contents to sda1. Still no go. Grub must be dead.
That one isn't too bad. Boot into the liveCD, and issue these commands:
```

sudo grub
find /boot/grub/stage1

```
(hd0,5)  /* I think this is what got returned */
```

root (hd0,5)
setup (hd0)
quit

```

Reboot, and success!  Ubuntu ran REALLY slow the first time I booted it, but every time after that it's been normal. I also lost my swap, but was able to turn that back on using swapon -a. All in all I won't complain about those 2 things, since I got everything back. 
Hopefully this will help someone else in the future if they run into the same problem.

---

### Post by dannyboy79 on 2007-04-24
this is awesome, I have used testdisk to bring back from the dead a couple of computers. the part I don't understand is why when you did mkfs.ext2 /dev/sda1 did it erase all your partitions? That command should have only created an ext2 partition at parititon 1 of the sda drive?

This is also a wake up call to you to backup your stuff!!!! I use sbackup, it's awesome. I have even tested the resulting files.tgz and when I performed a full restore everything was a-ok!!!! otherwise if you don't mind the command line and cron, just using tar is good enough. that's all sbackup uses but it's got a neat litttle frontend which also allows backup to ssh servers as well ftp servers.

---

### Post by jakev383 on 2007-04-24
> **dannyboy79 said:**
> this is awesome, I have used testdisk to bring back from the dead a couple of computers. the part I don't understand is why when you did mkfs.ext2 /dev/sda1 did it erase all your partitions? That command should have only created an ext2 partition at parititon 1 of the sda drive?

This is also a wake up call to you to backup your stuff!!!! I use sbackup, it's awesome. I have even tested the resulting files.tgz and when I performed a full restore everything was a-ok!!!! otherwise if you don't mind the command line and cron, just using tar is good enough. that's all sbackup uses but it's got a neat litttle frontend which also allows backup to ssh servers as well ftp servers.
I'm not sure why it wiped my partitions, either. All I know is I ended up with one 120G ext2 partition. I'm just hoping that this will help someone else in the future when they run into the same problem. I know I'm guilty myself, but most people don't post what the solution was.
As far as backups.... Yeah, I'm using the same SystemRescueCD and making backups with partimage. At least for the moment - in the near future I want to do incremental backups (at least for my / and FAT32 shares) so I'll be looking at solutions for that soon.
Have a good one!

---

### Post by dannyboy79 on 2007-04-25
just you are aware, restoring an NTFS Windows install to a NTFS partition may or may not work and if I were you and you haven't tested this ever, I would sure test it soon ebfore trusting this whole time that you have backups that will work in case of a disaster.

---

