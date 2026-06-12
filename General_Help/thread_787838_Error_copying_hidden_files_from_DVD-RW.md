---
title: "Error copying hidden files from DVD-RW"
date: 2008-05-09
forum: General Help
---

### Post by c-cube on 2008-05-09
Hi there,

I encounter the same issue as the one stated in this topic :

[http://ubuntuforums.org/showthread.php?t=444659](http://ubuntuforums.org/showthread.php?t=444659)

However as it wasn't solved and it is almost one year old, I thought it would be better to open a new one. Hope this was the right thing to do.

My problem is almost the same, but slightly different. I backuped my /home folder on a DVD-RW before I erase my previous Ubuntu (Gutsy) in order to install the new one (Hardy).
I can now copy anything from this DVD but the hidden files (the ones whose name begins with a dot).
When I try to copy any hidden file from this DVD, it fails and an I/O error message is being displayed.

This is all the more annoying as I've got a very important hidden file stored on this DVD : **.mozilla-thunderbird** which, of course, holds all my e-mails and contacts...

Here is what I tried so far, without any success, to solve the problem :

- Mounting my DVD drive with every possible options of the mount command.

- Changing UDMA settings of my DVD drive into the BIOS

- Openning the DVD on another PC with Gutsy Gibbon and an older kernel.

- Openning the DVD under Windows XP (yes I am that desperate...)

I think the problem as to do with the way the DVD was burnt. However, it seems quite strange to me that I can copy any "normal" file from this DVD, see the hidden files (whose size is correct by the way) but not copy them. The DVD isn't scratched.

Any idea about this hidden files issue ?

---

### Post by hermes0710 on 2008-05-09
How is the dvd mounted? (mtab entry?)

---

### Post by kpkeerthi on 2008-05-09
Suggestion. Create an ISO off the DVD (using K3B/Brasero/Gnomebaker/dd). [Mount the ISO]("http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html") and see if you can grab the contents off it. 

I recommend K3B for this purpose.

---

### Post by c-cube on 2008-05-09
Thanks to both of you for trying to help me.

**hermes0710**, I couldn't identify any line related to my DVD drive in the mtab file. Here is the whole content of this file :

```
/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sda11 /boot ext3 rw,relatime 0 0
/dev/sda7 /home ext3 rw,relatime 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sda8 /media/sda8 ext3 rw,relatime 0 0
/dev/sda10 /media/sda10 ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/cedric/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=c-cube 0 0
```

And here is the fstab line related to my DVD drive :

```
/dev/scd0       /media/cdrom0   udf,iso9660    user,noauto,exec,utf8    0       0
```


**kpkeerthi**, I'm going to try your solution and I'll keep you informed about the result.

---

### Post by songshu on 2008-05-09
just a few options you could try

this works with hidden .files for sure

mount -o loop /path/to/iso /some/mountpoint
rsync -av /some/mountpoint /opt/cd-image

---

### Post by c-cube on 2008-05-09
Ok, so I just tried **kpkeerthi** solution first. Unfortunately, it didn't work. I still have the same I/O error when trying to copy hidden files from the mounted ISO to any other folder.

Then, **songshu**, I tried yours and it didn't work either. For every hidden file the rsync command returned the following message :

```
ERROR: imageDVD/.hidden-file failed verification -- update discarded.

```

Then at the end of the whole process, it returned this message :

```
sent 4897275653 bytes  received 179948 bytes  16083598.03 bytes/sec
total size is 4239830277  speedup is 0.87
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

```

Too bad ! :(

---

### Post by songshu on 2008-05-09
oke,

i never tried it on a dvd, but as you are completely out of options and desperate anyway ;) you might want to try testdisk....not sure if it works on a dvd but definitely something i would try if all else failed to recover lost files.

---

### Post by c-cube on 2008-05-10
Thank you songshu. I tried testdisk (photorec) but it couldn't do the job. It doesn't handles mozilla-thundebird archives.
Yet it seems to be a very good tool for retrieving many other types of data.

I investigated a little further on my issue and discovered that not all the hidden files stored on the DVD are affected. I can copy some of them (but not the ones I need...). So I guess something went wrong with the burning process and I can consider that my Thunderbird datas are definitely lost.

Next time I will verify my DVD with more accuracy... or wont use a DVD to store such important datas.

Thank you very much to all of you who tried to help me.

---

