---
title: "Camera (USB) mounts but is not in /media--can't copy large videos"
date: 2015-03-28
forum: General Help
---

### Post by Ralph L on 2015-03-28
I am running ubuntu 12.04 on a Dell Latitude D610 with 2G of memory.  I just got a new Canon sx280hs camera and took some still images and some rather long videos (2G and 5G).  When I plug the camera into the computer, it appears on the left pane of the nautilus window and I can open it, see the various still image and video files, and using nautilus drag and drop, copy most of them to my hard disk.  However, some of the big files won't copy.  According to the "df -h" command I have 53GB of unused space in the partition to which I am trying to copy the file, although I have only 873MB of free space on my operation system partition.  When I try to nautilus drag and drop the 2GB file, it brings up the nautilus copy window and appears to be trying to copy the file.  The light on the camera blinks indicating that activity is taking place.  However, the progress bar remains at 0.  If I bring up System Monitor and view the graph of memory usage, it will start with about 600 MB of real memory in use and about 170MB of swap.  As the copy proceeds nearly all of the 2GB of real memory will fill up and then swap memory begins to fill.  After a while a window will pop up with the error message "Error getting file: -1: Unspecified error".

Thinking that the nautilus copy routine might have limitations, I decided to try "cp" from Terminal.  However, when I display the contents of /media, the camera does not appear.  Yet it appears very plainly in nautilus as "Canon Digital Camera", and, as I said before, I can copy most files from it to the hard disk using nautilus drag and drop.  Moreover, on my Window Vista system, the files copies to the hard disk in about 2 minutes and I can play the video.

I have several questions:
1..What could be causing nautilus to have problems copying this 2GB files?
2.  Why is nautilus completely filling my real memory and overflowing into my swap memory?  Does nautilus need to get an entire file into memory in order to copy it?
3.  How is it possible that a USB device is not mounted in /media, but is still appearing in nautilus all mounted and functioning?  Are USB devices now being mounted somewhere else?
4.  How can I use "cp" under to Terminal to copy a file that doesn't appear in a directory?

Any help appreciated..........

---

### Post by oldos2er on 2015-03-28
With the camera plugged in, use the *mount* command to find its mount point.

---

### Post by Ralph L on 2015-03-28
Thank you very much for responding

Here's the output of mount.  I don't see anything there that looks like Canon Digital Camera.
```
ralph@Lat1:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda10 on /media/Shared_Data type ext3 (rw,acl,user_xattr)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ralph/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ralph)
ralph@Lat1:~$ 
```

---

### Post by oldos2er on 2015-03-29
I don't either. I thought Ubuntu mounted devices in /mnt rather than /media, but I don't see that either.

---

### Post by Ralph L on 2015-03-29
Anybody else have any thoughts on how the Canon Camera is being accessed using USB through Nautilus, but with no entry in /media or /mnt.  There must be an entire other USB protocol in ubuntu that I don't know about.  I could really use some help on this, so I can get my new camera to work with ubuntu.  Otherwise I will have to drop back to Windows to be able to download video files from it.  I don't want to do that.

Thanks for any help you can give!

---

### Post by Bashing-om on 2015-03-29
Ralph L; Hello;

Mind you, I do not know, but maybe a hint to look in the right direction:
see:
```

man gvfs-mount

```
and to look deeper:
```

sudo apt-get install gvfs-bin
gvfs-mount --monitor --detail

```
I expect will tell a whole bunch about what is going on.

[INDENT][INDENT]all in knowing how to ask the system
[/INDENT][/INDENT]

---

### Post by gordintoronto on 2015-03-30
To clear some space in your root partition, use this command: sudo apt-get clean

I doubt if that will help with copying from the camera, but it will prevent other major problems down the road.

---

### Post by Ralph L on 2015-03-31
gordintoronto
Thanks for the tip.  I tried sudo apt-get clean but it exited (no error message) immediately.  Does this mean my system is already clean, or do I need to specify a parameter, or something else.

Thanks again

---

### Post by Ralph L on 2015-03-31
Bashing-Om
Thanks for responding.  Your suggestion was very helpful.  Here are the results from running gvfs-mount --monitor --detail and then plugging in the camera:
```
ralph@Lat1:~$ gvfs-mount --monitor --detail
Monitoring events. Press Ctrl+C to quit.
Volume added:       'Canon Digital Camera'
  Volume(0): Canon Digital Camera
    Type: GProxyVolume (GProxyVolumeMonitorGPhoto2)
    ids:
     unix-device: '/dev/bus/usb/001/005'
    activation_root=gphoto2://[usb:001,005]/
    themed icons:  [camera-photo]
    can_mount=1
    can_eject=0
    should_automount=1

Mount added: 'Canon Digital Camera'
  Mount(0): Canon Digital Camera -> gphoto2://[usb:001,005]/
    Type: GDaemonMount
    default_location=gphoto2://[usb:001,005]/
    themed icons:  [camera-photo]  [camera]
    x_content_types: x-content/image-dcf
    can_unmount=1
    can_eject=0
    is_shadowed=0

Mount changed: 'Canon Digital Camera'
  Mount(0): Canon Digital Camera -> gphoto2://[usb:001,005]/
    Type: GDaemonMount
    default_location=gphoto2://[usb:001,005]/
    themed icons:  [camera-photo]  [camera]
    x_content_types: x-content/image-dcf
    can_unmount=1
    can_eject=0
    is_shadowed=1

```  From this I was able to find the camera mount point (~/.gvfs/gphoto2 mount on usb%3A001,005).  Using this mount point I accessed the camera from Terminal and attempted to use "cp" to copy the 4G video file to my hard disk.  However, it had the same problem as the nautilus copy.  Using System Monitor (graphical display) to monitor it, it gradually filled all real memory and then started filling swap space.  Finally it aborted without copying any of the file.  I noticed the camera activity light continued to blink after the abort, so I am guessing that the camera continued to transmit the file even after the abort.  My current theory is that "cp" is filling the buffer, but for some strange reason is not moving the data to the hard disk, and the camera just continues pouring it into the computer.  Do you know of any parameter for cp that will force it to empty its copy buffer to disk before an end-of-file, as doing this would seem to be a fix for the problem?  Or do you know of any other copy routines for linux that would do this, or can you think of something else that might fix the problem?  
One idea I have is that I should do a purge of gvfs (or disable it some other way), and maybe cp would behave better.  I see that gvfs is a standard part of ubuntu (it was already on my system so I didn't have to install it), so I am concerned that if I purge it, I will damage my system.  Do you think I could remove it (or disable it temporarily)??

Again, thanks for your help!!

---

### Post by Bashing-om on 2015-03-31
Ralph L; Well,

Keep in mind it is always an affront to me dignity when I encounter situations "I do not know"; this is one of those .
However, what pops to mind is to check the file system in use on the camera . IF it is fat32 - there is a 4 Gig limit .
[http://support.microsoft.com/kb/314463](http://support.microsoft.com/kb/314463)

Else, one can use the tool 'rsync' to sync copying files:
```

man rsync

```

[INDENT][INDENT]I rest assured
[INDENT][INDENT][INDENT]there is a way to skin this cat
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Holger_Gehrke on 2015-03-31
You camera is using PTP (Picture Transfer Protocol) or the newer MTP (Media Transfer Protocol). GVFS (Gnome Virtual File System) is just an abstraction layer for making things that actually are not file system behave as if they were. libgphoto2 - which gvfs is using to access your camera - was never really meant to handle videos (as the name g**photo** implies ...). There is a command line interface for libgphoto2 named gphoto2, but I don't think it gets installed by default. It might be capable of transferring these large files, but I'm not sure. The easiest way is probably to use a card reader - assuming your camera stores the data on a card.

---

### Post by Bashing-om on 2015-03-31
> **Holger_Gehrke said:**
> You camera is using PTP (Picture Transfer Protocol) or the newer MTP (Media Transfer Protocol). GVFS (Gnome Virtual File System) is just an abstraction layer for making things that actually are not file system behave as if they were. libgphoto2 - which gvfs is using to access your camera - was never really meant to handle videos (as the name g**photo** implies ...). There is a command line interface for libgphoto2 named gphoto2, but I don't think it gets installed by default. It might be capable of transferring these large files, but I'm not sure. The easiest way is probably to use a card reader - assuming your camera stores the data on a card.

Now that ^^ is enlightening, Why I frequent this forum; a never ending learning process.

[INDENT][INDENT][INDENT]thanks 
[/INDENT][/INDENT][/INDENT]

---

### Post by Ralph L on 2015-04-01
I can't find a way to tell if the file system is FAT32.  However, I did find that there have been considerable problems with transferring large files using gvfs.  See  [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1075923](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1075923) Post 202.  It says the problem is still there.  I added a comment about my problem.

---

### Post by Bashing-om on 2015-04-01
Ralph L; Sheesshh ...

The bug report is interesting, and does address a few questions of my own.
However, this is well beyond my skill level. I do not know what I can add .

[INDENT][INDENT]surmounting
[INDENT][INDENT][INDENT]that wall of ignorance
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-04-02
Ralph L; Hey, hey ;

There were a number of updates today for the gvfs files. Any change for the good now after the updates ?

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by Ralph L on 2015-04-02
Bashing Om
I updated my computer today, but I didn't see anything on gvfs.  Where did you see that?  Anyway after the update I tried again to read a large file and again it filled real memory, started filling swap space, and then aborted with "Error getting file: -1: Unspecified error".  Same as before.

---

### Post by Bashing-om on 2015-04-02
Ralph L; Hey;


I am on release 14.04.2 and here is my log file of the update.

```

2015-04-02 12:56:32 upgrade gvfs:amd64 1.20.1-1ubuntu1 1.20.3-0ubuntu1
2015-04-02 12:56:32 status half-configured gvfs:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:32 status unpacked gvfs:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:32 status half-installed gvfs:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:32 status triggers-pending libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-04-02 12:56:32 status half-installed gvfs:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:32 status half-installed gvfs:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:33 status unpacked gvfs:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:33 status unpacked gvfs:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:33 upgrade gvfs-daemons:amd64 1.20.1-1ubuntu1 1.20.3-0ubuntu1
2015-04-02 12:56:33 status half-configured gvfs-daemons:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:33 status unpacked gvfs-daemons:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:33 status half-installed gvfs-daemons:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:33 status half-installed gvfs-daemons:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:33 status unpacked gvfs-daemons:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:33 status unpacked gvfs-daemons:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:33 upgrade gvfs-libs:amd64 1.20.1-1ubuntu1 1.20.3-0ubuntu1
2015-04-02 12:56:33 status half-configured gvfs-libs:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:33 status unpacked gvfs-libs:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:33 status half-installed gvfs-libs:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:33 status half-installed gvfs-libs:amd64 1.20.1-1ubuntu1
2015-04-02 12:56:34 status unpacked gvfs-libs:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:34 status unpacked gvfs-libs:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:34 upgrade gvfs-common:all 1.20.1-1ubuntu1 1.20.3-0ubuntu1
2015-04-02 12:56:34 status half-configured gvfs-common:all 1.20.1-1ubuntu1
2015-04-02 12:56:34 status unpacked gvfs-common:all 1.20.1-1ubuntu1
2015-04-02 12:56:34 status half-installed gvfs-common:all 1.20.1-1ubuntu1
2015-04-02 12:56:34 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-04-02 12:56:34 status half-installed gvfs-common:all 1.20.1-1ubuntu1
2015-04-02 12:56:34 status unpacked gvfs-common:all 1.20.3-0ubuntu1
2015-04-02 12:56:34 status unpacked gvfs-common:all 1.20.3-0ubuntu1
<snip>
2015-04-02 12:56:36 configure gvfs-common:all 1.20.3-0ubuntu1 <none>
2015-04-02 12:56:36 status unpacked gvfs-common:all 1.20.3-0ubuntu1
2015-04-02 12:56:36 status half-configured gvfs-common:all 1.20.3-0ubuntu1
2015-04-02 12:56:36 status installed gvfs-common:all 1.20.3-0ubuntu1
2015-04-02 12:56:36 configure gvfs-libs:amd64 1.20.3-0ubuntu1 <none>
2015-04-02 12:56:36 status unpacked gvfs-libs:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:36 status half-configured gvfs-libs:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:36 status installed gvfs-libs:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:36 configure gvfs-daemons:amd64 1.20.3-0ubuntu1 <none>
2015-04-02 12:56:36 status unpacked gvfs-daemons:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:36 status half-configured gvfs-daemons:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:37 status installed gvfs-daemons:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:37 configure gvfs:amd64 1.20.3-0ubuntu1 <none>
2015-04-02 12:56:37 status unpacked gvfs:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:37 status half-configured gvfs:amd64 1.20.3-0ubuntu1
2015-04-02 12:56:37 status installed gvfs:amd64 1.20.3-0ubuntu1

```

[INDENT][INDENT]maybe , just a maybe
[/INDENT][/INDENT]

---

### Post by Ralph L on 2015-04-04
Bashing OM
You are correct; installing the latest update on 14.04 fixed the problem!!!  I have just started experimenting with 14.04 and had it installed in a separate partition on my wife's computer.  I installed the latest update there and was able to download a 4GB file directly from the camera.  I had not been able to do that on 14.04 before I installed the latest update.
But its a bit of a good new, bad news thing.  With the latest update installed, now my wife's computer blinks every few seconds and is really unusable.  Now I have to run down that problem.  Did you happen to have a blinking problem, when you installed the latest update?  I will post a new question about that on the forum.
As an aside:  For some reason the mount point for my camera no longer shows up in /~.gvfs.  I don't know where it has gone to, but I guess it doesn't matter now.
Thanks again for all your help!!

---

### Post by Bashing-om on 2015-04-04
Ralph L; Great !

Pleased to no end that the bug is now under control. 
No thanks to me, all I did was hold your hand ... all thanks to our developers and those who maintain our code.
If you would, add your advisement to update that bug report for all to know .

And no, my system is solid after the updates .. running on an old dual core AMD Athlon chip set.

I too am interested in knowing where that mount point has been moved too. I do not have a camera that I can attach to test and see.

[INDENT][INDENT]good things do happen[/INDENT][/INDENT]

---

### Post by Ralph L on 2015-04-05
Bashing Om
I found the mount point for my camera on the latest (as of 4/3/2015) update version of ubuntu 14.04 in /run/user/1000/gvfs.  However, I can't find it for ubuntu 12.04, even though the camera is plainly mounted and I can see the files on it through nautilus.  Maybe I'll stumble upon it sometime.  Just thought you might be interested.

---

### Post by Bashing-om on 2015-04-05
Ralph L:
Yeah, always a process of learning.
what returns:
```

cat /proc/mounts

```
As I expect the virtual file system to keep track of all mounts. But I could be in error .

[INDENT][INDENT]'bout the time I think I know
[INDENT][INDENT][INDENT]I find I do not know enough
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Ralph L on 2015-04-08
Bashing Om
Here is the output of cat /proc/mounts:
```
rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=1019296k,nr_inodes=215805,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=205320k,mode=755 0 0
/dev/disk/by-uuid/84c781de-f7dd-4b72-9ba3-cb962240315f / ext4 rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
/dev/sda10 /media/Shared_Data ext3 rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/ralph/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=0,group_id=0 0 0
ralph@Lat1:~$ 

```
Now this time I found the camera mount point in ~/.gvfs again.  I am puzzled.  I don't why I didn't find it before.
Thanks for all your help.

---

### Post by Bashing-om on 2015-04-08
Ralph L; Welp;

All I can say is it is a complex system; There is still more I do not know about how the system mounts various components than what I do know.
The good news is that my faith in the report of " /proc/mounts/ " is restored. There is a means for sure to at least find out and learn.

[INDENT][INDENT]the more one knows
[INDENT][INDENT][INDENT][INDENT]the more one wants to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

