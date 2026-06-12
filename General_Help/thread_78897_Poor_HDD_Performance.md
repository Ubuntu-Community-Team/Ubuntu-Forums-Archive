---
title: "Poor HDD Performance"
date: 2005-10-19
forum: General Help
---

### Post by mb2k on 2005-10-19
Dear all,

I`m currently running Kubuntu / Ubuntu on my Server-rig (p4 2.6ghz, DFI I875 Board, 1GB Ram etc...).

I have installed 2 x 200GB Samsung SATA Harddrives as sda and sdb, plus one 160gb Samsung PATA drive as hda.

My / & /home dir resides on sda with XFS as filesystem and an LVM, and my old data and backup files are running on the hda with ext3 partition.

When I now copy large files ~700mb from hda to sda using for example MC, I really have worse performance.

It`s around 3-4 MB per second.

When I copy the same file from sdb to sda, I`ll get around 25-30 MB / sec.

I already tuned the hda with hdparm as described in here: 
[http://paul.hahn.name/Articles/InstallRepDir/HDParm/view](http://paul.hahn.name/Articles/InstallRepDir/HDParm/view)
or here
[http://usalug.org/phpBB2/viewtopic.php?p=33142](http://usalug.org/phpBB2/viewtopic.php?p=33142)

But it does not really make a difference !

Somtimes the speed goes up to 6-7 MB/s, but that is also quite nasty ...

Does anyone have a clue what might be the lack or problem ??? 

On my Fedora Core 4 Server, I never had issues like that...

---

### Post by darknuala on 2005-11-16
I have had bad experience with SATA on linux period.  I had similar problems as you but the hdparm thing fixed me.

---

### Post by frodon on 2005-11-16
You may need to add the good line (corresponding to your cpu) in /etc/module, it worked for me.
More details here (in  troubleshooting section) : [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

