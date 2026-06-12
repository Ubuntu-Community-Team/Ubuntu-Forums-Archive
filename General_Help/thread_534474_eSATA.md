---
title: "eSATA"
date: 2007-08-25
forum: General Help
---

### Post by Scorpuk on 2007-08-25
Never used this before and I was wondering if you can plug and unplug eSATA devices with the computer on?


FYI my motherboard is the Gigabyte GA-G33-DS3R.


Installed 64bit Ubuntu from ALT CD.




tnx.

---

### Post by Azriphale on 2007-08-26
... Nice motherboard. Wish I had one of those :)

I have not had the opportunity to actually test eSATA in Ubuntu (need to get an ExpressCard eSATA controller for my notebook first).
I notice that your motherboard has the ICH9R southbridge. This does directly support eSATA hotplugging (the ICHxR series do, the ICHx series do not). I do not know if only certain SATA ports on the motherboard support it (I'm assuming that you are connecting your eSATA to an internal SATA port on the motherboard).

At the very least, you can probably unmount the drive manually, and then unplug it:

```

$ sudo umount /media/sdb1

```

where /media/sdb1 is where is the point where your eSATA drive is mounted
or 

```

$ sudo umount /dev/sdb1

```

where /dev/sdb1 is the actual device file of your eSATA drive.

I'm afraid I can't give you any more than that. Anybody else got some help here?

Does the eSATA drive not show up as a mobile device on your desktop (in the same way as a flashdisk)? If so, you can right click on the icon, and select the "Eject" option (in Gnome) or "Safely Remove" in KDE. Of course, this will only be here if Linux supports the ICH9R eSATA hotplugging.

---

### Post by Scorpuk on 2007-08-27
Thanks for your reply.


Since the ICH9R ports are all used I have put the eSATA bracket into the purple SATA ports controlled by Gigabytes SATA 2 controller.


At the moment I have a SATA CD-ROM drive plugged into it, but that was so I could install the OS.


The main reason behind me wanting to be able to hot pug on this port is that this is a new server and I want to be able to plug in my old servers SATA drive to transfer the data and once complete unplug the drive without having to switch off the new server. Or at anytime in the future.

---

### Post by Azriphale on 2007-08-27
I'm guessing that your results with using the Gigabyte SATA controller means that it does not support hotplugging to the degree that the Intel one does. 

That still should not be a problem, except that as you have found, it won't happen automatically. As long as you unmount the drive before unplugging it, there should be no data corruption (once the drive is unmounted, the OS can't use it, so you won't interrupt any writing operations).

I'd say, it is likely to be safe to plug in the drive, mount it, copy your stuff across, and unmount it. Before you unplug the drive from the PC, power it down (I assume you are using an eSATA hard drive enclosure). Then unplug the drive from the eSATA port.

I'd test it for you with desktop (ICH8 controller), but its only got Vista on it. My nearby Ubuntu machine does not have accessible SATA.

---

### Post by Azriphale on 2007-08-27
I decided to do a bit of research on this again, and found that when a SATA controller has AHCI enabled, hotplug support will (should) be enabled. The Gigabyte SATA2 controller supports AHCI, and can be enabled in the BIOS, in the Integrated Peripherals section, by setting the "Integrated SATA/IDE Ctrl Mode" to AHCI. Note this is from my GA-965P-DS3, so it may be slightly different to yours.

You should also be able to set your ICH9R SATA mode to AHCI for hotplug support with that controller. AHCI mode also enables Native Command Queuing, and should theoretically improve performance. You may want to do that anyway.

And, I have come across Gigabyte stating that they will not allow AHCI on my ICH8 chip. Guess i'm moving my eSATA, and my main disk to the Gigabyte controller.

---

### Post by Scorpuk on 2007-08-27
thanks again for the reply.

I'll give it a try this weekend when I'm home.


For safety sake I'll try it with the drive plugged in on bootup, copy the files across and then try hot plugging. :)


The drives not in an enclosure, but directly connected to the eSATA back plate with the appropriate cables. If I need to I'll unplug the power lead 1st and then the data cable.


tnx again :D

---

### Post by Azriphale on 2007-08-27
One more thing, in a live system you actually probably do not want to play with AHCI settings on your SATA controller. Linux will probable handle it a whole lot better than Windows, but my Vista machine had a heart attack and wouldn't boot, even though I did not even have anything plugged into the AHCI-enabled SATA controller. I had to disable it again to get Windows to boot.

But you should be fine simply unmounting and powering down the drive. I tried that earlier, and everything still works. As long as the system is not writing to the drive, you will suffer no data loss, hence the unmounting prior to pulling the plug. If the drive is in use, you will not be able to unmount the volume, so you will know before you unplug.

---

### Post by phantom42 on 2007-08-31
Enabling AHCI should not be a problem in windows as long as you make sure to install the sata controller drivers **first**. Obviously, this won't be necessary in linux.

---

### Post by Azriphale on 2007-08-31
I'm using Vista, which is supposed to have sata divers out of the box. Maybe at some stage i'll get around to bothering to try again :P But that will probably only happen if i feel like doing a reinstall, and with the hard-drive image backup of Vista Ultimate, thats unlikely.

---

