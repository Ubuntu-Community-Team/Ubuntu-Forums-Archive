---
title: "Wiping write protected USB"
date: 2021-07-25
forum: General Help
---

### Post by Nina_W on 2021-07-25
I wanted to try Kubuntu on another PC (I've just upgraded to Ubunutu 20 on this one) and created a USB but couldn't get it to boot from it. I suspect the creation didn't quite work and so wanted to wipe it and try again but the USB is write protected. 
I spent ages looking up how to remove the write protection and lots of pages saying different ways, different things to install etc. all of them missing bits of what I need.

As I understand it I can use **chmod 666 /dev/xyz**   where xyz is the assignment of the device.

If I do a **lsusb** I get this for the device "Bus 002 Device 002: ID 0951:1666 Kingston Technology DataTraveler 100 G3/G4/SE9 G2" but I believe that doesn't have what I need but it does show the device is being seen. I believe I'm looking for either a sda or tty followed by usb but when I do an  **ls**  I'm getting lots of sdas and ttys but none of them referencing a USB.

So how do I find out the right thing I need to put in place of the xyz in the chmod command?

---

### Post by dragonfly41 on 2021-07-25
> [COLOR=#000000]but couldn't get it to boot from it. [/COLOR]

Perhaps you have not set boot flags (as just one thought).
I would inspect the drive using gparted.
In fact, by coincidence, I am about to refresh an old USB drive to hold a fresh download of Ubuntu 20.04 to install on an SSD (USB port) and I will be using gparted to setup.

---

### Post by mikewhatever on 2021-07-25
Why do you think it is write protected? Is there a switch/button to toggle on the USB stick?
The chmod command is used on files, and has nothing to do with write protection. No matter what mode is set on files, you should still be able to format the device, which is what is done, when an Ubuntu USB gets created.

---

### Post by Impavidus on 2021-07-25
Run **ls /dev**, then insert the usb drive, then run **ls /dev** again. Which device was added the second time? Probably sdb or sdc (if sdb already exists), along with something like sdb1 or sdb2, which are partitions on the usb drive.

Root should already have read and write access to the usb drive, other users shouldn't, so I don't expect you have to use chmod. Use sudo to write to the usb when wiping it clean or creating the live usb. Some usb drives have a physical switch to make then read-only. I haven't encountered any such drives recently, but they exist. In that case you have to move the switch.

---

### Post by TheFu on 2021-07-25
Not all USB flash drives are supported by every USB controller on every computer.  I have a number of USB flash drives with different Linux installers that work on 3 of my computers, but not the other 2.  Over the decades, I've looked for a pattern for which worked and which didn't. Never found one.

USB write protection is very uncommon.  If a device has it at all, then it is a hardware switch to be toggled, like on the SDHC cards with the slider.

Chmod won't make a USB device writable.  When creating a boot flash drive, the device much be unused, but still connected to the PC.  Systems that auto-access all connected storage will have issues with this.

When I'm creating a boot flash drive, I'll have 2 terminals.
a) **dmesg -w**
b) for other commands

Then I plug in the flash drive to be wiped.  When the OS sees it, the dmesg window will show the device name. There are a few lines to see, all related to /dev/sd ..... something.  Suppose the dmesg shows /dev/sdh and partitions sdh1 and sdh2.  We'll use that for commands below. What you see will most likely be different.

Next, I use the "cp" command in the "b" terminal
```
sudo cp /path/to/ubuntu-xxx-yyy.iso  /dev/sdh
```
Let that run. Should take 2-4 minutes.
Next type, **sync; sync; sync** into the "b" terminal.  By the time you type the 3rd one, all the disk buffers should have been flushed to the flash storage and it should be done.

When the command prompt comes back, it is done. I'd pull it out, wait 10 seconds, reinsert it.  Watch the "a" terminal with dmesg and see the connection and partitions.
If it gets auto connected, go into the GUI (file manager) and "Eject" the USB partitions.
It is ready for use.

While I used 'cp', any command that moves bits, unmolested, from a--->b can be used.  So, cat, more, less, dd, ddrescue, tee, can all be used.  Of course, you can use those specialty tools like unetbootin, rufus, etcher, whatever too, but they are just fancy tools to move bits from a--->b.

None of this can make a flash drive become magically compatible with a USB controller. Sorry.

I've never touched the partition types or boot flags on the flash storage. It isn't needed. The flags are contained in the ISO, already.

---

### Post by tea for one on 2021-07-25
[COLOR="#0000FF"]mkusb[/COLOR] is a very useful utility for creating bootable usb devices [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

It also includes features (among others) to:-
Restore to a standard storage device
Wipe a device

---

### Post by TheFu on 2021-07-25
+1 for mkusb.  

I've used it a few times for multi-boot with a little storage outside the ISO and "persistent" areas for data storage.  I think it was multi-boot, but don't quote me on that.  The guy behind it is active in these forums and has a long running thread with all the different releases and methods to use it.

Took me 3 attempts to get it to do what I wanted. I didn't understand the subtle terminology differences for the different choices available.  What I wanted was something that says
```
Persistent ext4 size = Xgb 
Persistent NTFS size = Ygb
Persistent exFAT size = Zgb
```
and let me specify the size for each.  

About a year ago, the menus were dumbed down for less technical people than me. I found it confusing/unclear for what would really be the outcome for each selection.

---

### Post by yancek on 2021-07-25
If you wrote an iso file of Kubuntu to the usb drive, it is read only and any time you mount it, you will get that message but you can still access it but not modify the contents.  If you want to use it for something else, create another flash drive to use for data or use it for another iso, use GParted and from the Device tab, create a new partition table.  What exactly are you doing when you get this message.

---

### Post by TheFu on 2021-07-25
yancek sees something that I had already moved passed.  ISO files are **ISO9660 standard** read-only images of a CDROM/DVD.  They are readonly and always will be. That's what an ISO is.  The file system is read-only, always. Can't be anything else. Read-only is the core nature of an ISO9660 standard.

To modify anything inside it there is a process called "re-mastering".  Re-mastering is the same as building it again.  There is a tool called mkisofs/genisoimage.  It has been a few decades since I created an ISO using any of these tools.

---

### Post by Nina_W on 2021-07-26
Many thanks for everyone who replied, I learned a lot that might be useful in the future even if I didn't use it this time around. I have re-done creating the bootable USB although not tried it yet, if it doesn't work I will look into TheFu's suggestion of using dmesg

QUOTE=dragonfly41;14050129]Perhaps you have not set boot flags (as just one thought).
I would inspect the drive using gparted.
In fact, by coincidence, I am about to refresh an old USB drive to hold a fresh download of Ubuntu 20.04 to install on an SSD (USB port) and I will be using gparted to setup.[/QUOTE]
I used the start-up disk creator from the Dash to create it so that should have taken care of the flags.

> **mikewhatever said:**
> Why do you think it is write protected? Is there a switch/button to toggle on the USB stick?
The chmod command is used on files, and has nothing to do with write protection. No matter what mode is set on files, you should still be able to format the device, which is what is done, when an Ubuntu USB gets created.
I'd thought I should be able to format regardless of protection (unless it was a hard lock) but it told me I didn't have access.

> **Impavidus said:**
> Run **ls /dev**, then insert the usb drive, then run **ls /dev** again. Which device was added the second time? Probably sdb or sdc (if sdb already exists), along with something like sdb1 or sdb2, which are partitions on the usb drive.

Root should already have read and write access to the usb drive, other users shouldn't, so I don't expect you have to use chmod. Use sudo to write to the usb when wiping it clean or creating the live usb. Some usb drives have a physical switch to make then read-only. I haven't encountered any such drives recently, but they exist. In that case you have to move the switch.
Yes, I finally opted for comparing the ls before and after I'd plugged it in, I was trying to avoid having the compare very long lists, but it had to be done.


> **tea for one said:**
> [COLOR=#0000FF]mkusb[/COLOR] is a very useful utility for creating bootable usb devices [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

It also includes features (among others) to:-
Restore to a standard storage device
Wipe a device
This looked like the most straightforward option so I went for this. Installed in linux and ran from Dash. It brings up a window asking for the source file first, then asking you for the destination, but has already found a likely looking USB and gives the sdb piece and the "Data Traveller" name so I'd no doubt it was the right one. It also has options to create a live/install one or a persistence one.

---

### Post by HermanAB on 2021-07-26
Going back to the original problem statement - Wiping a read-only USB widget:
It will will only show read-only after the file system was mounted and there are errors in the file system.
To wipe it, it must be unmounted.  However, a desktop system will automatically mount the device when it is plugged in, causing a Catch-22.

To wipe a widget, you got to Eject (umount) the device (on the right click menu), then you can create a new file system on it with gparted or similar.

The bootable Ubuntu CDROM images are also bootable USB images.  Therefore, to try Kubuntu, all you need to do is copy the CDROM image to the USB widget using a low level copy utility such as 'cat'.  You do need to know what you are doing when using a low level copy utility, otherwise you can erase or overwrite an important disk drive.  The mkusb utility prevents the most common mistakes in the copy process, so I second using that.  You don't need to delete the USB widget before you run mkusb, you just need to ensure that the widget is Ejected (umount).

---

