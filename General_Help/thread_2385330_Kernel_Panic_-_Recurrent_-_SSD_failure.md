---
title: "Kernel Panic - Recurrent - SSD failure???"
date: 2018-02-19
forum: General Help
---

### Post by ^_Pepe_^ on 2018-02-19
Hi all. 

I have a home server, headed, with a 16.04 LTS from...let me check...8.04. Upgraded carefully and successfully from there. Even with a HDD to SSD migration. Lots of things on it. LDAP, Torrent, DLNA, Samba....

So...one day, one week ago, kernel panic. not syncing VFS. I've tried several solutions, but any update-grub2, does nothing. And...which is more important...if I try to start from a old 12.04 from other HDD...kernel panic too.

I've reinstalled fresh 16.04, all solved. 

Yesterday, all was cracked again. And kernel panic again. 

Any clue???

I'm starting to think that SSD is failing somehow. 

Thanks. 
^_Pepe_^

---

### Post by TheFu on 2018-02-19
Did you check the logs?
SMART data for the disk?
Does
```
$ journalctl  -k  -p err
```
show anything?

---

### Post by ^_Pepe_^ on 2018-02-19
I have to start with a live pendrive, so, I'll try to get some info from the syslog (no idea what can be there), and fsdsk. Thanks for tip

---

### Post by TheFu on 2018-02-19
I have no idea what "fsdsk" is.  **smartctl** is the tool to read SMART data.
To read kernel panic data, sometimes that doesn't make it to any text log files, so only the journalctl get them.  I have not idea how to tell a live-flash drive to read the journalctl logs from the other disk.  Let me see what google can find .... 

Looks like you can use journalctl --directory=DIR to tell it to read logs from a different place.  There's also a --root= option that seems to want a path to an alternate root directory (probably something mounted in /mnt/ from a rescue boot on a flash boot?).

IDK.

---

### Post by ^_Pepe_^ on 2018-02-19
> **TheFu said:**
> I have no idea what "fsdsk" is.  **smartctl** is the tool to read SMART data.

I meant fsck, but I'll go for smartctl and badblocks

---

### Post by ^_Pepe_^ on 2018-02-20
Hi all. 

Just for the record. 

1. Started with a live pen. 
2. smartctl gave me some pre-fail and...fail. Kingston SSD, for info. 3 year, 24x7. Unnaceptable.

3. fsck -a repaired some blocks

and...

restarted...and beeps from RAM. I have been moving around the sticks through the banks, and finally 3 of 4 worked. 

Sounds bad. This hardware is pretty old (E8400, heavily overclocked for gaming in the past, now 24x7 underclocked server, but...) I think all is hardware related. It's like a "systemic failure". 

4. Now it's up, refreshing SMART info in all disks (4), but I'm looking for new hardware anyway, including SSD. 

Thanks to all

---

