---
title: "problem mounting a cd-rom"
date: 2014-09-03
forum: General Help
---

### Post by charitosha on 2014-09-03
I found some information on how to mount stuff but I had no luck in mounting my cd-rom.
I'm trying to do that on an old acer laptop travelmate 251lc_dt
The case is more and less the same. I insert the cd,it spins, but from there and on nothing.
from sudo lshw:
```

     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: CDRW/DVD SBW-242
             vendor: QSI
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: UX10
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc

```

```

diana@Acer250:~$ mount /dev/cdrom
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab
diana@Acer250:~$ mount /dev/sr0
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab

```

and lastly:
```
diana@Acer250:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=diana)

```
Any suggestions or guidance???

---

### Post by mcduck on 2014-09-03
Since the drive is  not configured in /etc/fstab, mount doesn't know where to mount the drive unless you actually specify the mount point in the command you run.

So:
```

sudo mkdir /media/cdrom
sudo mount /dev/cdrom -t iso9660 /media/cdrom

```
and then to unmount afterwards:
```

sudo umount /media/cdrom
sudo rm /media/cdrom

```

If you configure the cdrom drive with mount point, filesystem and other options in /etc/fstab and create the mount point beforehands, you can then use the simple *mount /dev/cdrom* command as mount can check the rest of the required info from the fstab file.

---

### Post by charitosha on 2014-09-03
mcduck thank you for your reply,
so, i wrote the ```
sudo mkdir /media/cdrom
``` line,had no reply, but i'm assuming that the directory got indeed created.
but, then:
```

diana@Acer250:~$ sudo mount /dev/cdrom -t iso9660 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: no medium found on /dev/sr0

```
how come and the device write-protected?
also how it's possible that no medium is found in /dev/sr0, even if it's shown from lshw?

---

### Post by mcduck on 2014-09-03
Makes sense, the file system used on CDs is write-only by design as that's how CD's work (you can't change or add individual files, the whole filesystem on the disc is created at the same time). So even CD-R and CD-RW are read-only filesystems unless you set up and use a packet writing software (which will use a different filesystem, UDF instead of ISO9660, loosing some of the space & compatibility to make it possible)

And lshw shows you the *device*, the CD drive itself, while mount deals with the *filesystem* which is stored on the disc you put in the drive. So as long as you have a CD drive on your computer, lshw will be able to show it. You still need to insert a CD that contains a filesystem (not empty disc) before you can read anything from the drive.

---

### Post by charitosha on 2014-09-03
That's some information that i didn't knew....
 > You still need to insert a CD that contains a filesystem (not empty disc) before you can read anything from the drive.
Also sorry for my ignorance but how your reply helps me? what type of filesystem should the cd contain?
i inserted a random non empty disk, but still the sudo mount gave me the responce of my previous post.

---

### Post by mcduck on 2014-09-03
Well, the error "mount: no medium found on /dev/sr0" would indicate that either there is no disc in the drive, or the disc isn't a normal data CD that contains files. (music CD's or empty discs won't work as they don't contain any actual files) Can you check that the disc you tried works on some other computer?

If you are sure the disc is fine, then there could always be some compatibility issue with your CD drive, although that seems a bit strange as lshw has detected it correctly. Or if you haven't used the drive in a while, it might just be that the read head needs some cleaning

---

### Post by charitosha on 2014-09-04
The ```
sudo mkdir /media/cdrom
``` worked. There is such a folder.
Now i tried multiple cd and dvd with text files pdf etc, no music or videos and i got always the same replies:
```

diana@Acer250:~$ sudo mount /dev/cdrom -t iso9660 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: no medium found on /dev/sr0
diana@Acer250:~$ sudo mount /dev/sr0 -t iso9660 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: no medium found on /dev/sr0

```
But let me ask you this: In order to mount a device, in this case a cd-driver, it really needs to have a cd/dvd in it?
And more importantly if the above fails, what should i do in order to mount it? I mean it should be possible to mount a cd-driver.

---

### Post by mcduck on 2014-09-04
Yeah, you need the CD or DVD in the drive, since you don't actually mount the *device*, only the filesystem stored on the device. (And in case of optical media, the filesystem is not stored on teh devcie but on the  CD or DVD disc you put into the drive.)

It seesm to be a bit of a strange problm, th commands you use are corrct, the drive itself is recongized and seems to be working, but it's not able to read (or even detect) the discs. At this point I'd probably try to get a lens cleaning disc and run it a copuple of times just to see if cleaning the optics in the drive solves the problem. (Or, since CD's should be mounted automatically when you run any of the Ubuntu's desktop versions, log into the desktop and see if CDs work there. Or try booting with a Ubuntu live disc, if the drive is working then that should work without any issues, and if it doesn't read the live disc then you'll know it's a hardwareproblem...)

---

### Post by charitosha on 2014-09-04
Via the Discks program (in Lubuntu) i can see the cd driver eventhe eject botton works.
However when i made it to mount at start-up, at the Lubuntu loading screen i got the error that it couldn't mount. Had 2 options either to skip it or to try fix it manually....

---

### Post by charitosha on 2014-09-06
Can somebody answer me 2 question:
1)Via the Discs program(the 2nd picture of my previous post) it has a tab which has the mount options that are stored in the fstab file. Are those simply there by default? I'm asking because in the fstab file there is no entry for the cd-driver...
2)Is it possible instead of using the UUID, to use symlink or just the by-id (of the device), in the fstab file? I'm asking this because apparently cd-drivers don't have uuid

---

