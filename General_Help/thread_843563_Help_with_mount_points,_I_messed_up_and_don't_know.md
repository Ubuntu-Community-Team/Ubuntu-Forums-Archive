---
title: "Help with mount points, I messed up and don't know how to fix this...."
date: 2008-06-28
forum: General Help
---

### Post by tmcarson1 on 2008-06-28
Ok, I have an mp3 player, with an sd card.  Works fine, was mounting just fine as 2 seperate drives in ubuntu.

Trying to get it to work properly with a sync program, I went to the drive icon on the desktop, clicked properties, volume and changed the Mount Point to /sansa on one and /sdmicro on the other.

Now when I connect it and try to mount it it gives me an error saying I cannot use the '/' symbol in a mount point.

Question is, how do I go in there and change it and take out the '/' symbol so that they will mount again?

The 2 drives show up in 'Places' but properties there doesn't give me the option to change the name of the mount point to remove the '/'.

So they are showing up, just can't mount them.  Any suggestions would be greatly appreciated.

Thanks
Tom


Update:
After some research it seems this is a known bug that has not been resolved yet, here is a link to the details on how to fix this if you get in this problem too.

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668)

---

### Post by tmcarson1 on 2008-06-28
It looks to me like they are showing up as /dev/sdd and /dev/sdc, but I don't see where it says a mountpoint for them for me to edit the mount point.


Here is the error I get when I plug the device in or try to mount it:
Cannot mount volume.
Unable to mount the volume 'Sansaone'.

Details:
mount_point cannot contain the following characters:newline, G_DIR_SEPERATOR (usually /)  
OK


Here is what dmesg shows:

  559.348417] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[  559.348465] sd 7:0:0:1: Attached scsi generic sg4 type 0
[ 2198.913764] usb 4-2: USB disconnect, address 8
[ 2241.346122] usb 4-2: new high speed USB device using ehci_hcd and address 9
[ 2241.485371] usb 4-2: configuration #128 chosen from 1 choice
[ 2241.514087] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2241.516017] usb-storage: device found at 9
[ 2241.516023] usb-storage: waiting for device to settle before scanning
[ 2246.512946] usb-storage: device scan complete
[ 2246.513970] scsi 8:0:0:0: Direct-Access     SanDisk  Sansa c250       Sans PQ: 0 ANSI: 0
[ 2246.514937] scsi 8:0:0:1: Direct-Access     SanDisk  Sansa c250       Sans PQ: 0 ANSI: 0
[ 2246.516433] sd 8:0:0:0: [sdc] 4013056 512-byte hardware sectors (2055 MB)
[ 2246.517556] sd 8:0:0:0: [sdc] Write Protect is off
[ 2246.517564] sd 8:0:0:0: [sdc] Mode Sense: 3f 00 00 08
[ 2246.517567] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 2246.520040] sd 8:0:0:0: [sdc] 4013056 512-byte hardware sectors (2055 MB)
[ 2246.521043] sd 8:0:0:0: [sdc] Write Protect is off
[ 2246.521049] sd 8:0:0:0: [sdc] Mode Sense: 3f 00 00 08
[ 2246.521052] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 2246.521058]  sdc: sdc1 sdc2
[ 2246.524087] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 2246.524138] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 2246.525410] sd 8:0:0:1: [sdd] 3932160 512-byte hardware sectors (2013 MB)
[ 2246.526285] sd 8:0:0:1: [sdd] Write Protect is off
[ 2246.526290] sd 8:0:0:1: [sdd] Mode Sense: 3f 00 00 08
[ 2246.526292] sd 8:0:0:1: [sdd] Assuming drive cache: write through
[ 2246.529029] sd 8:0:0:1: [sdd] 3932160 512-byte hardware sectors (2013 MB)
[ 2246.529907] sd 8:0:0:1: [sdd] Write Protect is off
[ 2246.529911] sd 8:0:0:1: [sdd] Mode Sense: 3f 00 00 08
[ 2246.529913] sd 8:0:0:1: [sdd] Assuming drive cache: write through
[ 2246.529920]  sdd: sdd1
[ 2246.532714] sd 8:0:0:1: [sdd] Attached SCSI removable disk
[ 2246.532763] sd 8:0:0:1: Attached scsi generic sg4 type 0


And here is what fstab shows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc8
UUID=4f9b29c7-778d-4489-99ea-2093d69149e5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc9
UUID=b4bc8947-54d5-4b73-ba8a-6d85342b7b71 /linuxmedia     ext3    defaults        0       2
/dev/hdc9 /storage ext3 defaults 0 0
# /dev/hdc5
UUID=7CE22C3A417A08E3 /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc6
UUID=87EA116A65CF426B /media/hdc6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc7
UUID=2d0c83d2-6a64-4f8d-884c-9223032fb145 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by drebux on 2008-07-03
I can't help you with your problem due to the fact I'm very new to Linux, but I wanted to reply to this thread to say thank you for the link you provided. I screwed up a mount point and couldn't figure out how to change the key, can't believe I didn't think of gconf-editor before.

Hope someone here can help you.

---

### Post by GuitarRocker2562 on 2008-07-03
try making those directories, sudo mkdir

---

### Post by akatsuki on 2008-08-05
not sure if you solved your problem yet, but i did the same thing as you and i just got everything fixed.

followed the instruction in the first post from this thread: 
[http://ubuntuforums.org/showthread.php?t=785263&highlight=mount+point+reset]("http://ubuntuforums.org/showthread.php?t=785263&highlight=mount+point+reset")

by choosing to mount the drives on boot, it also makes the drives mount instantly as well.
thus, you can now go back to properties and edit the mount point (ie: delete what you put in) and done

---

### Post by fhsm on 2008-08-06
This is a known bug and a problem I just had (and solved) I already [posted a solution]("http://ubuntuforums.org/showpost.php?p=5530231&postcount=44") under known bug and workaround.

Hope it works for you.

---

