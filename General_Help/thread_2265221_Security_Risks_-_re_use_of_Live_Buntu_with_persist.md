---
title: "Security Risks - re use of Live Buntu with persistence (no password)"
date: 2015-02-13
forum: General Help
---

### Post by JeQhdMD on 2015-02-13
I am demo'ing at our PC club, how to create a persistent Live OS using Xubuntu 14.04 on USB v3 Flashstick.  Note . . this way of running an OS is not intended to replace a traditional install on hdd/ssd - - but as a temporary way to access data either on windows or linux partitions (e.g., a rescue OS).

Performance is very close to actual hdd install - it's great to be able to add/remove apps, and save desktop modifications, but there are a couple "issues" or negatives.  I basically want to learn if there are methods to mitigate or lessen the risk(s).

Issue 1:  the normal package update process via system update app is not set up, and is not as functional (like kernel updates),  so may be running some apps with vulnerabilities,

Issue 2:  the normal permissions system is modified . . . no login ID or password for the "Live User" (sudo password is not required when installing or similar tasks).

So, am I _assuming a reasonably (low) risk_ to run a Live OS as a temporary way to recover lost data caused by non-hardware issues (especially for windows users that muff up the registry, etc.)???   

By the way, at another demo, I intend to show the process of obtaining and running a Live OS that is static such as "System Rescue CD", "Parted Magic", etc.    The down side to those distros are old browsers with limited media support, potential sound issues and the relative difficulty in fixing/customizing those static OS's.

Any feedback re the "actual" or "perceived" risks of the persistent Live OS is appreciated . . . one thing I may recommend to the club members is to replace the whole OS every 6 months.  (can be done easily).  Also, I may show & recommend installing and running "Encfs" with the "Gnome Encfs Manager" gui (needs ppa) so they can secure their data on the usb device.

PS . . .  Again, the reason I am even demo'ing the persistent method via USB3 is it runs "super fast" - - almost as if fully installed and is very customizable (a huge plus imho).

Thanks for sharing your ideas.

---

### Post by efflandt on 2015-02-13
While a live/install system can allow most anyone you knows what they are doing log in and do things (sudo) without a password, the system boots from a fixed squashfs file system, even if you have persistance. So somehow even if something in persistant data has been comprimised, it is unlikely to continue once it has been shut down unless something comprimised is manually run from persistant data, since fixed init scripts are intially run before persistant data is mounted.

---

### Post by sudodus on 2015-02-13
I agree that a persistent live system has a lower security level than

1. a live system without persistance (where nothing can be saved, so malware is not saved).

2. a fully updated/upgraded installed system (where known bugs should be patched).

I also agree that the risk is reasonably low, when persistent live systems are run in a cautious way.

Comment:

You can install a system into a USB pendrive in the same way as you install a system into an internal drive. It will be slow with USB 2 pendrives, but with fast USB 3 pendrives, the performance can be quite good. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858") post #6

---

### Post by C.S.Cameron on 2015-02-13
With a persistent install you can go to User Accounts and add yourself as a user.
You will then get a password prompt when booting up.
(You might have some problem shutting down though).
Casper-rw, (the file where persistence info is kept), can not be encrypted, (as far as I know), so it can easily be mounted and data extracted from it.

---

### Post by JeQhdMD on 2015-02-13
Hmm, more to think about . . . thanks for the input.  

Re encryption (encfs) on a persistent live usb . . . I haven't yet tested it (and unfortunately won't have time before the demo tomorrow am) . . . so, I won't talk about that aspect of the install until I know more if it's really doable.

Re risks of use - is running the live Xubuntu session at a place with open wireless smart (or not) . . . ports are still closed or stealthed except return routes on my browser queries - is the OS itself (files) open in any way?

Re actually installing the OS on the USBv3 flash-stick . . . . that's something I've thought about but not tested (perhaps a future demo).   Would the Live OS appear on the grub menu as an additional selection?  So far, the one significant downside to either a persistent Live OS or an installed OS on usb-stick is the filesystem read/write durability is less than SSD or HDD operation (but by what factor I wonder).

Anyway, thanks again guys for the useful info, it's helped me already to plan a better demo.

BTW, on a Live usb with persistence, even if adding a new user, at bootup, the "Live User" is the session automatically opened - if logging off the Live User, a prompt for login of the alternate user is displayed.

---

### Post by sudodus on 2015-02-14
> **JeQhdMD said:**
> ...
Re risks of use - is running the live Xubuntu session at a place with open wireless smart (or not) . . . ports are still closed or stealthed except return routes on my browser queries - is the OS itself (files) open in any way?

I'm no security expert. There might be risks. So I would not use the system on that demo pendrive to connect to my bank account after connecting at a place with 'open wireless'.
> 
Re actually installing the OS on the USBv3 flash-stick . . . . that's something I've thought about but not tested (perhaps a future demo).   Would the Live OS appear on the grub menu as an additional selection?  So far, the one significant downside to either a persistent Live OS or an installed OS on usb-stick is the filesystem read/write durability is less than SSD or HDD operation (but by what factor I wonder).

Yes, it would appear on a grub menu. You can make it appear on its own grub menu, and on that of the internal drive, or you could use chainloading to boot from either drive to a system on the other drive. Windows has methods to prevent booting from USB, probably in order to make it harder to work around the licence. Free software (linux) has no such need, and can treat a USB drive in a similar way as a SATA drive, simply a mass storage device, that can be made bootable.

It is recommended to use the mount option **noatime** to reduce repeated writing to the flash memory hardware. See *post #8* of this link for more details about lifetime
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL]

---

### Post by C.S.Cameron on 2015-02-14
You need to add the USB to the internal drive's grub menu manually, doing an update-grub does not work for me.

Most old good quality flash drives have a minimum write capacity exceeding 10000 writes.
If you do the math, (ie time to fill drive x 10000), you will find that they should last many years of normal 8 hour/day use.
The new ones are even better.
if you use noatime and your flash drive becomes unplugged I would suspect a greater chance of data loss, (which could be many times the cost of a flash drive).

---

