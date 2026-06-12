---
title: "Second HDD not being seen"
date: 2007-03-30
forum: General Help
---

### Post by Dream. on 2007-03-30
I have xp on my master drive and ubuntu on my slave, thanks to the kind ppl of this forum I can now boot to either o.s.

When in either o.s. I cant see the other drive to access it, I can however see the slave in device manager (xp) and the master in device manager (ubuntu)

I have searched the forums and I understand I need to mount the drive in ubuntu:confused: 

Is it possible also to access the slave(ubuntu drive) from xp?

---

### Post by taurus on 2007-03-30
If you want to access Ubuntu drive while you are in XP, you need to install [http://www.fs-driver.org](http://www.fs-driver.org).

And if you want to access XP while you are in Ubuntu, then you need to mount your master drive first.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Dream. on 2007-03-30
Thankyou taurus, I managed to mount the master drive and can now see the files on that drive from ubuntu.

As for installing the "Ext2 Installable File System For Windows", after reading the F.A.Q. on "Does the Ext2 driver access Ext3 volumes, too?" I am pretty much lost.

A few questions (if you dont mind)..

1. "The ext3 file system has to be mounted as ext2."

Does the 'Ext2 Installable File System For Windows' do that, and does it do that each time you boot into xp? and then dismount when shutting down?  (If so how long does it take?)


2. "If you mount an Ext3 file system as an Ext2 file system and the file system is not cleanly dismounted, (e.g. due to a system crash), you have to run the e2fsck tool.(Linux does it automatically.)"

When you boot into ubuntu it will automatically repair this?

3. " The Ext2 file system driver of the Ext2 IFS software will refuse mounting an Ext3 file system which contains data in its journal, just like older Linux kernels which have no Ext3 support. In this way data loss and damaging the file system is avoided when the journal is subsequently replayed. So you can access only those Ext3 volumes with the Ext2 IFS software which have been cleanly dismounted beforehand."

So here you would boot into ubuntu and run the e2fsck tool and then reboot into windows so it can properly mount the file system?

Overall how successful/stable is the "Ext2 Installable File System For Windows", do you use it and do you recommend using it?

One last question, can I install ubuntu on a Ext2 filesystem to avoid this and would that be recommended?

Cheers...       insert :very confused:  smilie

---

