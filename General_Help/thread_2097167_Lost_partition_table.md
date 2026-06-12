---
title: "Lost partition table"
date: 2012-12-22
forum: General Help
---

### Post by ravindasenarath on 2012-12-22
Hi,

I have a WD My Book 500GB external hard disk which I have been using for yesrs. Today when I plug it in it didn't power up as usual. I tried several things(including googling) and nothing works. So assuming the power adapter has blown up I removed the chasing and got 500GB SATA hard disk out. Then I plug in directly to the machine using SATA. I have my primary hard disk which is a IDE one(I didn't change any jumper settings). I heard the usual creek sound which I have heard while the hard disk power up before( some relief because at least it is woring). But once ubuntu booted up it didn't show external hards(which now has plugged in internally) partitions. I tried Disk Utility application. And disk is there. 

[IMG]http://i46.tinypic.com/2crovep.png[/IMG]

So I'm not sure what is the problem here. Disk utility says disk is healthy. Am I facing a lost of partition table problem? So I must try to recover data or is this something else?

Thank you

---

### Post by oldfred on 2012-12-23
That it is showing the entire drive as free does say a partition issue.

I might try testdisk to see if it can see the old partitions.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by ravindasenarath on 2012-12-23
thanks oldfred. I'm off from home now(on work). I left the hard disk at home. I'll try your solutions on next Saturday. I'll be back with results. :)

Thank you

---

### Post by ravindasenarath on 2012-12-29
I try to recover the disk but couldn't. After some further digging in I found that WD My Book external disks have a hardware encryption. So because of that without the enclosure it is impossible to read data. 

[http://carltonbale.com/western-digital-mybook-drive-lock-encryption-failure-and-recovery/](http://carltonbale.com/western-digital-mybook-drive-lock-encryption-failure-and-recovery/)

So as it seems I have run out of options. Previous post suggest that using a working enclosure it may be possible to read data. But it is not guaranteed different enclosures may use different key's to encrypt data. 

As my last option I post on WD support service. I don't know whether they'll attend to my case because warranty period is over.

---

