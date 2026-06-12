---
title: "edgy: &quot;/bin/sh: can't access tty; job control turned off&quot;"
date: 2006-10-31
forum: General Help
---

### Post by jeppester on 2006-10-31
I updated my ubuntu to edgy eft this weekend and it has been working very well untill now. When i booted it the boot screen appeared, but there was no progress. So I decided to start up in recovery mode. Unfortunately i got this message: "/bin/sh: can't access tty; job control turned off". Now I can't do nothing! I've seen other topics about this issue and i've tried pressing ctrl + alt + F1-F7 but nothing happened.
I'm thinking about whether it's possible to start from a live-cd and somehow repair the installation.
please help me, i really don't want to start all over.

---

### Post by sfagerhaug on 2006-11-02
I have this same issue.    I installed edgy a few days ago and now cannot boot linux at all.   I'm about ready to reinstall dapper unless someone knows what this error means and how to fix it.

---

### Post by jeppester on 2006-11-02
I booted a live-disk and when I mounted the filesystem it was corrupt, so I had to reinstall, luckily I keep /home on another partition, so it was not at big problem...
so it would be a good idea to check whether your partition is corrupted

---

### Post by taurus on 2006-11-02
Try booting your PC with the LiveCD and mount the partition where / is.  Then, look to see if you have /bin/sh on your / at all...  Here is how.  Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo mkdir /mnt/ubuntu  <-- create a mount point
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu  <-- mount your Ubuntu partition, assuming it's on /dev/hda1!!!
ls -la /mnt/ubuntu/bin/sh  <-- check to see if you have /bin/sh on your harddrive
(And if you don't have it, then you need to link it as...)
cd /mnt/ubuntu/bin  <-- change directory to your harddrive
sudo ln -s bash sh  <-- create a link
cd ~  <-- move out of your harddrive back to your LiveCD
sudo umount /mnt/ubuntu  <-- unmount your harddrive

```
Reboot and remove your LiveCD and see if you can log in to your computer now!!!

---

### Post by sfagerhaug on 2006-11-02
I checked my hard drive and I do have the bourne shell (/bin/sh) ...

I saw in some other threads on this topic that there may be some problems with the "generic" kernel image (which is what edgy decided I needed to replace the "686" kernel I was using on dapper).   They were saying that the plain "386" kernel might work.    What kernel image are others using?

How can I get the "386" kernel image if I can't log in?   Is there a way to use the live CD to boot and chroot into my setup and install another kernel?

My system is an HP Pavilion with pentium 4, 1 GB Ram and intel graphics.

Any other ideas?

---

### Post by taurus on 2006-11-02
I have both versions, i386 and i386-generic, and they're both working fine for me!  On the other hand, my /bin/sh looks like this on my Edgy...

```

lrwxrwxrwx 1 root root 4 2006-10-28 09:39 /bin/sh -> dash

-rwxr-xr-x 1 root root 79912 2006-07-11 15:31 /bin/dash

```

---

