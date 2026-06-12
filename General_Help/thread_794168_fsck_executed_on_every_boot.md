---
title: "fsck executed on every boot"
date: 2008-05-14
forum: General Help
---

### Post by shilpa.jabin on 2008-05-14
Hi,
I have Ubuntu Vmware image running on laptop with Windows OS. 
Now the issues is, for the first time when i boot the image it doesnt run fsck on /dev/sda1 where as after every reboot or halt it keeps running fsck on /dev/sda1. In log its is printed as
mount: / is busy
mount died with exit status 32

when the umountroot.sh script is run during shutdwon.

Any help is really appreciated.

BR

---

### Post by shilpa.jabin on 2008-05-14
Hi,
  I am running Ubuntu VMware image on my laptop. I am having strange fsck issue. When i boot the image for the first time everything seems to be fine and it boots in to runlevel 2 by default. On every restart then onwards, it does fsck on root saying, /dev/sda1 is not clean. I put the logs to find out if the umountroot.sh is executing properly upon init0/6. The log printed indicates as follows
mount: / is busy
mount died with exit status 32

strangely, if i change to runlevel 1 using init 1 and then execute /etc/init.d/rc 0 or 6 manually, the fsck is not done on next boot. Though the log indicates that mount died with exit status 32. If i use shutdown -r or -h in runlevel 1, the fsck is  done on next boot.

Is this problem is related to scripts? or unmounting? I have been struck in this for some time now. Any help is really appreciated..Thanks in advance.

BR,
Shilpa:(:(:(

---

### Post by pointone on 2008-05-14
Is the fsck completing without error, or is it failing and asking you to run it manually? Until fsck successfully scans the drive, it will keep trying on every boot.

---

### Post by shilpa.jabin on 2008-05-15
Hi,
Thanks for the reply. Fsck dies with exit status 3 and reboots. Upon restart, there is no fsck../dev/sda is clean. 

Br,
Regards

---

