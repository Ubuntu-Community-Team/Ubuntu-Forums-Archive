---
title: "How do I mount Ipod by label?"
date: 2021-05-21
forum: General Help
---

### Post by Colin@oxford on 2021-05-21
I have an ipod that I need to mount RW.  If I run blkid, this is what it says:

/dev/sdf2: LABEL="James GoldbergM-bM-^@M-^Ys iPod" TYPE="hfsplus" PARTLABEL="disk"

If I put this in fstab:

/dev/sdf2	/media/ipod	hfsplus	rw,user,force,noauto	0	0

Then it mounts fine and mtab has:

/dev/sdf2 /media/ipod hfsplus rw,nosuid,nodev,noexec,relatime,umask=2,uid=1000,gid=1000,nls=utf8 0 0

In File manager, the label of the ipod is shown correctly as "James GoldBerg's iPod

(I am not sure how to see than on the command line)

This is fine, but causes problems if I want to put in another USB device which has two partitions.  The second partition is also at /dev/sdf2 and so cannot mount because it is (say) ext3 not the hfsplus.

The solution would appear to be to put LABEL=<label> in fstab rather than /dev/sdf2.  However, this does not work, possibly due to that apostrophe.  It mounts, but RO, which is no good.

Any suggestions on how I can make mount see the label correctly?

---

### Post by TheFu on 2021-05-22
```
LABEL="James GoldBerg's iPod"
``` doesn't work?

If it were me, I'd change the label to not have spaces or other funny characters.

Or

you could use the UUID.

Every reboot means the device can change, so it is risky to leave /dev/sd{anything} in the fstab.
The available links that can be used are generated under /dev/disk/by-* when it is connected.  You can look below that directory for which symbolic links point at the current device (/dev/sdf1).

I don't have any iPod, but I do have a 64G USB3 flash storage device.  Let me plug it in and watch the device it gets:
```
$ dmesg -w
....
[637258.200962]  sdc: sdc1 sdc2 sdc3
[637258.202569] sd 16:0:0:0: [sdc] Attached SCSI removable disk
```
Ok, it has sdc1 sdc2 sdc3 devices.  Now, let's go fishing for the symbolic links that have been generated .... 

```
$ ls -l  /dev/disk/by-label/
total 0
lrwxrwxrwx 1 root root 10 May 22 01:35 backups -> ../../dm-0
lrwxrwxrwx 1 root root 10 May 22 19:47 ESP -> ../../sdc2
lrwxrwxrwx 1 root root 10 May 22 19:47 Ubuntu-Server\x2021.04\x20amd64 -> ../../sdc1
```
Ok, so the ESP ---> sdc2 
and 
Ubuntu-Server\x2021.04\x20amd64 ----> sdc1

To mount the Ubuntu-Server ... stuff, I'd put
```
LABEL=Ubuntu-Server\x2021.04\x20amd64 .....
```
into the fstab. Well, crap. That didn't work. Let's try quoting it.
```
LABEL=[COLOR="#FF0000"]"[/COLOR]Ubuntu-Server\x2021.04\x20amd64[COLOR="#FF0000"]"[/COLOR] .....
```
Double-crap. Not working.

Let's step back and try the ESP partition.
```
LABEL=ESP /mnt/1  auto   defaults   0 0 
```
Ok, that's working fine. Here's proof:
```
$ df -Th |grep mnt
/dev/sdc2                         vfat      4.9M  4.0M  988K  81% /mnt/1
```
and more proof:
```
$ mount |grep mnt
/dev/sdc2 on /mnt/1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

```
So, what have we learned?
**DON'T USE FUNKY CHARACTERS in Labels.**

What about using the UUID instead?
```
$ ls -l /dev/disk/[COLOR="#FF0000"]by-uuid[/COLOR]/
total 0
lrwxrwxrwx 1 root root 10 May 22 19:47 [COLOR="#00FF00"]2021-04-22-01-48-39-00[/COLOR] -> ../../sdc1
lrwxrwxrwx 1 root root 10 May 15 10:47 2471d686-fde5-4680-a75a-46c99c8a5550 -> ../../sdb1
lrwxrwxrwx 1 root root 10 May 22 19:47 F940-6C0E -> ../../sdc2

```
I removed some output to prevent confusion. Remember, we want sdc1 ... which has a uuid of "2021-04-22-01-48-39-00".
Here's the line I put into the fstab and the mount:
```
UUID=2021-04-22-01-48-39-00 /mnt/1  auto   defaults   0 0

$ sudo mount -a
mount: /mnt/1: WARNING: device write-protected, mounted read-only.
 
```
That's expected. It is a 21.04 Server ISO Flash drive. ISOs are read-only. See:
```
$ mount |grep mnt
/dev/sdc1 on /mnt/1 type iso9660 (ro,relatime,nojoliet,check=s,map=n,blocksize=2048)
```
Next is to umount the storage, then remove it, re-insert it and mount it again without touching the fstab.
Ok - that worked.
```
$ df -Th ....
/dev/sdc1                         iso9660  1.1G  1.1G     0 100% /mnt/1
```
Working as expected.  Does the HPFS driver support read-write operations?  IDK.

A handy command:
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
sdc                              57.7G disk iso9660     
&#9500;&#9472;sdc1                            1.1G part iso9660    [COLOR="#00FF00"] /mnt/1[/COLOR]
&#9500;&#9472;sdc2                            4.9M part vfat        
&#9492;&#9472;sdc3                            300K part iso9660     
```

Hope this has been helpful. There are other ways to get the information, but I prefer using the stuff closest to the OS for that.  We could have used blkid, for example.
```
/dev/sdc1: UUID="2021-04-22-01-48-39-00" LABEL="Ubuntu-Server 21.04 amd64" TYPE="iso9660" PARTLABEL="ISO9660" PARTUUID="512003f3-bf39-480c-aa7c-06b24049668b"
```

Huh.  Let's try that label.  Nope. I copied/pasted and still got:
```
$ sudo mount -a
mount: /etc/fstab: parse error at line 19 -- ignored

```
Line 19 is the line with the sdc1 mount (using LABEL="Ubuntu-Server 21.04 amd64").
Sometimes, funky characters screw things up.

BTW, I expected all of these methods to work, so it wouldn't hurt to do the same yourself.

---

### Post by Colin@oxford on 2021-06-13
Thanks for your extensive reply.  Sorry not to have responded earlier - I was not notified of a response :(

My problem is that the iPod is not mine and I would not know how to change the label if it were.

iPods (at least this one) do not have a UUID - or at least not one that blkid will display, just a PARTLABEL

Actually, I have managed to get the correct letters in the mtab, so I can mount it using "mount", but the system automatically mounts it elsewhere, so I have to manually unmount it before e-mounting.  Strange.

---

