---
title: "Anyone using backuppc?"
date: 2007-09-14
forum: General Help
---

### Post by amadeus266 on 2007-09-14
I am very good with computers and have looked at the documentation but it is a little too technical for me to get my head around. My questions are as follows:
1. Where are the backup files stored?
2. Can backuppc be set up to run automatically at certain intervals?

---

### Post by LRT on 2007-09-14
i'm currently trying to install backuppc on my ubuntu 7.04. its not going that well. i tried following the documentation and just using apt-get install backuppc. the software is very powerful. it can do more than you really ever need. the files can be stored anywhere, local or remotely, (with smb, cygwin or rsync). backuppc is completely customizable.

---

### Post by amadeus266 on 2007-09-17
How would one go about changing the location of the stored backup files?

---

### Post by wirelessmonkey on 2007-09-17
Yes, I do!
1) Typically files are stored in /var/lib/backuppc, this can be changed via the configuration file.
2) Yes, this is part of the nature of the beast.  This is also set via the configuration file, either the primary or in the per-machine configuration.

The configuration files are found in /etc/backuppc or you can edit them via the web interface.

---

### Post by peachy on 2007-10-24
It took a bit of hacking about /trial and error to get backuppc working but now that it is I can say it's by far the most flexible, powerful, quick and robust backup solution I have seen for an environment where you have a network of laptops that may or may not be connected at any given time.

Setup was actually easy, I was just trying to solve non existent problems. I should have started by ensuring the backuppc server could connect to the hosts using rsync (n.b., use rsync for windows hosts too, it rocks)

---

### Post by wirelessmonkey on 2007-10-24
The big problem I've found is backing up Windows Server... Backuppc does not copy locked files, i.e. MySQL tables/Active Directory.  To do so requires VSS (Volume Snapshot Service" utilities like vshadow, and a lot of custom scripting.   Sadly, I had to move away from Backuppc to Bacula, which is much less user friendly, but supports VSS natively.

---

