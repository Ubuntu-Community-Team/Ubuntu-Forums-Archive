---
title: "Kernel Panic"
date: 2008-02-09
forum: General Help
---

### Post by phoenix5002 on 2008-02-09
When I try to boot ubuntu 7.10 gutsy I get a "Kernel Panic" error.

Before I shutdown prior to this error, I was trying to fix my laptop suspend/hibernate problem and one suggestion i saw was to do:
**sudo apt-get install uswsusp**

so I did.  But I got a message saying it couldn't find a swap partition, should I let it set a swap or something like that and I selected no and then I pressed ctrl+c to stop it from finishing, then I thought I would remove the package by following the tip here:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

so i did **sudo apt-get autoclean**
and that's it.  I'm pretty sure all that stuff I did was what caused the problem I can't imaging what else it would be, and I tried to be as detailed about what I did as I could.

I can't boot anymore so pleaaase help me.


[EDIT]
Would it be possible to go into ubuntu with the live CD and make corrections?  i have the Gutsy Gibbon live CD

---

### Post by SpaceTeddy on 2008-02-09
what does the kernel panic say... usually the kernel gives some reason why it goes haywire...

as for repairing with a cd... maybe... depends on the problem.

---

### Post by phoenix5002 on 2008-02-09
When I start it normally it will do the grub loader and then this is what I see on my screen:

```
Starting up...
**[   11.427450] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)**
```


If I press esc at the grub loader and go into maintenance mode I see this:

```
[   12.926539] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.926957] input: Macintosh mouse button emulation as /class/input/input0
[   12.927151] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.931829] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.931891] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.932234] mice: PS/2 mouse device common for all mice
[   12.932476] EISA: Probing bus 0 at eisa.0
[   12.932538] Cannot allocate resource for EISA slot 1
[   12.932622] Cannot allocate resource for EISA slot 8
[   12.932676] EISA: Detected 0 cards.
[   12.932862] TCP cubic registered
[   12.932930] NET; Registered protocol family 1
[   12.933013] Using IPI No-Shortcut mode
[   12.933285]    Magic number: 12:482:592
[   12.964721] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.970278] Switched to high resolution mode on CPU 0
[   13.034290] VFS: Cannot open root device "UUID=efae0219-63c2-4096-a134-006a9d00ff223" or unknown-block(0,0)
[   13.034357] Please append a correct "root=" boot option; here are the available partitions:
**[   11.427450] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)**
```

I did my best to type it exactly as it appeared on the screen and all the numbers were probably a waste of time but I did it anyway.

---

### Post by SpaceTeddy on 2008-02-09
looks like the kernel cannot find your harddrive at the location grub tells it it should be. i take it your hd has not changed a bit in the last days since this problem occured?

ok, assuming that your drive is still fully intakt and only grub is messing up, you should be able to fix that with a live cd by letting grub reconfigure itself.

this can be done by booting the normal ubuntu cd and opening a terminal.
once there, you will need to check if your hd is mounted or not. answers about mounting filesystems can be found here [http://users.bigpond.net.au/hermanzone/p10.htm]("http://users.bigpond.net.au/hermanzone/p10.htm") (thanks to jan quark for the link)
unforteunatly i cannot tell you how to mount as i am not aware of your setup. 

once you got your hd working (i am assuming /media/rescue as the mountpoint for now) you will need to tell grub to reconfigure itself. this can be done via
> sudo grub-install --recheck --root-directory=/media/rescue/
and last you will need to write grub back to the drive

> sudo grub-install --root-directory=/media/rescue/

i am not sure if this will work, but i think there is no reason not to try it :)

PS: if i run the grub-install in my vm, i get the following output

> 
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda


---

### Post by phoenix5002 on 2008-02-09
Ok here is what I tried, which didn't work (get same errors as before).

I found that my harddrive was mounted to /media/disk
so I typed in exactly what you said but the commands weren't working.
I did try this:
sudo grub-install --root-directory=/media/disk /dev/hda
which made the command execute properly and I got the same output as you, but I tried rebooting and it failed with Kernel panic still.

---

### Post by SpaceTeddy on 2008-02-10
ok, short of a reinstall i only really have one more guess what could be wrong.

check if the file /etc/fstab (open with "sudo gedit /etc/fstab") contains the right devices. if you are in doubt what the right devices are, just paste it here along with a partition listing (get that via "sudo fdisk -l") and the uuid's for your hd's (get them with with "sudo vol_id $device" where $device is the partition what you want the uuid from. You will need the vol_id from every partition that is marked as linux

as an example, here are printouts of what my files look like

/etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=33003641-e6b1-459c-ba82-7da16935245d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=70ad5c35-fddb-4c02-b594-53c847f1f347 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


sudo fdisk -l
> sudo fdisk -l
[sudo] password for ipoese:

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f047d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         993     7976241   83  Linux
/dev/sda2             994        1044      409657+   5  Extended
/dev/sda5             994        1044      409626   82  Linux swap / Solaris


sudo vol_id /dev/sda1
> sudo vol_id /dev/sda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=33003641-e6b1-459c-ba82-7da16935245d
ID_FS_UUID_ENC=33003641-e6b1-459c-ba82-7da16935245d
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=


hope we still can fix this :) 
sorry i'm not explaining more, but i really need to hurry

**EDIT**
one more thing - please (if you decide to post the files here) give a listing of your grub configuration aswell (open it via "sudo gedit /boot/grub/menu.lst").

---

### Post by phoenix5002 on 2008-02-11
I couldn't take it anymore so I reinstalled ubuntu 7.10.

It was a new installation to begin with so it's no big deal, but thank you for taking the time to help me.

---

### Post by chrisccoulson on 2008-02-11
D'oh! Looking through your posts, it looks like your /boot/grub/menu.lst thought your root partition was at UUID=efae0219-63c2-4096-a134-006a9d00ff223, which was wrong. It should have been UUID=33003641-e6b1-459c-ba82-7da16935245d, which was the output of vol_id for /dev/sda1, and was consistent with the contents of your /etc/fstab.

It seems like something screwed up your /boot/grub/menu.lst. Maybe the '# kopts' line had the wrong UUID specified, and you ran update-grub which screwed it up. Modifying your menu.lst from the liveCD environment would have fixed this.

Not that any of this is of any use anymore, but don't be so quick to reinstall next time. This type of thing is fairly easy to fix and shouldn't require a reinstall

---

### Post by SpaceTeddy on 2008-02-12
the posts i did are acctually working. They are from a fresh ubuntu vm install and it boots. :) i just posted them as an example. 

But it looks like this thread died anyway, so i won't follow it anymore :(

---

