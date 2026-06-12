---
title: "GTKPod can't read iTunesDB"
date: 2005-04-10
forum: General Help
---

### Post by kjerstib on 2005-04-10
Hi

After installing Ubuntu I've tried to set it up to work with my iPOd mini, formatted on Windows. The iPod mounts correctly (media/ipod) when I plug it in, but when I try to read the iTunesDB from gtkpod, I get nothing. When synchronizing it complains that the db is unavailable. 

dmesg gives this: 
```

usb 3-4: new high speed USB device using ehci_hcd and address 4
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 7999488 512-byte hdwr sectors (4096 MB)
sdb: Write Protect is off
sdb: Mode Sense: 64 00 00 08
sdb: assuming drive cache: write through
SCSI device sdb: 7999488 512-byte hdwr sectors (4096 MB)
sdb: Write Protect is off
sdb: Mode Sense: 64 00 00 08
sdb: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0: p1 p2
Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
usb-storage: device scan complete
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
usb 3-4: USB disconnect, address 4
usb 3-4: new high speed USB device using ehci_hcd and address 5
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 7999488 512-byte hdwr sectors (4096 MB)
sdb: Write Protect is off
sdb: Mode Sense: 64 00 00 08
sdb: assuming drive cache: write through
SCSI device sdb: 7999488 512-byte hdwr sectors (4096 MB)
sdb: Write Protect is off
sdb: Mode Sense: 64 00 00 08
sdb: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: p1 p2
Attached scsi removable disk sdb at scsi3, channel 0, id 0, lun 0
usb-storage: device scan complete
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
usb 3-4: USB disconnect, address 5
usb 3-4: new high speed USB device using ehci_hcd and address 6
scsi4 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 7999488 512-byte hdwr sectors (4096 MB)
sdb: Write Protect is off
sdb: Mode Sense: 64 00 00 08
sdb: assuming drive cache: write through
SCSI device sdb: 7999488 512-byte hdwr sectors (4096 MB)
sdb: Write Protect is off
sdb: Mode Sense: 64 00 00 08
sdb: assuming drive cache: write through
 /dev/scsi/host4/bus0/target0/lun0: p1 p2
Attached scsi removable disk sdb at scsi4, channel 0, id 0, lun 0
usb-storage: device scan complete

```

I'm no expert, but it seems odd that the device is recognized twice (if that's what's happening), and there are some messages that could be errors. Any ideas what might be wrong?

---

### Post by c_dog on 2005-04-10
Double Check the gtkpod input/output preferences to be sure that it's not set to look for /mnt/ipod. Older versions of gtkpod did this. Also HAL and dbus sometimes seem to try handle mounting the windows iPod volume names on their own in the /media folder. You may need to create a symlink from /media/ipod to it. My 3G iPod hass been working great with the final release Hoary. But, there were some real problems last week with the RC and Daily Hoary having a broken HAL and dbus. Was not putting a iPod icon on the desktop and was not able to read the database.

---

### Post by kjerstib on 2005-04-11
[QUOTE=c_dog]Double Check the gtkpod input/output preferences to be sure that it's not set to look for /mnt/ipod. Older versions of gtkpod did this. Also HAL and dbus sometimes seem to try handle mounting the windows iPod volume names on their own in the /media folder. You may need to create a symlink from /media/ipod to it. My 3G iPod hass been working great with the final release Hoary. But, there were some real problems last week with the RC and Daily Hoary having a broken HAL and dbus. Was not putting a iPod icon on the desktop and was not able to read the database.[/QUOTE]
 I checked the gtkpod settings, and they point to /media/ipod. I have changed /etc/fstab to mount the ipod to /media/ipod when I plug it in. 

I have a mini iPod, should that make a difference? 

Anyone else having similar problems, or maybe a clue as to what's wrong?

---

### Post by gborbolla on 2005-04-11
Do you have an entry in fstab for your ipod? That can give you some trouble since hotplug automatically mounts your ipod at /media/[name of your ipod], ie my ipod's name is PANDA so hotplugs leave it in /media/PANDA.

Hope this helps.

---

### Post by astoltz on 2005-04-11
When I upgraded warty to hoary, my ipod changed from being mounted at /media/ipod to /media/iPod (capital P).  Could that be the problem you are seeing?

---

### Post by johndoe on 2005-04-12
I have an iPod mini, formatted a la Windows.

After connecting it (via USB) Hoary automounts it under /media/IPOD and a desktop icon appears saying 'IPOD'. Setting the location in gtkpod to '/media/IPOD' lets it all work automagically for me.

After I'm done I right-click the desktop icon (or the location icon in Nautilus browser) and select 'unmount volume', wait for the icon to disappear and after that do a 'sudo eject /dev/sda' to get rid of the 'Do not disconnect' message on the iPod.

Works like a charm for me.

(edit)

The iPod was first formatted for MacOS and Hoary mounted it under /media/iPod then. Maybe it mounts the USB device at /media/ and then the volume name on the device?

Also, you might want to use dd for a firmware backup - but only do this if you really, really know what you're doing. Incorrect use of 'dd' can nuke your iPod.. (IIRC the firmware is at /dev/sda1, if the iPod is /dev/sda).

---

### Post by kjerstib on 2005-04-17
[QUOTE=johndoe]I have an iPod mini, formatted a la Windows.

After connecting it (via USB) Hoary automounts it under /media/IPOD and a desktop icon appears saying 'IPOD'. Setting the location in gtkpod to '/media/IPOD' lets it all work automagically for me.

After I'm done I right-click the desktop icon (or the location icon in Nautilus browser) and select 'unmount volume', wait for the icon to disappear and after that do a 'sudo eject /dev/sda' to get rid of the 'Do not disconnect' message on the iPod.

Works like a charm for me.

(edit)

The iPod was first formatted for MacOS and Hoary mounted it under /media/iPod then. Maybe it mounts the USB device at /media/ and then the volume name on the device?

Also, you might want to use dd for a firmware backup - but only do this if you really, really know what you're doing. Incorrect use of 'dd' can nuke your iPod.. (IIRC the firmware is at /dev/sda1, if the iPod is /dev/sda).[/QUOTE]
 After removing the entry in /etc/fstab as suggested above, the ipod wont automount at all. It is recognized by HAL, but  not mounted.

Someone else recommended using /etc/fstab, but why shouldn't I.

---

### Post by mcescher on 2005-04-23
Complete noob to linux here.

Can anyone be so kind as to tell me the steps I need to go through to mount my 3rd gen iPod. I plug it in via firewire and there seems to be no communication with the computer. Under "Winblows" it works fine.

I have no clue how to mount this device. I have tried leaving it connected and rebooting....nothing. The iPod charges it's battery though.

Any help wiould be appreciated.

MC

---

### Post by c_dog on 2005-04-24
I've been using a 3G iPod on firewire on Hoary and SuSE 9.2 and now 9.3. Both see the iPod just fine "out of the box" with no special tweaking. What kind of firewire card are you using. Some people have had trouble with the firewire ports on Soundblaster Audigy2 cards because Creative didn't follow the IEEE 1394 spec properly. The iPod should be formated in Windows FAT format.  Also HAL and Volume Manager mount the iPod better if you have the it hooked up while booting the system. Here's a page from Oreilly books '100 Indutrial-Strength Tips & Tools" for using an iPod with Linux.
[www.oreilly.com/catalog/linuxdeskhks/chapter/hack97.pdf](www.oreilly.com/catalog/linuxdeskhks/chapter/hack97.pdf)

---

### Post by sfabel on 2005-04-25
My 4th gen iPod is being mounted just fine, I can access it like a USB hard drive. However, I cannot delete anything I put on it, nor (now with Hoary) can I write to it. The error is always "read-only filesystem", although it is not mounted that way (I think?).

That's the output of mount:

```
/dev/sda2 on /media/IPOD VON ST type vfat (rw,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8 )
```
[SIZE=1](I inserted the space between 8 and the ) to keep the board from converting it into a smiley. It's not there in the output).[/SIZE]

It's kind of a mess. I've used the MP3 gain adjusment utility included with GTKpod and it seems to have messed up my M4A's that were on the iPod. Since there were a couple of other artefacts on it, I decided to "wipe it clean" and then just sync it again with my MP3 library on my PC.

I issued a "rm -rf" on the mounted partition, knowing the firmware would just create a new set of directories upon a reset. It started to erase the directories (Notes, Calendars, etc. were all deleted), but it stopped deleting when it came to the subdirectories of the "Music" folder (fXY). I opened Nautilus after several tries and out of frustration tried to delete the files there and voila - it seemed as if it really had deleted them! So I did a reset, the directories get re-created, everything seems fine until I notice the little directory: ".Trash-stephan" which had all the "deleted" files in it... *sigh* to make a long story short, I ended up with an iPod that has several songs in it's (my) Trash, I can't delete it as it tells me it is a "read-only" filesystem, but it has 7 gigs of space wasted in that folder.

Can ANYONE tell me what the &!%$ went wrong with Hoary? Everything worked just fine when I used Warty but it seems that Hoary is very unstable compared to Warty. I've had a couple of issues, starting with sound, ending with the iPod and seriously thinking about switching back to Warty.

*frustration*

Okay, where's the little switch that lets me delete something from the iPod?  :???: 

Thanks a lot,

Stephan

---

### Post by kjerstib on 2005-04-25
[QUOTE=sfabel]

Can ANYONE tell me what the &!%$ went wrong with Hoary? Everything worked just fine when I used Warty but it seems that Hoary is very unstable compared to Warty. I've had a couple of issues, starting with sound, ending with the iPod and seriously thinking about switching back to Warty.

*frustration*

Okay, where's the little switch that lets me delete something from the iPod?  :???: 

Thanks a lot,

Stephan[/QUOTE]

Donæt know if I can tell you what went wrong, but I've had a similar problem. Somehow I've managed to corrupt (perhaps the iTunesDB?) and the songs, although on the disk, aren't recognized anywhere. I did a complete restore on a win-box to fix it. 

However, I still have problems with getting ipod/gtkpod to work under ubuntu. I'm still uncertain whether to let hal do the mounting or whether to add a mount command in /etc/fstab, people seem to have differing opinions. 

At the moment, with mount defined in /etc/fstab, the ipod is recognized and mounted when I plug it in, but when I try to import the iTunesDB, I get this error message: ```
Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.
``` 

If I try to synchronize, I get this message: 
```
You did not import the existing iTunesDB. This is most likely incorrect and will result in the loss of the existing database.

Press 'OK' if you want to proceed anyhow or 'Cancel' to abort. If you cancel, you can import the existing database before calling this function again.
```

I would really like to get gtkpod to work, and as some people get it to work, I can't see why I shouldn't? 

So, anyone has any tips?

Kjersti

---

### Post by johndoe on 2005-04-28
[QUOTE=kjerstib]
[...]
At the moment, with mount defined in /etc/fstab, the ipod is recognized and mounted when I plug it in, but when I try to import the iTunesDB, I get this error message: ```
Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.
``` 

If I try to synchronize, I get this message: 
```
You did not import the existing iTunesDB. This is most likely incorrect and will result in the loss of the existing database.

Press 'OK' if you want to proceed anyhow or 'Cancel' to abort. If you cancel, you can import the existing database before calling this function again.
```

I would really like to get gtkpod to work, and as some people get it to work, I can't see why I shouldn't? 

So, anyone has any tips?

Kjersti[/QUOTE]

Go to a shell window, and do this ..

```

johndoe@b0rked:~ $ mount | grep -i media
/dev/hdc on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=moondust)
/dev/sda2 on /media/IPOD type vfat (rw,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077)

```

The "/dev/sda2 on /media/IPOD type vfat [...]" line indicates where the iPod gets mounted. (If you don't have that.. you have a different problem.) Go to gtkpod -> edit -> edit preferences-> ipod mount point and fill in the /media/IPOD or wherever it's mounted.

The iTunesDB file is simply a file that gtkpod has to be able to find. Test it like this:

```

johndoe@b0rked:~ $ ls -l /media/IPOD/iPod_Control/iTunes/iTunesDB
-rwx------  1 johndoe johndoe 425914 2005-04-28 14:28 /media/IPOD/iPod_Control/iTunes/iTunesDB

```

Make sure you don't blindly copy this! The /media/IPOD part should be whatever it is on your system! The -rwx------ line should be the same with your username instead of 'johndoe'... Good luck!

---

### Post by Rlink on 2005-05-12
[QUOTE=kjerstib]Donæt know if I can tell you what went wrong, but I've had a similar problem. Somehow I've managed to corrupt (perhaps the iTunesDB?) and the songs, although on the disk, aren't recognized anywhere. I did a complete restore on a win-box to fix it. 

However, I still have problems with getting ipod/gtkpod to work under ubuntu. I'm still uncertain whether to let hal do the mounting or whether to add a mount command in /etc/fstab, people seem to have differing opinions. 

At the moment, with mount defined in /etc/fstab, the ipod is recognized and mounted when I plug it in, but when I try to import the iTunesDB, I get this error message: ```
Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.
``` 

If I try to synchronize, I get this message: 
```
You did not import the existing iTunesDB. This is most likely incorrect and will result in the loss of the existing database.

Press 'OK' if you want to proceed anyhow or 'Cancel' to abort. If you cancel, you can import the existing database before calling this function again.
```

I would really like to get gtkpod to work, and as some people get it to work, I can't see why I shouldn't? 

So, anyone has any tips?

Kjersti[/QUOTE]


I had the same problem, it actually turned out that my /home/user/.gtkpod directory was owned by root and therefore locked. The reason it was giving the error wasn't because it couldn't read the file from the ipod, it just wasn't able to store it anywhere because the directory on your hard drive couldn't be written to. 
Just do a 
```

chown user:user home/user/.gtkpod 

```
and it should straighten everything out.

---

### Post by angkor on 2005-05-12
I have a 4g 20G Ipod and used this howto to get it to work with Debian Sarge and now Hoary. I use an USB-2 cable.

It works like a charm on both distros, so maybe you guys have some luck with it as well.

[http://www.linux-sxs.org/non_pc/iPod.html](http://www.linux-sxs.org/non_pc/iPod.html)

I use 'sudo gtkpod' cause otherwise I don't have permission to write the ItunesDB. And I skip the unmounting /dev/sda part cause it's never given me any trouble to pull the ipod free when it is unmounted.

---

