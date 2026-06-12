---
title: "Serious issue. Help me so I don't have to reinstall (again)"
date: 2007-11-09
forum: General Help
---

### Post by Roasted on 2007-11-09
I'll try to make this short...

I have 3 hard drives. 250 (a) 250 (b) and 200 (c)

The first drive (a) is partitioned like so: 25gb Windows, 2gb Swap, 13gb Root, remainder is Home.

Drive B and C are simply backup drives. I have a script that I run, which is this - sudo rsync -a --progress --delete ~/ /media/Backup1 (or Backup2 is we're talking about drive C, but in this instance we're not)

sdb2, which is drive B, is mounted as Backup1.

Yet, I just got an error saying low disk space. SOMEHOW it is writing the stuff in my home directory to root. The last time this happened I was unable to even boot back into Ubuntu. I have no idea what to do. I mean... damnit this is frustrating. SDB2 IS MOUNTED AS BACKUP1. Why in the world is it writing to root? Where in root can I find the files so I can delete them so next time I reboot I can actually get INTO Ubuntu?


new curve ball - SDB2 wasn't mounted. My mistake. But... BUT!!! How in the world does that justify it writing all of my info to root instead of saying "SDB2 NOT MOUNTED!" ???????

---

### Post by geirha on 2007-11-09
Just to make sure, it's mounted to /media/Backup1 and not /media/backup1 for instance? 

It's case sensitive, so if you don't get that right, it will create a new directory in /media/, which is part of the root partition.

---

### Post by dabl on 2007-11-09
Is there anything in the hidden file .trash on the root partition?

Otherwise I guess I'd browse through /usr and see if there's anything huge lurking in there.

How big is your root partition?

---

### Post by Roasted on 2007-11-09
brain fart - how do I get to the .trash file?

it's a 13gb partition, but it's like 11.9gb usable, which 11.9 is currently being used with 0 bytes of free space. YES! SWEET!

---

### Post by geirha on 2007-11-09
Boot the ubuntu-cd, open nautilus by going to places->home for instance
In the left margin you should see your partitions listed with sizes, so double click the one with 13GiB, that will mount it. Double click again and you're looking at your root partition in nautilus.

---

### Post by Roasted on 2007-11-09
I noticed something...

When I unmounted sdb2, the contents were still inside the Backup1 folder to which sdb2 was mounted to. The contents inside were 8.7 gig, which is exactly what it took to fill up my 11.9 root.

I guess the problem was, I commanded linux to rsync everything to my Backup1 folder which WAS in existence. The thing was, sdb2 wasn't mounted there to take the load, so it got put on root.

I love learning things the hard way.

---

### Post by dabl on 2007-11-09
> **Roasted said:**
> 

I love learning things the hard way.



The lessons are more memorable that way.  :lolflag:

---

