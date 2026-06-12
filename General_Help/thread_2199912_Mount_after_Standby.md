---
title: "Mount after Standby"
date: 2014-01-16
forum: General Help
---

### Post by chris137 on 2014-01-16
Hi,
I got my external Drives in my fstab:
```
chris@knix:~$ cat /etc/fstab

UUID=01CE1B8B1A1B1670        /media/Serien        auto 
UUID=22A42D06A42CDDD3        /media/Serien2         auto
```
So after every reboot it's exactly how I want it.
Usually I don't shut my PC down but suspend it. I also cut the power of those external drives (don't know if that's the problem or not).
So after I wake the PC up the drives are still mounted but the content does not appear.
This is what I get after waking it up:
```
chris@knix:~$ mount

/dev/sdh1 on /media/Serien type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdg1 on /media/Serien2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```
The drives appear in nautilus in Computer but are empty when opened.
They also appear in Devices (unmounted) and when opening I get this:
> Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdg1 is already mounted on /media/Serien2
mount failed
Yeah, makes sense to me because it actually is still mounted as we see above.
mtab looks like this if it helps:
```
chris@knix:~$ cat /etc/mtab

/dev/sdh1 /media/Serien fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdg1 /media/Serien2 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
```

To solve this I manually umount and mount them again which also only works with -l because they are always busy (whatever they are doing..)
```
chris@knix:~$ sudo umount -l /dev/sdh1
chris@knix:~$ sudo umount -l /dev/sdg1
chris@knix:~$ sudo mount -a
```
Everything as expected after that.

So what do I have to do to avoid this?
Last thing I want to do is start a script every time I wake my PC up.
There should be an easy solution for that, right?

Edit: 
So I just simply suspended the PC but did not cut the power of the drives.
After waking it up they still were there.
I guess problem might be the following:
The get mounted everytime on an other location.
For example they are now mounted at sdk1 and sdl1 while they were mounted at sdh1 and sdg1 when I posted this.
I did already do something to make sure they always get mounted at the same spot but this obviously does not work.
I will ask the person who helped me with that if no one knows the solution.

---

### Post by chris137 on 2014-01-16
As always..
Acutally writing down my problems, all factors in one post helps me to simply find the right key words for google.
This post helped me.
[http://ubuntuforums.org/showthread.php?t=2058123&p=12240979#post12240979](http://ubuntuforums.org/showthread.php?t=2058123&p=12240979#post12240979)
Simply put "nofail" in your fstab and ubuntu won't care if there is actually a drive attached or not.

Sorry for the thread, I hope it helps someone with the same issue.

---

