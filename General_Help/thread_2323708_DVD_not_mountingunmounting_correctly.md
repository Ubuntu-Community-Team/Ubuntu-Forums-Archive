---
title: "DVD not mounting/unmounting correctly"
date: 2016-05-07
forum: General Help
---

### Post by gleedadswell on 2016-05-07
Hello,
This is similar to some other problems reported but the details of the symptoms are different and other posts I've looked at haven't resolved the problem for me.  I can get a DVD to play (including commercial DVDs with restricted codecs) but the steps necessary to do this are not quite right.  I suspect I've messed up the fstab.

I have a fresh Ubuntu 16.04 install.  Here are some stats:

```

uname -a
Linux oldHP 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:53:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

```

lshw | less
...
     *-cpu
          product: AMD E-350 Processor
...
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT31L
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: MR52


```

I installed the various dvd playing packages and codecs.  But when inserting a DVD it simply wouldn't be detected.  Trying to manually mount the dvd resulted in the typical "can't find ### in fstab" error message.  So, I created a mount point in /media and then added the following line to fstab:

```

## DVD
/dev/sr0    /media/carol/cdrom0    udf,iso9660    ro,user,noauto    0    0

```

Now when I insert a DVD the following happens:

1. The DVD spins up, an icon appears on the launcher bar, but instead of the correct CD/DVD symbol it is the symbol that stands for a hard drive (similarly if nautilus is open it appears in the list of devices as a hard drive).
2. Right clicking the hard drive icon and selecting "open" makes the drive spin up, the icon turns into the correct CD/DVD icon and it opens in nautilus.
3. Nautilus has a "Videos" button in the top right corner (is that new - I've never noticed it before).  Clicking that makes the DVD play correctly.
4. When ejecting the DVD (either right clicking the icon on the launcher bar or via nautilus) it requires authorization saying:

"Authentication is required to unmount hp  DVDRAM GT31L (/dev/sr0) mounted by another user"

So, I can play DVDs, but it isn't working the way it is supposed to.  Any help would be much appreciated.

---

### Post by kansasnoob on 2016-05-07
You're not alone:

[http://ubuntuforums.org/showthread.php?t=2323204](http://ubuntuforums.org/showthread.php?t=2323204)

[http://ubuntuforums.org/showthread.php?t=2323524](http://ubuntuforums.org/showthread.php?t=2323524)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768)

It should not be necessary to edit fstab for optical discs to be recognized :(

---

### Post by mc4man on 2016-05-07
To get some info - 
with your current setup insert a dvd, let it settle but don't open or do anything else. Run these & post, for mtab only post last 2 lines, for lshw just the _complete_ *-cdrom section
```

cat /etc/mtab
```
```
sudo lshw -c disk
```

Then do whatever to cause it to show up correctly, run the 2 commands again & post if different from above results

---

### Post by gleedadswell on 2016-05-08
> **kansasnoob said:**
> You're not alone:

[http://ubuntuforums.org/showthread.php?t=2323204](http://ubuntuforums.org/showthread.php?t=2323204)

[http://ubuntuforums.org/showthread.php?t=2323524](http://ubuntuforums.org/showthread.php?t=2323524)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768)

It should not be necessary to edit fstab for optical discs to be recognized :(

Agreed.  In most recent Ubuntu installs I've done the DVDs have just worked, with no messing around.  Don't know what was different this time.  

mc4man, I'll post the diagnostics you're asking for soon, but I'm not near that computer now so I can't do it at the moment.

---

### Post by Carol_Lee on 2016-05-08
This is the original poster, though it doesn't look like it.  I'm setting this computer up for someone else and this is her Ubuntu Forums account.

Here is the requested info.  After inserting the DVD and doing nothing else I get...

last three lines of mtab (the third from last looks possibly relevant):
```

fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=363828k,mode=700,uid=1000,gid=1000 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0

```

cdrom portion of output from lshw -c disk:
```

  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GT31L
       vendor: hp
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: MR52
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```

...after right clicking and opening in nautilus, causing it to show DVD icon correctly...

last line of mtab (only the last line seems to be new):
```

/dev/sr0 /media/carol/cdrom0 udf ro,nosuid,nodev,noexec,relatime,utf8 0 0

```

cdrom portion of output from lshw -c disk:
```

  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GT31L
       vendor: hp
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       logical name: /media/carol/cdrom0
       version: MR52
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,noexec,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/carol/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,noexec,relatime,utf8 state=mounted

```

Comment: it looks like in 16.04 each user's mount points for disks is within their own directory inside /media (this is new, right?).  So when I set up the mount point in fstab I made it /media/carol/cdrom0.  But I'm wondering if I should have just made it /media/cdrom?  I'll try that and see if it changes anything.

Later edit: No, changing fstab so it tries to mount at /media/cdrom makes it worse (can't get it to recognize it as a DVD at all).  I've put it back to the way I had it.

Further comment.  Before my original post, in trying to diagnose the problem I had done some manual mounting of the DVD as sudo.  I'm wondering if that has caused to get something to get "stuck" with the DVD as a resource owned by root.

---

