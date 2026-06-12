---
title: "How can the computer run so slowly???"
date: 2023-06-13
forum: General Help
---

### Post by groston on 2023-06-13
I recently had an Ubuntu experience that I simply cannot explain.

I need a Linux system to accomplish a task, so I decided to build Ubuntu on a USB drive. To do this, I downloaded Rufus, V3.22 (the newest that will run on my 10+ year old Windows 7 Machine) and ubuntu-22.04.2-desktop-amd64.iso. When I ran rufus, I selected MBR as the partition scheme, BIOS (or UEFI-CSM) as the target system, FAT32 as the file system, and I made the Persistent partition size 8 GB (on a 32 GB drive). I then clicked Start and rufus did its thing.

The first time I  booted into Ubuntu, the activity light on the USB drive was flashing quite a bit. I tried doing some simple stuff, but the system was taking forever to respond. So, I shut it down and reran rufus.

The second time I booted into Ubuntu, I walked away from the computer for 8+ hours and when I came back, the activity light on the USB drive was not flashing. I tried running Firefox, but it did not work. A search and suggested that I run these two commands: sudo apt update and sudo apt upgrade. The first command executed quickly and the second one downloaded 275+ updates. The download didn’t take much time, but the installation… After installing for 7+ hours, during which I did not once touch the machine, the progress bar indicated 43% complete. I cannot begin to fathom how a computer can be so slow.

When I typed sudo reboot –h now, after 10 minutes that computer had not yet rebooted, to I hit the reset button.

Ubuntu is a good OS, but what the heck happened to me????

---

### Post by TheFu on 2023-06-13
I think Rufus has been having issues, the last few years and running it on Win7 will likely cause other issues.  Most people new to Linux are recommended to use **Etcher**.
Nerds like me use '**cp**', but any program that will move bits from A ---> B unmolested can be used.  I haven't used Windows to create a boot flash drive in about 15 yrs.  Windows is just too hard to use.

Using Rufus as the basis would be a bad choice, IMHO. Etcher.

If Ubuntu takes more than 15 seconds to boot, you have a bad flash drive or a bad/incompatible USB port or both. Something isn't right.

All the other complaints aren't helpful without spelling out the system hardware.  I've seen Core i7 systems brought to their knees from bad BIOS settings.  I've also seen Atom CPUs fly.  RAM matters and the performance of the USB device does too, if you are using it.  Always use the fastest USB you can, USB3.2 10Gbps would be best, USB3 is the minimum for an ok desktop experience, assuming the flash drive isn't a cheapo, freebie, they give away.  USB2 is fine for emergencies, but not running the OS.  If you really want performance and are stuck with USB3+ to connect the storage, get a USB-2-SATA (or NVMe) and install a $20-$40 SSD into the enclosure and use that.

However, typically, any computer that came with Win7 shouldn't be running the flagship DE that comes with the default Ubuntu desktop.  Try a lighter flavor, say XUbuntu or Ubuntu-Mate.

Anyway, if you'll use Etcher to create the boot flash drive and use a light Ubuntu flavor, then run **inxi -bz** and post the output here wrapped in forum code tags (Advanced editor (#) button, then we'll be able to see what you have and which drivers have been selected, which can tell us much.  Nothing sensitive will be in that output.

Ubuntu Desktop (running Gnome) is a lesson in how to make a really fast computer deal with bloat, I'm sorry to say.

---

### Post by MAFoElffen on 2023-06-13
A few things... Booting a "persistent" Live Image Environment (L.I.E.) takes a while. 

USB Flash drives, the speed varies widely from USB2.0 and USB3.X... Then even with USB3.2 Flash drives, shop around for one that's read and write speeds are as high as you can find. Pay attention to those. Why? Because the LIE is a compressed image that has to expand for use, so all parts of it has to be read to do that, while it is in the boot process.

On USB Flash drives, if I intend to run a portable OS on, I shop around for ones that I can 're-program' from being seen as USB Removable Storage devices into USB Mass Storage Drives... This might be above your skill level, and if not done right, can brick the device... But is much faster booting and running, as it installs as if it is a portable drive, instead of a compressed Live Image Environment.

I have a few generic Windows To Go, and Linux Distro's, installed to USB Flash drives, to use on onsite support calls. On those kinds of service calls, I don't have time to wait for a machine to boot slowly, so that I can diagnose them.

I personally sort of lean towards either a Kingston DataTraveler Max 1TB and Lexar P30 1TB. (The Lexar, I can modify to look like a mass-storage drive) If It is something that I want to be more practical and durable, then I lean towards portable SSD's. I have only one USB C Flash drive, which I use for some specialized mobile device tools.

Ensure you are plugging it into a USB3.x port to ensure you are getting the highest speeds that you can get.

---

