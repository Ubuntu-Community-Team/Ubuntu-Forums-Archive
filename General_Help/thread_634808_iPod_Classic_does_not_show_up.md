---
title: "iPod Classic does not show up"
date: 2007-12-08
forum: General Help
---

### Post by Breepee on 2007-12-08
I just connected my new iPod Classic to my computer, and although on the iPod's display it says it's connected and I have to disconnect before removing, it does not show up anywhere in Ubuntu. lspci has no trace of the iPod and /media has no /ipod either.

I properly initialized it in iTunes (in Windows) first, and set the device to show up a a normal hard drive. I don't want to synch with Amarok or Rhythmbox,  just see the drive and put normal files on it (or remove them). Any ideas?

---

### Post by gobbles414 on 2007-12-08
Breepee

Try running *lsusb* in the command line. Run it once without your iPod connected to get a baseline reading. The run the command with your iPod connected to see if it is detected. If your iPod is not detected, then there are a few possibilities: (1) Try another USB port on your computer, preferably a rear one if you are using a desktop computer. (2) The cable that connects your iPod to your computer has been damaged. (3) Your iPod's software and/or hardware has been damaged. I am sure other possible causes exist. But those are all that I can think of at the moment.

If your iPod is detected, the problem probably lies somewhere in the assigned mount point in Ubuntu. Try using a program such as the *GNOME Partition Manager* to reformat your iPod. A program such as Banshee should then be able to replace your iPod's file structure. Keep us posted with you progress please.

---

### Post by Breepee on 2007-12-08
Gobbles,

lsusb turns up an entry with Apple Computer Inc. in it. Since it's the only Apple device I have, it's gotta be the iPod.

GParted however does not see the iPod, so nothing to do here.

The iPod (and the cable, and the port, which is at the back) works fine in Windows and I have loaded it up through iTunes there (plays back OK too). So I don't think it's the hardware.

What it *is* however, I have no clue.

---

### Post by Wobblybob on 2007-12-08
try this :
[[COLOR="Purple"]**http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+classic**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+classic")          
I now have my iPod classic black 80GB running on my Gusty Intel PC thanks to these guys.

---

### Post by gobbles414 on 2007-12-08
Breepee,
Well... at least we know that all of your hardware is working. It does indeed sound like a software issue. If Wobblybob's solution fails, you might want to try either disabling *legacy USB* support in your computer's BIOS and/or reformatting you iPod using *My Computer => right-click on iPod => Format* in Windows. If Ubuntu thinks that your iPod is a normal hard drive, it might mount the device correctly. Then use Banshee or another iPod-compatible application to rebuild the iPod's directories.

Wobblybob,
The link that you have provided seems promising. BUT, there are five pages worth of posts in that thread! Could you please provide us with the post(s) with the procedure that worked for you?

---

### Post by Wobblybob on 2007-12-09
> Wobblybob,
The link that you have provided seems promising. BUT, there are five pages worth of posts in that thread! Could you please provide us with the post(s) with the procedure that worked for you?

The first page has the main How To, if you get errors then many of them are covered in the following pages

This from Paradoxni was also very useful

```
Ok I got hold of a new gen IPOD nano to test this out and was getting the same problem as you, empty IPOD even with songs uploaded to it with Rythmbox. I fixed it thou...

Delete the old libgpod libraries:
Code:

 sudo rm /usr/lib/libgpod.so.2.0.0
sudo rm /usr/lib/libgpod.so.2

Create links to the new one:
Code:

sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2

ipod-read-sysinfo-extended is supposed to create SysInfo file on IPOD with FirewireID inside, but it did not work here, so I added it manually:

Connect IPOD to PC, then
Code:

sudo lsusb -v | grep -i Serial

Note down your FirewireID from the list, its the 16 digit one.
Code:

 iSerial                 1 0000:00:1a.1
  iSerial                 3 000A27001AD21163  <---- IPOD FirewireID
  iSerial                 3 3547160158733600
          line coding and serial state
          line coding and serial state
  iSerial                 0 
  iSerial                 1 0000:00:1d.7
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0
  iSerial                 1 0000:00:1a.0
  iSerial                 0 
  iSerial                 0 
  iSerial                 0 
  iSerial                 1 0000:00:1d.2
  iSerial                 0 
  iSerial                 3 060114014271000001
  iSerial                 1 0000:00:1a.7

Create SysInfo file on IPOD (assuming IPOD mounted at /media/IPOD):

Code:

sudo gedit /media/IPOD/iPod_Control/Device/SysInfo

SysInfo should only contain:
Code:

FirewireGuid: 0x<your firewire ID>

e.g. FirewireGuid: 0x000A27001AD21163


```


The rest of the thread is here [[COLOR="Purple"]**http://ohioloco.ubuntuforums.org/showthread.php?t=611404&page=2**[/COLOR]]("http://ohioloco.ubuntuforums.org/showthread.php?t=611404&page=2")

Good luck!

---

### Post by Breepee on 2007-12-10
Thanks, but it is still assumed (and in every howto I could find) that the iPod is mounted at /media/ipod. It is not, that is the whole problem.

I cannot find anything on this, so basically what you're saying is that I should format the thing in Windows and rebuilt in Linux with Banshee or whatever. Hmm. I want to keep using it in iTunes... (it appears i can't switch album when uploaded with third-party software, anyone expiencing the same?).

---

### Post by gobbles414 on 2007-12-10
Hi Breepee,

I vaguely remember reading about some iPods that would not mount due to firmware issues -- but that was well before the iPod Classic was released. Speaking of firmware, have you applied the latest updates from Apple to your iPod?

Try this for me please: Boot your computer from a Ubuntu 7.04 or 7.10 LiveCD -- the same disk that you would normally use to install Ubuntu. It might actually be a good idea to try both the .04 and .10 disks. Once the LiveCD has finished loading, plug your iPod into your computer. Does it mount? If so, that probably means that some customization or unsupported software has corrupted your Ubuntu installation. Updating from one release of Ubuntu to another can also cause odd behaviors such as you describe. In that case, backup any important data from your hard drive and re-install Ubuntu.

Formatting the iPod in Windows is just an idea that might force Ubuntu to assign a new mount point to your iPod. Once that has happened, you can probably re-sync it with iTunes and still have the device mount in Ubuntu. There is also something called in Linux called *submount* that could help you to solve your problems. But I have never used it before.

As far as I know, iPods can only sync with one library at a time -- with a possible exception for iTunes Music Store files using iTunes. You can use RhythmBox to listen to music from your iPod on your computer. But you cannot sync with both RhythmBox and iTunes. I know that Banshee is not yet compatible with the way in which newer versions of iTunes manage iPods. So you must choose between Banshee compatibility and iTunes compatibility.

Keep us informed regarding your progress.

---

### Post by Breepee on 2007-12-10
At first I only used Yamipod (which works for me in Windows and OSX), but it has a little bug that prevents me from changing albums uploaded with Yamipod. So then I turned to iTunes and set it to show up as a hard drive, copy files over manually, bla bla, basically switched of everything automatic. I uploaded about 110GB and then I could edit the library on the iPod on a different computer with yamipod. I dont want to synch, just copy stuff over when I want to.
Yamipod claims to work with every iPod, so it means that it doesn't care if the iPod is 'locked' to some system (which I like, since I use multiple systems). Yamipod is available for Linux, but I couldn't try it out because Ubuntu doesn't mount the iPod.

I'll be right back with an update on how it works in a LiveCD.

Update: OK, I booted into the 7.04 LiveCD (don't have the 7.10, I have 7.04 installed too btw). Works perfectly. Shows up (though not as /media/ipod but as /media/name_itunes_asked_me_te_give_it). Anyway, Rhythmbox asked be to set it up, I could browse the music on it fine. Yamipod wanted it mounted under /media/ipod so I symlinked it there, but it didn't see it.

Anyway, the drive was recognized correctly. Any ideas what part my current Ubuntu install may be the problem? I hadn't installed anything related to the iPod before I first tried to connect. Also I havn't changed that much on this install.

---

### Post by gobbles414 on 2007-12-10
Breepee

**I booted into the 7.04 LiveCD (don't have the 7.10, I have 7.04 installed too btw). Works perfectly**
OK... this establishes that the iPod will work with Ubuntu.

**Yamipod wanted it mounted under /media/ipod so I symlinked it there, but it didn't see it.**
Two things: (1) You might try naming your iPod *iPod* in iTunes. (2) While using the LiveCD, the LiveCD itself is acting as your hard drive and operating system. But it is also *read-only*. That means that you cannot save any files or install any programs while using the LiveCD.

**Any ideas what part my current Ubuntu install may be the problem?**
No... But you might try doing a fresh install of 7.10. That version of Ubuntu has better support for "foreign" disk formats than 7.04.

---

### Post by gobbles414 on 2007-12-12
Hi again Breepee,

I just remembered that the original versions of Windows Vista mishandled iPods. Are you running iTunes in Vista? And if so, have you applied all of the latest updates from Microsoft? I doubt that the Vista bug is the source of your problems. Otherwise the iPod would probably not have mounted in the Ubuntu LiveCD.

---

### Post by Breepee on 2007-12-13
Nope, I use XPSP2 (of course updated).

I'll try installing 7.10 I hope this year, and if that doesn't solve the problem, I'll report back ;)

---

### Post by fullbleedboy on 2007-12-13
Breepee, your problem reminds me of the issue Fiesty had with some USB 2.0 devices.  Your ipod doesn't automatically mount when connected, right?  What does your *dmesg* show?  If you had the same problem as I did, you'll see **ehci_hcd** error messages in your logs.  ehci_hcd fails to handle the device so it doesn't get emulated as a SCSI device, and will not automatically mount.  

To test this, unload the ehci_hcd module, then connect your ipod.  It will automatically mount, but will only operate in *FullSpeed* and not *HiSpeed*.  I wouldn't suggest syncing music in USB 1.1, unless you're a masochist.

To fix the problem, I upgraded to 7.10.  New kernel, new modules, everything worked.

HTH.

---

### Post by Breepee on 2007-12-14
Interesting results from dmesg:

> [  148.443055] usb 7-5: new high speed USB device using ehci_hcd and address 3
[  148.576515] usb 7-5: configuration #1 chosen from 2 choices
[  148.675497] usbcore: registered new interface driver libusual
[  148.682511] Initializing USB Mass Storage driver...
[  148.682566] scsi8 : SCSI emulation for USB Mass Storage devices
[  148.682607] usbcore: registered new interface driver usb-storage
[  148.682609] USB Mass Storage support registered.
[  148.682690] usb-storage: device found at 3
[  148.682691] usb-storage: waiting for device to settle before scanning
[  153.675760] usb-storage: device scan complete
[  153.683380] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  153.699340] sdc: Spinning up disk....ready
[  155.666360] SCSI device sdc: 39023511 4096-byte hdwr sectors (159840 MB)
[  155.666981] sdc: Write Protect is off
[  155.666984] sdc: Mode Sense: 68 00 00 08
[  155.666985] sdc: assuming drive cache: write through
[  155.668605] SCSI device sdc: 39023511 4096-byte hdwr sectors (159840 MB)
[  155.669229] sdc: Write Protect is off
[  155.669231] sdc: Mode Sense: 68 00 00 08
[  155.669233] sdc: assuming drive cache: write through
[  155.669235]  sdc: sdc1
[  155.850840] sd 8:0:0:0: Attached scsi removable disk sdc
[  155.850883] sd 8:0:0:0: Attached scsi generic sg4 type 0

So the drive is listed (I have the 160GB iPod). No errors that I can identify as such. I've used Gparted to see what's at /sdc and it is some 18GB partition (my iPod has one partition). Gparted has not any more info on this partition/drive, but somehow I think it's the iPod, but when I don't attach the iPod, that partition isn't there (I was not paying attention when I earlier said that Gparted didn't see anything).

Edit: I unloaded ehci_hcd and reattatched the iPod, no effect. Still not mounted in any way.

---

### Post by gobbles414 on 2007-12-15
Breepee,

I totally agree with fullbleedboy. The easiest and quickest way to fix your problem is to install Ubuntu 7.10. As I probably have already stated, I recommend doing a clean install instead of an upgrade.

---

### Post by Breepee on 2007-12-16
I'm awaiting a new hard drive (it'll come this week I hope) and then I'll install 7.10 and see how goes.

---

### Post by gobbles414 on 2007-12-31
How did it go?

---

