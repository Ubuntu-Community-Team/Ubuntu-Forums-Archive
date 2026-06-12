---
title: "USB Flash: No GUI Recognition"
date: 2014-08-18
forum: General Help
---

### Post by Kurt_Alan on 2014-08-18
****

Not a hardware issue with drive because I have several flash drives operating normally on a second linux box. However, on my primary linux box the gui is not recognizing any drive regardless of ports used, reboot, etc. When I plug in  the drive icon does not appear even though I have it checked off to do so in desktop settings.  These drives did work previously on this same machine, so I'm assuming some kind of config corruption. ```
 lsusb 
``` outputs my Kingston drive in ```
 Bus 001 Device 003: ID 174f:1403 Syntek Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0951:1665 Kingston Technology 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lucas@lucas-Inspiron-1011:~$ lsusb
Bus 001 Device 008: ID 1b1c:1a0a Corsair Survivor Stealth Flash Drive
Bus 001 Device 003: ID 174f:1403 Syntek Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
``` and ```
 sudo fdisk -l 
``` outputs ```
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15359999     7678976    b  W95 FAT32

```

Where do I go from here?

---

### Post by oldfred on 2014-08-18
Often NTFS & FAT32 formatted drives they will not be mounted as the filesystem has corruption.
Have you tried running chkdsk from Windows on the drive?

Can you actually mount it manually? Or that may show some issues on why. Or gparted may have a red or yellow icon and show some standard type issues when icon is clicked on.

---

### Post by Kurt_Alan on 2014-08-19
****

Hi, oldfred, I know you are the boot expert. This is my first look at your post. A couple of thoughts before I follow up:

Often NTFS & FAT32 formatted drives they will not be mounted as the filesystem has corruption.
Have you tried running chkdsk from Windows on the drive? 

OP: Are you suggesting, as a general principle, that I should format all flash drives as ext4? (I am a Linux only user and do not always have Windows access). Can you give me a heads-up on how to proceed with this?

Can you actually mount it manually? Or that may show some issues on why. Or gparted may have a red or yellow icon and show some standard type issues when icon is clicked on.  

OP: Both of these items are being followed up now: I will try viewing with gparted and look for any red flags.  Second, I have not learned how to manually mount from CLI, so I will then check the forums to find out how to do that -- unless someone wants to give me the code, it would be greatly appreciated!

---

### Post by Kurt_Alan on 2014-08-19
OP:

1. gparted reads drive and all date with no yellow or red flags.
2. If lsusb is seeing drive but I have no GUI icon, does that mean that it IS mounted?
3. Would it make sense to "re-initialize" the drive by unmounting it, then remounting it and seeing if I get a GUI icon?

---

### Post by oldfred on 2014-08-19
If it is mounted try this command to see if it mounted:

mount

I still have some FAT32 or NTFS flash drives. 
But those that I know I will only use with Linux I partition using gpt and format with ext4. I do that just like I do with any hard drive and almost always use gparted.

On a vfat drive you can run repairs from Linux.
 sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck -t vfat /dev/sdb1

---

### Post by sedawk on 2014-08-19
You can also run dmesg before and after inserting the USB drive. That way you will see which device name is used for the disk (in your the basic stuff
looks okay as you can see /dev/sdb1).
You can continue either by run command line tool "mount" to list all mounted partitions, or you can manually check the content of /media or /media/<username>.
Normally usb drives are mounted there (newer Ubuntus use /media/<username>). If you insert your USB drive and wait for a few seconds there should be
a new directory like /media/<username>/fd84-sfd3 where "fd84-sfd3" depends on your stick/vendor/volume label.

---

### Post by Kurt_Alan on 2014-08-20
****

@oldfred --
@sedawk --

I am still following up with your suggestions. Meanwhile:

1. What is the difference between lsusb and mount? Via lsusb my device IS recognized. Via mount my device is NOT recognized. So if my device is not mounted, why is it showing up in lsusb?
2. Re: formatting flash drives with gparted fat32 or NTFS VERSUS ext4, are there any file types that cannot be read from ext4??? Most of my files are .wav files.
If I can read, open, and execute everything from ext4, then it would seem better to format with native filesystem on all drives. Maybe my errors have to do with the interoperability, or lack thereof, of two different filesystems . . . I do NOT need Windows recognition.
3. gparted does NOT read my drive. Can I assume from that that my drive is NOT mounted, in spite of what lsusb says, and that I must do a manual mount?

---

### Post by sudodus on 2014-08-20
> **Kurt_Alan said:**
> 

@oldfred --
@sedawk --

I am still following up with your suggestions. Meanwhile:

1. What is the difference between lsusb and mount? Via lsusb my device IS recognized. Via mount my device is NOT recognized. So if my device is not mounted, why is it showing up in lsusb?

lsusb lists all usb devices, also devices that cannot be mounted. mount (without parameters) lists mounted devices.
> 
2. Re: formatting flash drives with gparted fat32 or NTFS VERSUS ext4, are there any file types that cannot be read from ext4??? Most of my files are .wav files.
If I can read, open, and execute everything from ext4, then it would seem better to format with native filesystem on all drives. Maybe my errors have to do with the interoperability, or lack thereof, of two different filesystems . . . I do NOT need Windows recognition.

There are advantages with a native file system (ext4), but linux has no problems reading files and directories in fat32 and ntfs file systems.

But linux is not quite capable of repairing those foreign file systems. And the permissions are set globally at the mounting instead of individually (ext4 is managed with more flexibility).
> 
3. gparted does NOT read my drive. Can I assume from that that my drive is NOT mounted, in spite of what lsusb says, and that I must do a manual mount?

If you drive is not mounted, it might still be possible to mount its partition with the terminal window command mount (with parameters). If you try

```
sudo mount /dev/sdb1 /mnt
``` (assuming that your USB drive is still there at /dev/sdb).

- What is the output to the terminal window?
- What do you see with the command

```
ls -l /mnt
```

---

### Post by Kurt_Alan on 2014-08-20
> **sudodus said:**
> lsusb lists all usb devices, also devices that cannot be mounted. mount (without parameters) lists mounted devices.

There are advantages with a native file system (ext4), but linux has no problems reading files and directories in fat32 and ntfs file systems.

But linux is not quite capable of repairing those foreign file systems. And the permissions are set globally at the mounting instead of individually (ext4 is managed with more flexibility).


If you drive is not mounted, it might still be possible to mount its partition with the terminal window command mount (with parameters). If you try

```
sudo mount /dev/sdb1 /mnt
``` (assuming that your USB drive is still there at /dev/sdb).

- What is the output to the terminal window?
- What do you see with the command

```
ls -l /mnt
```

Status Update:
a. Info. Yes, I checked info lsusb and confirmed that the lsusb utility only identifies buses, not mounting. So an unmounted drive will still show up on lsusb
Event sequence:
b. Plug in drive. No GUI interface.
c. df Only my root partition appears: /dev/sda1
d. sudo fdisk -l  My drive appears as: ```
  Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *        2048    15359999     7678976    b  W95 FAT32 
```
e. I'm not sure if it's mounted, since it doesn't show in df, so I try: ```
 sudo mount /dev/sdb1 /mnt 
``` and ```
 mount 
``` and the output is: ```
 /dev/sdb1 on /mnt type vfat (rw) 
``` so, yes, I can confirm that it is mounted.
f. I can even unmount it: ```
 sudo umount /dev/sdb1 /mnt 
``` which outputs: ```
 umount: /mnt: not mounted 
``` and when I check mount, in fact, the drive no longer appears.

Conclusion:
I've learned to mount and unmount a drive and to determine if a drive is mounted.
Problem:
1. No GUI window means the drive is useless because I have no access.
2. When I ```
 sudo gparted 
``` after I have mounted the drive, it does appear. I will now try reformatting from fat32 to ext4 and find out if this solves my GUI interface problem. Successfully reformatted to ext4.
3. Reboot. (gparted unmounted the drive--what will happen now? Linux should automatically assign a mount point for the device.)
4. Result of experiment: The filesystem (fat32) is not the problem: Linux does not read the drive either by GUI or by mount: The drive is unmounted. And, if I mount it, I still can't use it w/o a GUI interface.
5. Linux box #2, same distro, sees device instantly via GUI and mount command shows that it has been mounted.

Any possibility of a hardware problem on linux box 1? Any other troubleshooting solutions short of OS reinstall?

Even though I don't have a solution yet, you, sudodus, is what makes the Ubuntu community outstanding for support.

---

### Post by sudodus on 2014-08-21
This command

```
 sudo umount /dev/sdb1 /mnt 
```

unmounts /dev/sdb1, and then tries to unmount /mnt, but it was already unmounted, because it is 'the other end' of mounting /dev/sdb1.

Use only 
```
 sudo umount /dev/sdb1
``` or
```
 sudo umount /mnt 
```
to unmount.

> **Kurt_Alan said:**
> ...
Conclusion:
I've learned to mount and unmount a drive and to determine if a drive is mounted.
Problem:
1. No GUI window means the drive is useless because I have no access.

I don't understand what you mean by "I have no access". Is it too inconvenient to mount it from a terminal window?

In that case you may need to change the permissions and or ownership of the default mount point. Please post the output of
```
ls -l /media
```
and
```
ls -ld /media
```
I hope it will show what to change in order to make it work with automatic mounting.
> 
And, if I mount it, I still can't use it w/o a GUI interface.
...

Is this a server, desktop or laptop computer? I don't understand what you mean by "can't use it w/o a GUI interface".

---

### Post by mastablasta on 2014-08-21
I would still run a chkdsk on it first. it is possible that part of file system is corrupted. even if you manage to mount it in some "box" it doesn't mean it is mounted properly.
chkdsk can be run using repair disks and similar. maybe even using FreeDOS. you do not nee the whole windows OS to run it.

---

### Post by Kurt_Alan on 2014-08-21
Mounting is no longer the issue. The problem is that when I plug in the drive, there is no GUI interface that enables me to interact with the drive, its files, play music, etc. Desktop settings in xfce are checked so that all removable media should appear--but none of my flash drives on this netbook linux box, my primary computer, appear. Therefore, even though I can mount the drive, I cannot use it.  Whereas if I plug the same drive into linux box 2, same distro, the drive's icon appears immediately and I can use it. All of my flash drives on linux box 1--netbook, see specs below--are inaccessible.

I also believe that when I insert a drive after booting, that the OS will not automatically mount it, as it should, and that I have to do a manual mount. Yes, confirmed. My OS will not automatically mount any of my several flash drives. Not sure if you need this: ```
 lucas@lucas-Inspiron-1011:~$ ls -l /media
total 4
drwxr-x---+ 2 root root 4096 Aug 14 19:22 lucas 
``` and ```
 lucas@lucas-Inspiron-1011:~$ ls -ld /media
drwxr-xr-x 3 root root 4096 Jun 30 21:02 /media 
```

---

### Post by Kurt_Alan on 2014-08-21
I have already formatted one flash drive to ext4 and the same problems exist, so I don't think chkdsk is relevant.

---

### Post by sudodus on 2014-08-21
> **Kurt_Alan said:**
> Mounting is no longer the issue. The problem is that when I plug in the drive, there is no GUI interface that enables me to interact with the drive, its files, play music, etc. Desktop settings in xfce are checked so that all removable media should appear--but none of my flash drives on this netbook linux box, my primary computer, appear. Therefore, even though I can mount the drive, I cannot use it.  Whereas if I plug the same drive into linux box 2, same distro, the drive's icon appears immediately and I can use it. All of my flash drives on linux box 1--netbook, see specs below--are inaccessible.

I also believe that when I insert a drive after booting, that the OS will not automatically mount it, as it should, and that I have to do a manual mount. Yes, confirmed. My OS will not automatically mount any of my several flash drives. Not sure if you need this: ```
 lucas@lucas-Inspiron-1011:~$ ls -l /media
total 4
drwxr-x---+ 2 [COLOR=#ff0000]root root[/COLOR] 4096 Aug 14 19:22 lucas 
``` and ```
 lucas@lucas-Inspiron-1011:~$ ls -ld /media
drwxr-xr-x 3 [COLOR=#ff0000]root root[/COLOR] 4096 Jun 30 21:02 /media 
```

I think the ownership of the mount point for automatic mounting is the problem. Mounting is done without superuser (root) privileges. Try to change the ownership of /media/lucas.

```
sudo chown lucas:lucas /media/lucas
```

I'm assuming that your user ID is lucas. If not, create another directory in /media with the same name as your user ID.

After this, it might work with automatic mounting etc. Try un-plugging and re-plugging a pendrive. But remember to ***unmount (eject) the pendrive before unplugging***. Otherwise the file system can be corrupted.

-o-

But after manual mounting you should be able to browse with your file browser (GUI) to **/mnt** and then access the files in the USB drives.

---

### Post by Kurt_Alan on 2014-08-22
> **sudodus said:**
> I think the ownership of the mount point for automatic mounting is the problem. Mounting is done without superuser (root) privileges. Try to change the ownership of /media/lucas.

```
sudo chown lucas:lucas /media/lucas
```

I'm assuming that your user ID is lucas. If not, create another directory in /media with the same name as your user ID.

After this, it might work with automatic mounting etc. Try un-plugging and re-plugging a pendrive. But remember to ***unmount (eject) the pendrive before unplugging***. Otherwise the file system can be corrupted.

-o-

But after manual mounting you should be able to browse with your file browser (GUI) to **/mnt** and then access the files in the USB drives.



I can successfully mount and unmount my drives manually. And, yes, to my surprise, I can access and utilize my files via Thunar filemanager navigating /mnt directory (GUI). I got your two points on the umount format and remembering. It's harder to remember to umount manually when you can't see the drive icon! 

I could accept the above as a work-around and mark this thread as solved but I would like to try first and solve the automount problem.

You suggested that the problem might be with the ownership of the mount point, noting that mounting is done by non-root owner. 

Accordingly I: ```
 sudo chown lucas:lucas /media/lucas 
``` which outputs: ```
 drwxr-x---+ 2 lucas lucas 4096 Aug 14 19:22 lucas
 
``` so now ownership of /media is non-root. However, when I also: ```
 ls -ld /media 
``` 
I am still root: ```
 drwxr-xr-x 3 root root 4096 Jun 30 21:02 /media
 
```

Does option -ld mean copy symbolic links?
This is where I'm stuck. I don't understand why, in the first case root was changed to lucas but in the second case root remained root, /media being the same in both cases.

---

### Post by sudodus on 2014-08-22
Did you try to unmount and unplug the pendrive and then plug it in again? Maybe it works.

If not, maybe it uses some 'synthetic' user ID, and we need to change the permissions too

```
sudo chmod ugo+rwx /media/lucas
```

This means full permissions for 'everybody' but if you are the only user, it does not matter. Otherwise we should narrow it down.

I don't think you need to bother about the ownership of /media, as long as there is /media/lucas, and it has good ownership and permissions.

Try once more to unmount and unplug the pendrive and then plug it in again! I think and hope it works now.

---

### Post by Kurt_Alan on 2014-08-24
> **sudodus said:**
> Did you try to unmount and unplug the pendrive and then plug it in again? Maybe it works.

If not, maybe it uses some 'synthetic' user ID, and we need to change the permissions too

```
sudo chmod ugo+rwx /media/lucas
```

This means full permissions for 'everybody' but if you are the only user, it does not matter. Otherwise we should narrow it down.

I don't think you need to bother about the ownership of /media, as long as there is /media/lucas, and it has good ownership and permissions.

Try once more to unmount and unplug the pendrive and then plug it in again! I think and hope it works now.

I applied the chmod input to change ownership to all but this had no effect on automounting.

None of my four or five drives will automount. I plugged multiple drives in different ports, rebooted, etc. All these drives automount on a different linux box.

Meanwhile, I found out that my workaround of manually mounting and navigating to /media files is not sufficient for solving my problem.  This is because when I download data from the cloud, my drive, even though it has been manually mounted, does not show in Places. Therefore, I cannot add files directly to drive via downloading.

My /dev/sda1 is one of the earliest solid state drives--only 8 GB. Therefore, I use flashdrives to download subsets of data from the cloud. If I cannot do this, then I can't access my data because there is not enough space on /dev/sda1 to download to /media

I think the smoking gun is the automount fail. Is this a daemon? In what directory is this process described? Is there a way to troubleshoot the automount fail?

---

### Post by sudodus on 2014-08-25
I'm not sure about this, but I think you can start looking at ***udisks***

```
man udisks
```

---

### Post by Kurt_Alan on 2014-08-27
> **sudodus said:**
> I'm not sure about this, but I think you can start looking at ***udisks***

```
man udisks
```

I'm marking this thread SOLVED because I solved part of my problem by learning mount and umount.  Thanks.

---

