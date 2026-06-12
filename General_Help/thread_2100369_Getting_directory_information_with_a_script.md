---
title: "Getting directory information with a script"
date: 2013-01-01
forum: General Help
---

### Post by ncwalker2010 on 2013-01-01
First - HAPPY NEW YEAR !!!

Second - the question(s):

I have written a small shell script to rsync my desktop to a few flash drives.  The folders I sync are dependent on the flash drive.  Right now, when I plug in the flash drive, it appears in "/media" with the name of the flash drive and the names are different for each of the flash drives.

The shell script works fine, but in truth, I have one for each flash drive and would like to combine them.  I have a handle on how to code the conditionals in the script, but where I am lost is determining which flash drive was plugged in.

Question 1:  How would I go about looking at which flash drive was plugged in automatically?  I envision using the "ls" command on "/media" but don't know how to get the output of that back to the script in a variable.

Question 2:  How would I set up this master script to run every time a flash drive was plugged in?  I would like to be able to plug in a flash drive, have this action spawn the script, and the script check the identity of the drive and if it is one of my specials, then execute the rsync.

---

### Post by tgalati4 on 2013-01-01
Perhaps Block ID would work?

man blkid

tgalati4@Dell600m-mint14 ~/Desktop $ sudo blkid /dev/sda5
/dev/sda5: UUID="91b58024-da5a-4e16-889a-dc000942ecb0" TYPE="ext4" 

Plug in your flash drive:

sudo fdisk -l

Find out what device it is.  Then run blkid to get the UUID.  Use the UUID in a grep statement to satisfy your condition.  Post your script for others to enjoy.

Each flash drive that you use should have it's own user-unique ID number (UUID) that you can use to identify the drive regardless of how it's plugged into the system.

A simpler method would be to use gparted and put unique labels on each flash drive.  The drives should then mount under /media/label.  I think you are limited to 8 characters.

---

### Post by Cheesemill on 2013-01-01
The best way to do this is with custom udev rules.

Udev is responsible for mounting removable drives when they are plugged in, by writng custom udev rules you can automatically launch a script whenever a specific device is inserted.

Take a look at this thread:
[http://ubuntuforums.org/showthread.php?p=10259447](http://ubuntuforums.org/showthread.php?p=10259447)

Also Googling for 'custom udev rules' should give you a good place to start.

---

### Post by wazntme on 2013-01-01
Google "Running a script on usb insertion"

You will find somw udev rules and scripts.

---

### Post by ncwalker2010 on 2013-01-01
At Cheesemill - WOW.  Lots of information there.  But beyond my skill level, currently.  Also, it "reads" like when you write a udev rule that executes a script, you cannot get any feedback that anything is happening.  I'm sort of thinking I would like to plug in the USB, have it do it's thing, then pop me up a window that says "Sync of USB drive complete."  Which may mean I have to write some python code, then execute THAT.  But I'm really not sure.

At wasntme - OK, reading your links now.....

And thanks to you both.

---

### Post by ncwalker2010 on 2013-01-01
OK - I have the concept I think.  Excuse me if I don't have all the Linux terms right.  You set a trigger udev with a rule.  This thing monitors the devices, including the plugging and unplugging of USBs.

Key Point One:  It seems that whatever script you "fire" with your UDEV rule really needs to fire another one so you don't tie things up with the trigger script.  I get that conceptually.  Also, it is important to be able to identify your USB drive.  At least it is to me, because I only want this script to run on a couple of USB drives.  One for my music, that goes to my car audio system, and one for pictures.  If my son plugs in his USB drive, I don't want it to do anything.

And this is where I get stuck.....

This link seems to be the most informative (at least I understand it).

[https://help.ubuntu.com/community/UsbDriveDoSomethingHowto](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto)

And the author says run dmesg to determine if your USB drive is plugged in.  He does this and says "So our device is sda..."

Yeah.  HE may see that, I sure don't.  My dmesg output is HUGE.  And I cannot see a line in mine anywhere that is like the "Initializing USB Mass Storage Driver...." anywhere.

I have even redirected the dmesg output to two text files.  One with the USB plugged in, and one without.  And the length of the files is only two lines different.  (Looking through them now to find out where).

Now, lsusb seems MUCH better.  If I run this with the usb in and out I get:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
Bus 003 Device 002: ID 04f2:0760 Chicony Electronics Co., Ltd Acer KU-0760 Keyboard
```Where the Bus 003 Device 002 is my photo USB.  (The only line of output that changes as I plug and unplug the device.)

My question - is the ID unique?  It seems to be, if so, how do I use it next, because seriously - I can't figure out from the dmesg output what my usb is.

---

### Post by Cheesemill on 2013-01-01
Plug your USB device in then run the command:
```
sudo fdisk -l
```
This will list all of the drives connected to your system, if your post back with the results we can figure out which is your USB drive.

---

### Post by ncwalker2010 on 2013-01-01
OK.  Now I feel dumb.
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc4632d33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    36866047    18432000   27  Hidden NTFS WinRE
/dev/sda2   *    36866048    37070847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        37070848  1339123119   651026136    7  HPFS/NTFS/exFAT
/dev/sda4      1339123710  1953523711   307200001    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1339123712  1354747903     7812096   82  Linux swap / Solaris
/dev/sda6      1354749952  1953523711   299386880   83  Linux

Disk /dev/sdd: 8166 MB, 8166703104 bytes
256 heads, 63 sectors/track, 989 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          56    15950591     7975268    c  W95 FAT32 (LBA)
```It is sdd1 (all the sda stuff is partitions on the only hard drive I have, dual boot, Windows and Ubuntu 12.04)  Also, sdd1 goes away when I unmount the flash drive.

We are back moving again.

But man, the help on dmesg was lacking.  Also, the output was all listed as SYSFS stuff and mine all says ATTRS when I run dmesg.  Hold on for the next question....

---

### Post by Cheesemill on 2013-01-01
Don't worry about that, there's been a change in the  udev naming convention since that article was written.

Just use ATTRS{...} instead of SYSFS{...} in your udev rule so it's the same as the fields you want to match from the output of:
```
udevadm info -a -n /dev/sdd1 
```You've probably already come across this page but the definitive guide to udev rules can be found here:
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

### Post by ncwalker2010 on 2013-01-01
OK.  Now my curiosity is REALLY up on what this stuff that this command is producing:

```
udevadm info --attribute-walk -- name /dev/sdd1
```Below is the output.  NOTE:  it is LONG, so where I removed a bunch of stuff I replaced it with [[Deleted stuff in here]] and also my comments are in [[ ]], that is NOT output from udevadm.

```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/host33/target33:0:0/33:0:0:0/block/sdd/sdd1':
    KERNEL=="sdd1"
    SUBSYSTEM=="block"
    DRIVER==""
    [[Deleted stuff in here]]

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/host33/target33:0:0/33:0:0:0/block/sdd':
    KERNELS=="sdd"
    SUBSYSTEMS=="block"
    DRIVERS==""
    [[Deleted stuff in here]]

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/host33/target33:0:0/33:0:0:0':
    KERNELS=="33:0:0:0"
    SUBSYSTEMS=="scsi"  [[The website was looking for a section with "BUS==scsi" and "DRIVER==sd" so
                          I think this is the block that I want]]
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="PNY     "          [[Here is the vendor]]
    ATTRS{model}=="USB 2.0 FD      "   [[Here is the model]]
    ATTRS{rev}=="1100"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x2b8"
    ATTRS{iodone_cnt}=="0x2b8"
    ATTRS{ioerr_cnt}=="0x1"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/host33/target33:0:0':
    KERNELS=="target33:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/host33':
    KERNELS=="host33"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0':
    KERNELS=="1-4:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    [[Deleted stuff here]]

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-4':
    KERNELS=="1-4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="200mA"
    ATTRS{urbnum}=="1993"
    ATTRS{idVendor}=="154b"
    ATTRS{idProduct}=="005b"
    ATTRS{bcdDevice}=="1100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="16"
    ATTRS{devpath}=="4"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="PNY Technologies"
    ATTRS{product}=="USB 2.0 FD"
    ATTRS{serial}=="ACADHD1000004641"    [[But THIS looks like what I really want to use
                                           to identify the USB drive]]

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="343"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0302"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.2.0-35-generic-pae ehci_hcd"  [[This seems to indicate we have
                                                                  moved up the "tree to the OS level]]
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:02.1"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.1':
    KERNELS=="0000:00:02.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    [[Deleted stuff here]]

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```This looks like it starts real deep and gives you information, backing out as you go.  I am noticing that the KERNEL started with "SDD1" which I issued the command on...  then it drops the 1 for "SDD".  The next level out switches to "33:0:0:0" and that seems to be where I want my information for identifying my USB in udev.  Mainly because of the website above - the author is looking for BUS==scsi and DRIVERS==sd (but MY output calls it SUBSYSTEMS instead of BUS).

Here's the thing -- If I look at the vendor and model keys, they look rather generic.  So if I keep coming up the tree a few more levels, I find ATTRS{serial} which just seems to be a more unique identifier to use.

Still plugging away....

---

### Post by oldfred on 2013-01-01
I still like labels.
sudo blkid -c /dev/null -o list

Snipped to just show my flash drives. One just has Raring as an install flash drive and the other is formatted and has 3 partitions. sys will become a full install and data just data.

```
/dev/sdb1  vfat    RARING   /media/RARING  D84B-95A6
/dev/sdf1  vfat    EFI32    (not mounted)  2404-8A43
/dev/sdf3  ext4    sys      /media/sys     e2156d09-329e-4262-9549-f72a05d97f93
/dev/sdf4  ext4    data     /media/data    b1b11cef-6fc6-4cd8-8343-e7c1852de805

```

---

### Post by ncwalker2010 on 2013-01-01
OK.  I am stuck now.  :-(

I have created the file 99-plugspecificdevice-usb.rules out in /etc/udev/rules.d and the contents of this file are:

```
# This file sets the autorun rules for SPECIFIC USB Flash Drives when they are plugged in.
# See udev(7) for syntax.
#

# Searches for the Phillips USB
ACTION=="add", ATTRS{serial}=="ACADHD1000004641", RUN+="/usr/local/bin/launch_phillips_sync.sh"

# Serches for the Sheila USB
ACTION=="add", ATTRS{serial}=="0572311B525277BD", RUN+="/usr/local/bin/launch_sheila_sync.sh"
```I made it by cut/pasting one of the other in there and editing it and the permissions are identical to the other files in the directory.  I got the serial attribute from udevadm and I know that is correct.  I am trying to test the Sheila USB (the second one.

So in /usr/loca/bin i have that launcher script.  The contents of it are:

```

#!/bin/bash

DEBUG=1

if [ "$DEBUG" = 1 ]; then

if [ "${ACTION}" = "add" ] && [ -f "${DEVICE}" ]
then
# Write a message to the log file
    echo "Successfully mounted" & ${DEVICE} >> ~/bin/logs/plugspecificdevice.log
fi

else

fi

```Now at this point, I am just trying to determine if my udev rule is firing.  So I got this code from one of the links and my expectation is it should be making a file in my home directory of /bin/logs that says it successfully mounted the device.  But I'm not sure if the syntax is right in THIS script.

---

### Post by ncwalker2010 on 2013-01-01
And my following thoughts..... (been piddling around).

I took all the extra stuff in my "debug" script out just to see if I could write a file upon execution.  No dice.  Meaning I simplified my "launcher script" to essentially

```

#!/bin/bash

echo "Successfully mounted" >> ~/bin/logs/plugspecificdevice.log

```I figured I just needed to know if the udev code was firing.

Then I redid the rules to simply be:

```

ACTION=="add", SUBSYSTEMS=="usb", RUN+="/usr/local/bin/launch_sheila_sync.sh"

```Thinking shis should trigger my script if I plug any USB anything into it.  Nada....

One thing, all the links say when I change these rules I need to issue:

```
udevcontrol reload_rules
```but mine (Ubuntu 12.04) doesn't like that.  It DOES like:

```
sudo udevadm control --reload-rules
```I also tried a hard boot for grins.  Still, nothing is working.

Now - when I DO stick the drive in, Ubuntu is opening up a browser with Nautilus, like to display what is on the drive.  Could THAT be interrupting my interrupt?  I mean, that fires and udev manager, or whatever, stops checking for more rules?

---

### Post by steeldriver on 2013-01-01
a couple of things:

1. the script will be run by root so ~/ is probably not going to cut it as a path for your log file (at least, it will be /root if it expands at all). Personally I find it useful to use 'logger' e.g.

```
#!/bin/bash

logger "$0: successfully mounted" 
```which will write to /var/log/syslog

2. check that the script runs from the command line and writes to syslog!

3. if you're in doubt about the rule getting reloaded, try

```
sudo service udev restart
```

---

### Post by tgalati4 on 2013-01-01
Normally udev rules would be the way to handle this, but I think a simple script run by the user which runs blkid for identification will allow the user control to perform backups as required.  With udev rules, you must somehow wrestle away root priviledge for performing user home directory backups.

---

### Post by ncwalker2010 on 2013-01-01
ARRRGHHH.

So I was seeing "logger" in the examples and thinking to myself that I would play it safe and only mess around in my home folder.

Not understanding that it would execute as root.....

It was working the whole time (now that I know how to test the output).

So I have my launcher script working, now I just need to execute the backup script properly.  In testing that, I realized I CAN execute that one with "echo" and the ouput to a local file.  But it seems to be executing twice....

One step closer....

---

### Post by ncwalker2010 on 2013-01-01
OK.  I got her working.  This is basically what happens:

1) I stick in the specific usb and the udev rule sees this has occurred.  It fires my "launcher" script.

2) The launcher script fires my actual synchronization script.  Because all the help files said I really should exit the udev initiates script quickly.  OK.  I will believe that without question, and that's what I did.

3) The synchronization script runs the rsync command which does what I want it to do.

Now - more questions....

I have tried to show some kind of feedback that all this is going on.  And looked at zenity.  It would be REALLY nice to know this, because you don't really know when it is OK to pull out the flash drive.  (My manual way ran in a terminal, you could SEE when it was done.  I am thinking that because "root" is running the launcher script, it is then running the actual synchronization script.  Is there any way to get this visible to the user?

---

### Post by steeldriver on 2013-01-01
there's another active thread at the moment about using zenity for udev notifications - searching thread titles for 'zenity' should find it

---

### Post by ncwalker2010 on 2013-01-02
Well I found it.

Yeek.

This is all echelons above my programming skill.....

---

