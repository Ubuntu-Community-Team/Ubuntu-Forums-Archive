---
title: "Recognizing IDE slave in XP"
date: 2008-01-13
forum: General Help
---

### Post by k.i.s.s. on 2008-01-13
After searching through thread after thread I soon get bogged down in info that is inapplicable to my problem so I am going to simply state my prob and would greatly appreciate any help.

Have Windows XP on primary SATA HD. Had a second IDE HD as slave to CD-RW on IDE controller, which I used for file storage. All was working fine. I could access these files through My Computer since each partion in IDE slave was listed as E, F, G, & H.
I installed ubuntu on this slave IDE HD after first disabling SATA HD C with XP in BIOS. Now I can boot up into Win XP or ubuntu by changing sequence in BIOS. My problem is that I want to access the files (or what is left of them after ubuntu partitioning) on the slave IDE HD thru Win XP on the primary SATA hd but slave IDE doesn`t  show in My Computer.
What is the simplest solution? 
Thanks! :)

---

### Post by -grubby on 2008-01-14
well you'd want windows to have read/write support for ext3. The closest thing I found was support for ext2
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by k.i.s.s. on 2008-01-14
Thanks!

That looks like a workable solution and should not screw up my Win XP on the primary drive, which is my main concern. Since this can be removed or uninstalled thru add/remove in Control Panel it won`t adversly affect my Windows OS.
THX again. Will post back with the results when I get the time to install and run the program.

:)

---

### Post by k.i.s.s. on 2008-01-14
The "Ext2 Installable File System for Windows" did the trick! Now I can read/write to the 2nd HD. Unfortunately I wiped out the whole drive with all of my music, video, etc. files when I installed ubuntu, thinking I was just using the first partition! But at least now I can use it with XP again. And I have ubuntu, such as it is, with no sound and looking like it will take some major configuring, etc. to get it up to an OS I would be comfortable with.
Thank you nathangrubb for your time & help! :D

---

