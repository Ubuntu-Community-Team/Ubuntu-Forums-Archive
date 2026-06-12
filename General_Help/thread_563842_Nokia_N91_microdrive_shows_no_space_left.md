---
title: "Nokia N91 microdrive shows no space left"
date: 2007-09-30
forum: General Help
---

### Post by karhulitos on 2007-09-30
Hi,

I've been trying search answer but no luck so far.

I have a strange problem with my phone's 4GB disk and Ubuntu (7.04); Ubuntu says no space left to copy songs onto it, although I should have enough space left, around 1,6GB.

Now the history is that I've copied songs until the phone was indeed full after which I deleted some. Ubuntu created the .Trash-user folder and it was empty as I've emptied the trash can.

Phone itself reports 1,6GB left like Windows does but Ubuntu says to me 5,4MB free. Disk file system is vfat/FAT32.

I am about to reformat the drive but before I do that is there something obvious I'm missing?

---

### Post by SeanTater on 2007-09-30
The output of the following commands may help

```
df -h
mount
```I also know that on occasion ext ans similar FS's will reserve space for only root to use. This seems like anomalously large abount of extra space, just just to check, either copy a file to it using root privIledges or:

```
sudo dd if=/dev/zero bs=1048576 count=100 of=/THEPATHTOTHEDRIVE/testfile
```Then if it's there, do
```
rm /THEPATHTOTHEDRIVE/testfile 
```

---

### Post by karhulitos on 2007-09-30
Hi,

thanks for helping me out!

```

$ df -h
file sys            size  Used Free Use% Mountpoint
/dev/sdb              3,8G  3,8G  5,5M 100% /media/N91

```
I deleted more music from the disk but still Ubuntu wants to keep that free space away from me!

mount:
```

$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb on /media/N91 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

```

sudo dd if=/dev/zero bs=1048576 count=100 of=/THEPATHTOTHEDRIVE/testfile
```

1$ sudo dd if=/dev/zero bs=1048576 count=100 of=/media/N91/testfile
Password:
dd: kirjoitetaan tiedostoa "/media/N91/testfile": No space left on device
6+0 tietuetta sisään
5+0 tietuetta ulos
5668864 tavua (5,7 MB) kopioitu, 1,10853 sekuntia, 5,1 MB/s

```
(sorry output is partly finnish but I guess the hightlight is in english. No space, Jose)

Odd..

---

### Post by karhulitos on 2007-10-01
Hmm..

got some progress myself. I decided to go on the path of reformatting the microdrive. Before I started I deleted all songs from the phone's disk using Ubuntu. All of a sudden Ubuntu said I have 1,4GB of free space. Great. Now I only have about 2,4GB missing.

Thinking of that 1,4GB it correlates pretty closely to the amount I've ever copied files to the phone from Ubuntu, So the 2,4GB part I might have tried to delete using the phone's tools or Windows. Or I have copied 2,4GB using Windows, can't be sure anymore. Hmm..

Could this be? Using Ubuntu only (copying or removing songs) would work just fine with vfat(FAT32) but if I use both phone sw or Windows  to delete files, it would end up in no free space reported by Ubuntu? Can anyone confirm this kind of behavior?

I guess this should be pretty much same for any external drives used if they have vfat and they're used in both Windows and Ubuntu.

---

### Post by karhulitos on 2007-10-01
OK,

formatting done, here are some test output with clean disk.

1. after format
Phone says:
- 4GB free
- 400kB used
Ubuntu says:
- 3,7GB free
- 400kB used

2. copied data (1,2GB) to the disk from Ubuntu (sudo dd if=/dev/zero bs=1048576 count=200 of=/media/N91/testfile2 and sudo dd if=/dev/zero bs=1048576 count=1000 of=/media/N91/testfile)
Phone says:
- 2,7GB free
- 1,2GB used
Ubuntu says:
- 2,6GB free
- 1,2GB used

3. deleted tesfile2 (200MB) using Ubuntu, emptied Trash
Phone says:
- 2,97GB free
- 1GB used
Ubuntu says:
- 2,8GB free
- 1GB used

4. deleted testile (1GB) using phone
Phone says:
- 4GB free
- 400kB used
Ubuntu says:
[COLOR="Red"]- 2,8GB free[/COLOR]
- 400kB used

5. created a new testfile3 (200MB) in Ubuntu
Phone says:
- 3,8GB free
- 200MB used
Ubuntu says:
- 2,6GB free
- 200MB used

6. deleted tesfile3 (200MB) using Windows XP
Phone says:
- 4GB free
- 400kB used
Windows says:
- 3,7GB free
- 400kB used
Ubuntu says:
[COLOR="Red"]- 2,6GB free[/COLOR]
- 400kB used

(the phone seems to display 4GB disk size a bit differently; while Ubuntu and Windows said size is 3,7GB, phone says it's 4GB)

This test proved to me that somehow phone and Windows deletions are not detected by Ubuntu and those files still use the space and I cannot reuse those if I use Ubuntu to copy new files on vfat(FAT32) file system.

Now I format again and if I only use Ubuntu to manage phone's music library, I'm just fine, so 'workaround' exists. :)

Is this a bug or by design?

---

### Post by dinhluong on 2007-10-04
I'm having the same issue with my Seagate external hard drive.  When I used XP, the free space still showed up again in Ubuntu, but if I delete with my new Vista computer, Ubuntu doesn't seem to recognize the space.

---

### Post by karhulitos on 2007-10-05
Thanks for letting me know, now I'm sure it's something to do with vfat/Ubuntu. Would be nice to know though is this a bug or does it work as designed..

---

