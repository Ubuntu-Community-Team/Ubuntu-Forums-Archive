---
title: "When I boot up, my drives are mounted. Why?"
date: 2006-09-25
forum: General Help
---

### Post by Roasted on 2006-09-25
I have 2 drives. 

Drive A: 30 gig Windows partition/205 gig Linux partition.
Drive B: Backup drive, used with rsync.

Windows partition is SDA1.
Backup drive is SDB2.

When I boot up SDA1 and SDB2 are on my desktop. I don't want them mounted. I have NO use for SDA1 (windows) to be mounted, and my backup drive (SDB2) I set up a script to auto mount/rsync/auto unmount, so no need to keep it mounted.

How can I alter this to make these two drives not auto mount upon system start?

---

### Post by pay on 2006-09-25
Comment out (#) SDA1 and SDB2 in the /etc/fstab file

---

### Post by orb9220 on 2006-09-25
open a terminal and enter folowing command.

gksudo gedit /etc/fstab

add # in front of drives mounted in media/

---

### Post by Roasted on 2006-09-25
Thanks. Worked great.

What exactly is fstab? It's file system table, right? Is the fstab file basically a file that commands what hard drives to do what?

---

### Post by pay on 2006-09-25
It's a file that contains information on where your partitions are and how and where Linux should mount them. It also handles CD/DVD drives.

---

### Post by Roasted on 2006-09-25
I see. And by gksu gedit'ing it, I obtain full control over that... hence me unmounting my other 2 partitions that kept auto-mounting upon boot.

Cool shit. Learn something new everyday.

---

