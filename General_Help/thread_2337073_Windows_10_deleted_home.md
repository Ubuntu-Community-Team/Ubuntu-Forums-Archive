---
title: "Windows 10 deleted /home"
date: 2016-09-14
forum: General Help
---

### Post by Quarkrad on 2016-09-14
(Was) running 16.04.  I accidentally deleted my ext4 /home partition reinstalling Win10 on a GPT HD. Ubuntu sees the partition as unallocated space (live CD)  - what seems to have happened is that Windows 10 has changed the partition type to MS Data.  I have identified the sector numbers of the (lost) partition and can see it via Testdisk (installed another HD with OS running Testdisk) - (td1 attached).  If I select P (in Testdisk) to view the files I'm told 'Can't open filesystem. Filesystem seems damaged' - see tdp below.  If I select T to change the type of partition I get (tdt) of list of file types but no Ext4 - however, I'm not sure this is the way to go.  Any advice appreciated.  Note:  I've use PhotoRec on the same partition and pressing p it does show my pictures - but it all the other files I would like to recover.

---

### Post by Quarkrad on 2016-09-14
Sorry - had to rebuild; ran out of time.

---

