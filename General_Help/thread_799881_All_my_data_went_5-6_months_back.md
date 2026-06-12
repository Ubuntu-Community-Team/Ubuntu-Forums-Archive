---
title: "All my data went 5-6 months back?"
date: 2008-05-19
forum: General Help
---

### Post by mogie on 2008-05-19
One of my HDDs on my Ubuntu 6.10 server had a power failure, and after starting the server again all my data on my /home folder (one HDD is mountet to /home and the rest of /, and the other one to /media2 etc.) have gone some 5-6 months back in time. It seems that a recovery or something has been startet at boot-up: heres all messages from the bootup:

[IMG]http://www.diskusjon.no/index.php?act=attach&type=post&id=229466[/IMG]

what has happend? anyone? :( this is a crisis BIGTIME!!

---

### Post by bobblehat on 2008-05-19
Probably you also have a /home directory on the other drive with some old data in and you're seeing that because the drive that contains your current data failed to mount.

---

### Post by mogie on 2008-05-19
> **bobblehat said:**
> Probably you also have a /home directory on the other drive with some old data in and you're seeing that because the drive that contains your current data failed to mount.

Thats impossible. There is only one partition on the other drive I have - its about 467GiB (500GB), and it contains only static data mountet to the /media2 folder.


It is clearly that all the content on the / (all except /media2 ofcourse) has been set back 5-6 months! I can recognize the data.

I have a hw RAID 1 (mirror) set on the / -partition (including /home of course), and I'm curious if anything has happened here during bootup. Anyhow, it should have nothing to say since the content on both disks are the same.

Should I dare to make a reboot to check it out? or should I do a fsck or something before this...or what? :(


Edit:

I made the reboot and everything is back to normal...? :P Alle my files are just the way they were...


WHAT HAS (MOST TRULY) HAPPENED:
The HW RAID-1 array did not start at boot-up - therefore only one disk was beeing mounted to /. It's then clear that the content on this disk has not changed since I started up the RAID-1 array (it has never worked). I then got a problem to solve here..

Why the array did not start up at boot i still unclear to me..

---

