---
title: "Error after Hardy upgrade"
date: 2008-04-24
forum: General Help
---

### Post by Son of Silas on 2008-04-24
Hi,
I just upgraded one of my PCs to Hardy this morning and it appears something went wrong.

When it boots it drops me to a black screen with the error:

> The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

After a bit of fumbling around it appears it is halting when e2fsck checks 2 HDDs I have.

My fstab has the following lines:
> /dev/hdb1	/media/Media	ext3	auto,rw	0	1
/dev/sda1	/media/MediaServer	ext3	auto,rw	0	1

I have discovered if I comment them out, the PC boots fine presumably because they are not mounted e2fsck doesn't check them?
Once the pc has booted i can mount them manually and the work fine and if I type mount I see the following:

> /dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/Media type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1 on /media/MediaServer type ext3 (rw,nosuid,nodev,uhelper=hal)

Anyone have any ideas what I can do?

---

### Post by coyotito on 2008-04-24
I find the delay when ubuntu checks windows drives very annoying, it slows the boot process by 20 secs at least.
I boot them manually with xvmount when I need them.
So if that is a possible option .. it's very fast and easy.

---

### Post by Son of Silas on 2008-04-24
After huge amounts of help from a friend (thanks Adam) the solution seems to be:
Change my fstab from 

> /dev/hdb1 /media/Media ext3 auto,rw 0 1
/dev/sda1 /media/MediaServer ext3 auto,rw 0 1
to
> /dev/sdb1	/media/Media	ext3	auto,rw	0	1
/dev/sdc1	/media/MediaServer	ext3	auto,rw	0	1	

I do not understand why prior to the upgrade these drives were hdb1 and sda1, yet after the upgrade the PC now calls them sdb1 and sdc1??

also, I ran
> fsck -f /dev/sdb1
and
> fsck -f /dev/sdc1

this seems to have done the trick. Both drives are behaving normally now.

---

### Post by coyotito on 2008-04-24
Good!
Does look like a better fstab line.

The change is because of the new kernel setup, all is treated as scsi it seems.

the newest kernels dont seem to like my ide disks now

---

### Post by niko7865 on 2008-04-25
I had this problem too, really scared me =P

Anyway, fix it by:

```
sudo fdisk -l
```

Which will show all your hard drives. From that, figure out which ones are not being mounted, then change their entries in /etc/fstab from /dev/hda1 to /dev/sda1 [Example, may be different for you] then reboot! or do

```
sudo mount -a
```

---

### Post by kordite on 2008-05-08
I have just suffered the same error but the suggested solution failed to resolve the issue.

sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot   Start      End      Blocks   Id   System
/dev/hda1   *        1     1912    15358108+  83   Linux
/dev/hda2         9539     9726     1510110    5   Extended
/dev/hda3         1913     9538    61255845   83   Linux
/dev/hda5         9539     9726     1510078+  83   Linux swap / Solaris

hda1 is the boot drive with the OS
hda3 is where my home directory is

My etc/fstab looked like this:

unionfs / unionfs rw 0 0 
tempfs /tmp tmpfs nosuid,nodev 0 0 
/dev/hda5 swap swap defaults 0 0 

so, as per the above suggestion, I changed the hda5 to an sda5 and rebooted to the same result. Booting from the CD showed that fstab file was the same that it had been. Did I just not save it? I made sure it wasn't read only, reopened the file after closing it and made sure that the change had been made and rebooted again to the same result. 

I'm sure I'm missing something.

---

### Post by Black_Monkey on 2008-05-31
Would this also affect CD drives? My fstab file is saying that my cd drive is at /dev/hda, but this does not exist. Should I edit the file, and if so, to what?

---

### Post by kordite on 2008-05-31
I believe it could. I didn't notice after the upgrade but as part of my attempt to repair I just wiped out everything and Installed v8 clean. It would not recognize my CD-RW drive at all and couldn't get Wine to install from the other CD drive. I don't know if that was Wine's issue or something with the drive as well. Ultimately I just wiped it all again and re-installed v7. Everything's been fine after that.

---

