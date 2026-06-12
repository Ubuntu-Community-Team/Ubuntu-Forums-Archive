---
title: "Lsblk &amp; gparted recognize a USB SSD, the Gnome Disks utility does not."
date: 2023-08-10
forum: General Help
---

### Post by randompoint on 2023-08-10
I'm running a full version of 22.04.3 LTS from a persistent USB stick.  It works perfectly with the exception of disk detection.  Lsblk & Gparted see my USB SSD as sdb.  It doesn't show up at all in the Gnome Disks utility.  It also doesn't show up in Clonezilla.  Can anyone shed any light on the differences in device detection between Gparted and the Gnome Disks utility or how to address this problem?  Thanks.

---

### Post by TheFu on 2023-08-11
udisks2 being used by the Gnome stuff.  

Perhaps the USB driver is the issue?  I think there are 3 different drivers and they all suck, just in different ways. If you can, use SATA or eSATA connections instead.  USB storage is for backups, not primary storage.

I don't know about clonezilla.  I use ddrescue to copy a partition or whole storage device, which is very, very, seldom.  Image-based tools aren't for backups. They are for data recovery.

I've learned these things over decades as an admin.  My primary job is to avoid issues, not fix them.  If I didn't avoid a problem, then I've failed.

---

### Post by #&amp;thj^% on 2023-08-11
> **randompoint said:**
> I'm running a full version of 22.04.3 LTS from a persistent USB stick.  It works perfectly with the exception of disk detection.  Lsblk & Gparted see my USB SSD as sdb.  It doesn't show up at all in the Gnome Disks utility.  It also doesn't show up in Clonezilla.  Can anyone shed any light on the differences in device detection between Gparted and the Gnome Disks utility or how to address this problem?  Thanks.
One other possible, lsblk is rather high level. Check dmesg to see if Linux had trouble detecting the disk. But yes, a malfunctioning device may appear absent with other tools you have used.

---

### Post by VMC on 2023-08-11
I'm surprised it doesn't show up on Clonezilla. Gnome sucks at times when I plug in external usb device. Then I either use mount or restart. My KDE doesn't seem to have that issue. I've thought of trying to restart udisks2 somehow.

---

### Post by #&amp;thj^% on 2023-08-11
> **VMC said:**
>  I've thought of trying to restart udisks2 somehow.
This I just don't trust:
```
systemctl restart udisks2 

```
So I use this method instead:
```
systemctl stop --now udisks2 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> systemctl status udisks2 
&#9675; udisks2.service - Disk Manager
     Loaded: loaded (/lib/systemd/system/udisks2.service; enabled; preset: enab>
     Active: inactive (dead) since Fri 2023-08-11 10:05:52 MDT; 21s ago
   Duration: 50min 7.711s
       Docs: man:udisks(8)
    Process: 1223 ExecStart=/usr/libexec/udisks2/udisksd (code=exited, status=0>
   Main PID: 1223 (code=exited, status=0/SUCCESS)
        CPU: 140ms

```
And 
```
systemctl start --now udisks2 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> systemctl status udisks2 
&#9679; udisks2.service - Disk Manager
     Loaded: loaded (/lib/systemd/system/udisks2.service; enabled; preset: enab>
     Active: active (running) since Fri 2023-08-11 10:07:23 MDT; 5s ago
       Docs: man:udisks(8)
   Main PID: 72545 (udisksd)
      Tasks: 7 (limit: 18737)
     Memory: 4.6M
        CPU: 168ms
     CGroup: /system.slice/udisks2.service
             &#9492;&#9472;72545 /usr/libexec/udisks2/udisksd

```
Second check if necessary
```
systemctl list-units --type=service | grep udisks2
  udisks2.service                                        loaded active running Disk Manager

``` 
There is also "udisksctl"
```
udisksctl --help
Unknown command `--help'
Usage:
  udisksctl COMMAND

Commands:
  help            Shows this information
  info            Shows information about an object
  dump            Shows information about all objects
  status          Shows high-level status
  monitor         Monitor changes to objects
  mount           Mount a filesystem
  unmount         Unmount a filesystem
  unlock          Unlock an encrypted device
  lock            Lock an encrypted device
  loop-setup      Set-up a loop device
  loop-delete     Delete a loop device
  power-off       Safely power off a drive
  smart-simulate  Set SMART data for a drive

Use "udisksctl COMMAND --help" to get help on each command.


```

---

### Post by MAFoElffen on 2023-08-11
In your first post, you said USB stick, but you also refer to it as a USB SSD... There have been some "fakes" lately bought by members, that have had problems in how they show up in Gnome Disks, so that has my curiosity perked.

What is the ouput of:
```

sudo smartctl --all /dev/sdb | head -n20

```
(You said it shows up on your system as /dev/sdb...)

---

### Post by VMC on 2023-08-11
> **1fallen said:**
> This I just don't trust:
```
systemctl restart udisks2 

```
So I use this method instead:
```
systemctl stop --now udisks2 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> systemctl status udisks2 
&#9675; udisks2.service - Disk Manager
     Loaded: loaded (/lib/systemd/system/udisks2.service; enabled; preset: enab>
     Active: inactive (dead) since Fri 2023-08-11 10:05:52 MDT; 21s ago
   Duration: 50min 7.711s
       Docs: man:udisks(8)
    Process: 1223 ExecStart=/usr/libexec/udisks2/udisksd (code=exited, status=0>
   Main PID: 1223 (code=exited, status=0/SUCCESS)
        CPU: 140ms

```
And 
```
systemctl start --now udisks2 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> systemctl status udisks2 
&#9679; udisks2.service - Disk Manager
     Loaded: loaded (/lib/systemd/system/udisks2.service; enabled; preset: enab>
     Active: active (running) since Fri 2023-08-11 10:07:23 MDT; 5s ago
       Docs: man:udisks(8)
   Main PID: 72545 (udisksd)
      Tasks: 7 (limit: 18737)
     Memory: 4.6M
        CPU: 168ms
     CGroup: /system.slice/udisks2.service
             &#9492;&#9472;72545 /usr/libexec/udisks2/udisksd

```
Second check if necessary
```
systemctl list-units --type=service | grep udisks2
  udisks2.service                                        loaded active running Disk Manager

``` 
There is also "udisksctl"
```
udisksctl --help
Unknown command `--help'
Usage:
  udisksctl COMMAND

Commands:
  help            Shows this information
  info            Shows information about an object
  dump            Shows information about all objects
  status          Shows high-level status
  monitor         Monitor changes to objects
  mount           Mount a filesystem
  unmount         Unmount a filesystem
  unlock          Unlock an encrypted device
  lock            Lock an encrypted device
  loop-setup      Set-up a loop device
  loop-delete     Delete a loop device
  power-off       Safely power off a drive
  smart-simulate  Set SMART data for a drive

Use "udisksctl COMMAND --help" to get help on each command.


```

Thank you! I'll try it next time plug-it-in usb doesn't work.

---

### Post by TheFu on 2023-08-12
I moved a SATA SSD into a USB enclosure for SATA SSDs a few months ago after it was working years in a system here as the OS/boot storage.  Laid down GPT, setup LVM on it and it worked fine, but only in Linux.  As a portable device, LVM was a little too much hassle for my needs, so I wiped LVM, created a single partition, formatted it with NTFS and tried to use it connected to some video recording equipment. 
It didn't work.  Wiped GPT and put an MSDOS/MBR onto the disk, created an NTFS partition and tried again.  That worked. The video equipment didn't like GPT.  It also only works with either NTFS or FAT32, nothing else. No exFAT.

Not that this has anything to do with the OPs situation, but sometimes the partitioning type matters.  We've all been told that GPT creates a backup MBR so older systems can use the storage. Guess that isn't true for everything.  For a computer that doesn't support GPT, I'd look for a BIOS/firmware update.  For my video device, no updates exists.

---

### Post by randompoint on 2023-08-12
> **MAFoElffen said:**
> In your first post, you said USB stick, but you also refer to it as a USB SSD... There have been some "fakes" lately bought by members, that have had problems in how they show up in Gnome Disks, so that has my curiosity perked.  What is the ouput of: ```
 sudo smartctl --all /dev/sdb | head -n20 
``` (You said it shows up on your system as /dev/sdb...)  It's a Samsung USB SSD bought from Amazon and it's specifically a detection problem when running Ubuntu from my Live USB.  If Mint is booted from the internal SSD on the same computer the Gnome Disks utility it does detect the drive.

---

### Post by randompoint on 2023-08-12
> **1fallen said:**
> One other possible, lsblk is rather high level. Check dmesg to see if Linux had trouble detecting the disk. But yes, a malfunctioning device may appear absent with other tools you have used.  The drive works when manually mounted from within Clonezilla.  It also works when booting Linux Mint 21.1 from another SSD on the same computer, in fact the only problem I'm having is the detection of the SSD in Ubuntu.

---

### Post by randompoint on 2023-08-12
> **VMC said:**
> Gnome sucks at times when I plug in external usb device. Then I either use mount or restart.  It didn't occur to me that it could be a Gnome issue, but that make sense.  Will load the Cinnamon desktop and see if that makes a difference.

---

### Post by #&amp;thj^% on 2023-08-12
Well there is this quote from a forum member Morbius1 "Just say No to Disks".
Ahh come on that at least got a smile...;)

---

### Post by MAFoElffen on 2023-08-12
=d>=d>=d>=d>=d>

---

### Post by TheFu on 2023-08-12
> **1fallen said:**
> Well there is this quote from a forum member Morbius1 "Just say No to Disks".
Ahh come on that at least got a smile...;)

 +1

When I say "gnome", I'm really grouping everything built with GTK+ libraries.  I think Cinnamon is built with older versions of GTK+.

BTW, you realize that the installation ISO and a fully installed Ubuntu have different drivers, right?   Sometimes the installer has newer drivers and sometimes it is missing drivers completely.  There are lots of people who boot into a "Try Ubuntu" environment have sound, wifi, ethernet, touchpad all work.  They do an install, then find that wifi doesn't work ... because the drivers for their wifi are part of the installation run-time environment, but not part of the installed wifi drivers.

I suppose the same happens with disks.  For example, Linux really wants us to use ACPI and never use RAID as the SATA connection mode.  With USB, there are a number of different drivers. I don't know how they are selected, just that some work better than others.  I also know that USB storage connected all the time can vibrate loose.  Just a few days ago, a disk connected via USB became unavailable.  It been about a decade since the last time I saw this.  Ended up removing and re-connecting the USB plug after a reboot didn't fix it.  Just glad that I use autofs for all USB and network storage.

---

### Post by MAFoElffen on 2023-08-12
Yes. +1.

Over the years, I found that constantly plugging-unplugging devices directly into my USB ports, wears them out. For my workstation and servers, I buy 6" USB extension cords, which I leave plugged into my machines, and plug my devices into them. Easier and cheaper to let them wear out / easier to replace, and protects the investment in my hardware. 

I think a set of six is still less than $10 on Amazon.

I learn from my mistakes. LOL

---

### Post by TheFu on 2023-08-12
I use 6' extensions.  6" was never enough to reach around the back.

Have an SSD USB3-c with a 6" connector. Because the system it gets connected into is about 4inches off the ground on a bread rack with carpet to keep the vibration noise down, it just dangles without bottom support (for now).  I need another 6ft USB3 10Gbps cable to clip to my desk for each access.

How is it that a full day happens, but seems like I did nothing?

---

### Post by #&amp;thj^% on 2023-08-12
> **MAFoElffen said:**
> 
Over the years, I found that constantly plugging-unplugging devices directly into my USB ports, wears them out. For my workstation and servers, I buy 6" USB extension cords, which I leave plugged into my machines, and plug my devices into them. Easier and cheaper to let them wear out / easier to replace, and protects the investment in my hardware. 

I think a set of six is still less than $10 on Amazon.

I learn from my mistakes. LOL

+2
Great Minds! lol

---

### Post by MAFoElffen on 2023-08-12
LOL. I also have 6' extensions to things I want to "convenient", or to reach further.

My old workstation server-class motherboard had two USB-A ports on the motherboard, which I plugged 6' cords into so I could get access to them outside the case, and actually be used... LOL

We all probably overlook those kinds of tips, because they are just there and just common place to "us" now, so we don't think to share them.

I have a very old server tower case, which, every once in a while, I think about replacing. Each time I do, I can't find a case laid out as well as the old one. It has been hard to let go of that case. Besides, that is my cat's favorite place to lay down and watch me work. LOL

---

### Post by randompoint on 2023-08-13
> **MAFoElffen said:**
> Yes. +1.  Over the years, I found that constantly plugging-unplugging devices directly into my USB ports, wears them out. For my workstation and servers, I buy 6" USB extension cords, which I leave plugged into my machines, and plug my devices into them. Easier and cheaper to let them wear out / easier to replace, and protects the investment in my hardware.   I think a set of six is still less than $10 on Amazon.  I learn from my mistakes. LOL  I've found that picking up a laptop or phone up when the cord is caught on something, or just tripping on it causes causes way more damage to my stuff than wear.  A 6" extension cable plugged in between the main charging cable and the device works as a strain relief.  That way when I trip over the cord (and that's something that eventually will happen) the cables pull apart before damage is done.  Saved many dollars on repairs doing that.

---

### Post by TheFu on 2023-08-13
> **randompoint said:**
> I've found that picking up a laptop or phone up when the cord is caught on something, or just tripping on it causes causes way more damage to my stuff than wear.  A 6" extension cable plugged in between the main charging cable and the device works as a strain relief.  That way when I trip over the cord (and that's something that eventually will happen) the cables pull apart before damage is done.  Saved many dollars on repairs doing that.

If you are tripping over a cord, perhaps your setup needs modification?  My cords connect in the back and come to the front where they are binder-clipped to either a higher rack/shelf or to the desk.  They are nowhere near where anyone would walk. Here's 110 pcs for $6 with amazon code B09241ZST4.  They are very useful for cable management.

Or you can buy some velcro strips to use like tie-wraps, just reusable and softer. These work well if there's something to tie around. I need to clean up the cables behind my rack.  Had to replace a 15 yr old UPS recently.  Velcro Cable Ties are excellent for this purpose.  150 for $11. B09RKGXHPM  8 inch long.  These are useful for cord management around the house. Even those huge orange outdoor extension cords - just use 2 cable ties together to make a longer table tie.  I need to find the roll I already have here ... somewhere. I do have some other velcro things - but that item number is the best for cable management.  You can probably use 50 of them now. Give the other 100 away to family and friends so they don't go to waste. Same with the binder-clips.

There are lots of youtube videos on stuff like this, if you need to see how to use them.

---

### Post by VMC on 2023-08-13
> **1fallen said:**
> This I just don't trust:
```
systemctl restart udisks2 

```
So I use this method instead:
```
systemctl stop --now udisks2 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> systemctl status udisks2 
&#9675; udisks2.service - Disk Manager
     Loaded: loaded (/lib/systemd/system/udisks2.service; enabled; preset: enab>
     Active: inactive (dead) since Fri 2023-08-11 10:05:52 MDT; 21s ago
   Duration: 50min 7.711s
       Docs: man:udisks(8)
    Process: 1223 ExecStart=/usr/libexec/udisks2/udisksd (code=exited, status=0>
   Main PID: 1223 (code=exited, status=0/SUCCESS)
        CPU: 140ms

```
And 
```
systemctl start --now udisks2 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> systemctl status udisks2 
&#9679; udisks2.service - Disk Manager
     Loaded: loaded (/lib/systemd/system/udisks2.service; enabled; preset: enab>
     Active: active (running) since Fri 2023-08-11 10:07:23 MDT; 5s ago
       Docs: man:udisks(8)
   Main PID: 72545 (udisksd)
      Tasks: 7 (limit: 18737)
     Memory: 4.6M
        CPU: 168ms
     CGroup: /system.slice/udisks2.service
             &#9492;&#9472;72545 /usr/libexec/udisks2/udisksd

```
Second check if necessary
```
systemctl list-units --type=service | grep udisks2
  udisks2.service                                        loaded active running Disk Manager

``` 
There is also "udisksctl"
```
udisksctl --help
Unknown command `--help'
Usage:
  udisksctl COMMAND

Commands:
  help            Shows this information
  info            Shows information about an object
  dump            Shows information about all objects
  status          Shows high-level status
  monitor         Monitor changes to objects
  mount           Mount a filesystem
  unmount         Unmount a filesystem
  unlock          Unlock an encrypted device
  lock            Lock an encrypted device
  loop-setup      Set-up a loop device
  loop-delete     Delete a loop device
  power-off       Safely power off a drive
  smart-simulate  Set SMART data for a drive

Use "udisksctl COMMAND --help" to get help on each command.


```

I finally got a usb HD to fail to mount. Trying the above procedure failed. lsblk -f revealed that indeed it was seen, just Gnome failed to mount it. A logout fixed it. I would have thought the udisks2 commands would work.

---

### Post by #&amp;thj^% on 2023-08-13
> **VMC said:**
> I finally got a usb HD to fail to mount. Trying the above procedure failed. lsblk -f revealed that indeed it was seen, just Gnome failed to mount it. A logout fixed it. I would have thought the udisks2 commands would work.
D-bus come into play on some systems so maybe something like:
```
udisksctl mount --block-device /dev/sdc1
Mounted /dev/sdc1 at /media/me/1TB-BU

```
Amend "sdc1" for that drive.
```
udisksctl mount --block-device /dev/nvme1n1p1
Mounted /dev/nvme1n1p1 at /media/me/2F61-1171

```
All this just makes me appreciate my simple XFCE4 DE.
Seems the old Gnome story lives on, fix one thing break another, and related to the GUI aspect of gnome, it seems all your CLI works.
To the OP, sorry for all this noise, but there is some very useful information here.

---

### Post by randompoint on 2023-08-13
> **TheFu said:**
> If you are tripping over a cord, perhaps your setup needs modification?  My cords connect in the back and come to the front where they are binder-clipped to either a higher rack/shelf or to the desk.  They are nowhere near where anyone would walk. Here's 110 pcs for $6 with amazon code B09241ZST4.  They are very useful for cable management.  Or you can buy some velcro strips to use like tie-wraps, just reusable and softer. These work well if there's something to tie around. I need to clean up the cables behind my rack.  Had to replace a 15 yr old UPS recently.  Velcro Cable Ties are excellent for this purpose.  150 for $11. B09RKGXHPM  8 inch long.  These are useful for cord management around the house. Even those huge orange outdoor extension cords - just use 2 cable ties together to make a longer table tie.  I need to find the roll I already have here ... somewhere. I do have some other velcro things - but that item number is the best for cable management.  You can probably use 50 of them now. Give the other 100 away to family and friends so they don't go to waste. Same with the binder-clips.  There are lots of youtube videos on stuff like this, if you need to see how to use them.  My desktop computer and server has the cables routed so they're completely out of the way.  This problem occurs with laptop computers and phones.

---

