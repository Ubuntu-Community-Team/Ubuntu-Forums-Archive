---
title: "mounting an old sony mp3 player"
date: 2008-06-29
forum: General Help
---

### Post by davesec on 2008-06-29
hi, so i'm not great at computers and am having a hell of time trying to get this to work.

it's a sony nw-e507, which is an old mp3 player.

if i plug it in, nothing happens other than the mp3 player starts to charge. if i type in 'fdisk -l' in terminal, nothing happens.

if i type in 'lsusb', i get this:

Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 0000:0000  


if i type in 'sudo lsusb', i get this:

Bus 003 Device 005: ID 054c:01fb Sony Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 0000:0000  

so i guess that means it's recognized? if i open up gparted AFTER i've typed in 'sudo lsusb' it recognizes it as a FAT32 /dev/sdb1 drive

if i open up gparted BEFORE i type in 'sudo lsusb', it does not detect the drive. if i click 'refresh devices', it searches for a bit, then shuts down without any warning/prompting.

anyway, in gparted it says the mp3 player has a 'boot' flag, that it isn't mounted, and there's a warning saying "unable to read the contents of this filesystem!"

i tried "sudo rmmod ehci_hcd" and i'm not sure if that does anything.

after i do all this, 'sudo lsusb' no longer shows the SONY line, and just 'lsusb' shows it

if i try mounting it i type:

"sudo mount /dev/sdb1 /media/usbdrive -t vfat"

this takes the computer a few minutes and then shows a 'usbdrive' option in the 'Places' tab. If I try to open this, the window freezes and I have to force quit it. All my desktop items also disappear while doing this. (If I unmount it using 'sudo umount' everything goes back to normal.

If I click on the 'Computer' tab in 'Places', it recognizes a Sony device in addition to the 'usbdrive', but if I try to mount that at anytime it says I can't, and that there's probably no media on the drive.

Anyway, if anyone can help me, I'd really appreciate it. I don't really know what I'm doing, and I'm trying everything. I know that once I get this to mount I have to get jsymphonic or something working on it in order to transfer music without using Sony's stupid software, but I guess one step at a time.

Please help!
Thanks!

---

### Post by cozmicharlie on 2008-06-29
This might work for you:

Install pmount:
Code:

sudo apt-get install pmount

and then:
Code:

pmount /dev/sdxx 

For sdxx use whatever the device is showing up as in your system. To find out type or cut and paste:
Code:

ls /dev/disk/by-label -lah

If this does not work you may have to modprobe the usb serial but see if this works first.

Someone on another thread recommended this for managing ([http://nwe00xmp3man.sourceforge.net/](http://nwe00xmp3man.sourceforge.net/)) - it looks like it would work for your plyer.

---

### Post by davesec on 2008-06-29
hi!

thank you for writing back so quickly!

copying dave@dave:~$ ls /dev/disk/by-label -lah

returns

ls: /dev/disk/by-label: No such file or directory

fdisk -l reveals the following:

Disk /dev/sdc: 511 MB, 511180800 bytes
32 heads, 32 sectors/track, 975 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0x00000000

which i believe is the mp3 player, since /dev/sda is my harddrive. so i tried 

pmount /dev/sdc

and it sort of froze. it's been about 5 minutes now and nothing has happened.

i've downloaded the program you recommended, but in order to do it i need to be able to copy some files onto the mp3 player, and it absolutely won't let me do that in my current situation. any 'cp -r' commands end with permission denied, omitted file, etc etc etc. i do not think it's properly mounted.

what is a modprobe?

thank you!
dave

---

### Post by cozmicharlie on 2008-06-29
If it is still going - go ahead and stop it.  it should not take that long.

Yes, it looks like it is not recognizing it so you have to manually set the usb to recognize your device (in a sense).  

*Whenever I write type - you can type or cut and paste

Disconnect the device
Open a terminal and type:
```
sudo -i
```
Now all the commands you type will be as root 

Before you insert your device type 
```
cat /proc/bus/usb/devices > devices
```

Insert the device and type (this is optional and is just a double check) 
```
dmesg
```
you will get a long output - at the end though it should show your device. 

now type:
```
diff /proc/bus/usb/devices devices | grep Vendor
```
the output should be something like this
< P: Vendor=1234 ProdID=5678 Rev= 0.00
write down the vendor and ID

Now we will remove the usb and replace it with your information
eject the device
```
modprobe -r usbserial
```
Now in teminal type following code Replacing values 1234 and 5678 with your own output from previously noted lines ::
```
modprobe usbserial vendor=0x1234 product=0x5678


```Plug it in and see if that works.

---

### Post by davesec on 2008-07-04
dave@dave:~$ sudo -i
root@dave:~# cat /proc/bus/usb/devices > devices
cat: /proc/bus/usb/devices: No such file or directory



i'm probably retarded but this is what is coming up after step 2

any thoughts?

---

### Post by davesec on 2008-07-04
i went ahead and tried 'dmesg', here's the end of it (let me know if you need more)

[13921.144000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[13921.144000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[13924.928000] sd 3:0:0:0: [sdb] 998400 512-byte hardware sectors (511 MB)
[13925.680000] sd 3:0:0:0: [sdb] Write Protect is off
[13925.680000] sd 3:0:0:0: [sdb] Mode Sense: 00 6a 00 00
[13925.680000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[13928.200000] sd 3:0:0:0: [sdb] 998400 512-byte hardware sectors (511 MB)
[13928.956000] sd 3:0:0:0: [sdb] Write Protect is off
[13928.956000] sd 3:0:0:0: [sdb] Mode Sense: 00 6a 00 00
[13928.956000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[13928.956000]  sdb: sdb1

this only worked after i ran partition editor. i tried it earlier and received a whole bunch of this:

[13741.192000] scsi 2:0:0:0: rejecting I/O to dead device
[13741.192000] scsi 2:0:0:0: rejecting I/O to dead device
[13741.192000] scsi 2:0:0:0: rejecting I/O to dead device
[13741.192000] scsi 2:0:0:0: rejecting I/O to dead device
[13741.192000] scsi 2:0:0:0: rejecting I/O to dead device
[13741.192000] scsi 2:0:0:0: rejecting I/O to dead device
[13741.192000] scsi 2:0:0:0: rejecting I/O to dead device
[13741.192000] scsi 2:0:0:0: rejecting I/O to dead device
[13741.192000] scsi 2:0:0:0: rejecting I/O to dead device

anyway. the third command returned this again:

root@dave:~# diff /proc/bus/usb/devices devices | grep Vendor
diff: /proc/bus/usb/devices: No such file or directory

thanks so much for the help, though, i really appreciate it.

---

### Post by davesec on 2008-07-04
bump!

---

### Post by davesec on 2008-07-05
lord jesus it's mounting!

who knows what happened... maybe typing in 'lsusb' 80 kazillion times over a three-day span suddenly fixes the problem. i'm not sure what worked, but it now pops up as 'disk'

now i need to get jsymphonic to work - the encryption (i believe it uses ffmpeg) doesn't seem to work, i keep getting MG errors.. i read that since my mp3 player is old, i need to generate a 'dvid.dat' file.. however you need windows to do this, which sucks. i'll try it on my friends' computer.

anyway, thanks! the problem is solved, but damned if i know how. for anyone looking for help, there's a special command you type to revert from usb 2 to usb 1.1 (search around for this, i don't have the link), and the only other stuff i did was turn on partition edition a thousand times, tried to force mount a bunch of invalid drives, and lsusb/sudo lsusb/dmesg so many times i think the keys are starting to not work anymore

---

### Post by ChameleonDave on 2008-07-05
> **davesec said:**
> dave@dave:~$ sudo -i
root@dave:~# cat /proc/bus/usb/devices > devices
cat: /proc/bus/usb/devices: No such file or directory



It works for me, so I imagine you don't have the same version of Ubuntu.

Type "cat /etc/lsb-release" at the command line.

---

### Post by DLF44 on 2008-12-07
i have the same problem with my sony mp3 player, when i type is step 2 i get the same code as the person above. "no such file directory"

ive been trying everything and cant find anything that works or gets mine anywhere

---

### Post by cozmicharlie on 2008-12-08
Did you try the command chameleondave suggested?

Did you try jsymphonic?
[http://backports.ubuntuforums.com/showthread.php?t=716477&page=2](http://backports.ubuntuforums.com/showthread.php?t=716477&page=2)
you will need sun java JRE installed.

---

