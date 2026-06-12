---
title: "iSCSI Problem"
date: 2008-03-21
forum: General Help
---

### Post by Particle on 2008-03-21
I am posting this here because I don't know what part this problem lies with:  the OS, the VM, the target software, etc.

I made a script yesterday that installs iSCSI Enterprise Target onto a fresh install of Ubuntu server or desktop ([available here if anyone cares)](http://downloads.pcrpg.org/iSCSI%20Enterprise%20Target.sh).  However, I am having an odd problem.  Everything installs right, runs, you can discover, you can connect to a target, and you can even write data it seems...however, I can not get Windows to format the volume for the life of me.  If I do a quick format it just sits there forever.  If I do a full format, it will zero out the disk to 100% (hence I know it can write to the volume) and then sit there forever.

Any idea what I'm doing wrong?  Alternately, how can I format the drive in ubuntu to fat32 or ntfs (text mode [and for example's sake, let's say it is /dev/sdb]) and see if it works once pre-formatted?

---

### Post by Widodh on 2008-03-25
Have you tried a Linux iSCSI client for this?

Just boot a Ubuntu Live CD in a different machine and install open-iscsi as client (initiator) and try to use the device.

Does that work?

And also, post you ietd.conf please!

Oh btw, IET is available in the Ubuntu repositories!

---

### Post by yanman on 2008-05-05
Particle - thanks for your install script!! I used it any got iSCSI target working. I then used [this guide]("http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1280953,00.html") for some lines of the config and used my currently empty RAID volume /dev/md3 as a test. I then used the MS initiator and managed to mount it easy. It took a while to do a quick format (maybe 2 minutes) but after that I was able to copy data to and from it fine!

---

