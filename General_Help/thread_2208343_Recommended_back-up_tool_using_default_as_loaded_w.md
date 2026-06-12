---
title: "Recommended back-up tool? using default as loaded with 13.1: deja-dup"
date: 2014-02-27
forum: General Help
---

### Post by keith14 on 2014-02-27
Hi,
What back up tool is recommended?
If using deja-dup is answer then:
It doesn't report completion. 
It suggests where the back-ups are written but I was not able to find same.
It reports that old back-ups will be saved until disk space becomes a limitation, where are they stored and what attributes do they have? you can not specify any when you think you're creating same.
Thanks,
Keith

---

### Post by slickymaster on 2014-02-28
Here's some food for thought:
[Backup tools Available for Debian Linux and Other Linux Distributions]("http://www.debianhelp.co.uk/backuptools1.htm")
[21 of the Best Free Linux Backup Software]("http://www.linuxlinks.com/article/20090105114152803/Backup.html")
[10 outstanding Linux backup utilities]("http://www.techrepublic.com/blog/10-things/10-outstanding-linux-backup-utilities/")
[Comparison of backup tools]("http://askubuntu.com/questions/2596/comparison-of-backup-tools")

---

### Post by keith14 on 2014-03-01
Hi, thanks for your response. I went through it as well as several other blogs on line and was interested in clonezilla home supported by saucy, downloaded clonezilla-live-20140114-saucy-amd64.zip and would like to create a drive partition to store it in. I believe I can achieve this using the ISO disk which created the partitions listed below:
   Device Boot           Start               End      Blocks   Id  System
/dev/sda1   *            2,048          718,847       358400    7  HPFS/NTFS/exFAT
/dev/sda2             718,848   194,409,177    96845165    7  HPFS/NTFS/exFAT
/dev/sda3       194,410,494   312,580,095    59084801    5  Extended
/dev/sda5       304,609,280   312,580,095      3985408   82  Linux swap / Solaris
/dev/sda6       194,410,496   304,609,279    55099392   83  Linux

I added the "," to start/end.
Why to parts 3,5,6 overlapping?

---

### Post by keith14 on 2014-03-02
The partitions are OK: see [http://gparted.org/h2-fix-msdos-pt.php](http://gparted.org/h2-fix-msdos-pt.php)
The blog [http://gparted.org/display-doc.php?name=help-manual#gparted-create-new-partition](http://gparted.org/display-doc.php?name=help-manual#gparted-create-new-partition) gives step by step on re-allocating current partition.
I did not go this way, instead downloaded ISO of clonezilla to burn CD.


Origional question what back-up utility to use? 
I cloned current OS and continue to use deja-dup (not tested if it works just cr
eate back-ups after some major change).
isolated files/DB's I use tar to pendrive.
thanks,
Keith

---

