---
title: "have to move 200gb from one pc to another"
date: 2007-11-09
forum: General Help
---

### Post by gian on 2007-11-09
I am rebuilding my server, and have to move a pile of GB from one Ubuntu box to another, which way is faster?

[LIST=1]
[*]scp via SSH
[*]usb2 disk
[*]NFS
[/LIST]

thanks for your time,
-Gian

p.s. I need to save all file permissions, if possible.

---

### Post by stinger30au on 2007-11-09
anything is faster then multi-spanning 1.44 meg floppy discs, or sending it via morse code , or via smoke signal, or... you get the idea:lolflag:

---

### Post by TheExplorer on 2007-11-09
NFS is faster. But better is dd command (disk 2 disk bit2bit copying).
If I'm not mistaken:
```
dd <from_location> <to_location>
```You'd better google it out.

P.S. With SSH you will loose file permissions. With NFS you'll have to look it depends on how your devices are mounted. Not sure.

---

### Post by Prospero2006 on 2007-11-09
I second dd

I use it to move +200 gb across the network frequently.

dd if=/dev/(input hard drive) of=/mnt/remotedirectory/harddriveclone.iso

This will create an iso file on the remote computer that you can browse and work with provided you insert the correct 'remotedirectory' and 'input hard drive'.

Pros

---

### Post by mixmaster on 2007-11-09
Stick the old HD in the new box temporarily?

---

### Post by gian on 2007-11-09
thanks all for the suggestions...

I need to reuse the same hardware, which has a raid array.

dd looks more appropriate for entire disks/partitions of the same size, if I'm not wrong.

---

