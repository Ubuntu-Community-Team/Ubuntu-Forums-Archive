---
title: "sda vs hda"
date: 2008-05-15
forum: General Help
---

### Post by logos34 on 2008-05-15
My ShipIt Hardy cd just arrived in the mail and I decided to fire it up to check out the menu and desktop (I have UbuntuStudio 8.04 installed).  I opened gparted and ran fdisk and noticed that they see my ide/pata hard disk as 'sda' instead of 'hda' (as my current install does). The version of gparted is the same (0.3.5). 

Since the adoption of the libata scsi driver back in Feisty I've been expecting my ide drive to show up as 'sda', yet that hasn't happened (except for the small fact that 8.04 install does now see my cd/dvd as 'scd0' instead of hdc in fstab.
  
I wonder why

---

### Post by bingoUV on 2008-05-15
> **logos34 said:**
> My ShipIt Hardy cd just arrived in the mail and I decided to fire it up to check out the menu and desktop (I have UbuntuStudio 8.04 installed).  I opened gparted and ran fdisk and noticed that **they see my ide/pata hard disk as 'sda' instead of 'hda'** (as my current install does). The version of gparted is the same (0.3.5). 

Since the adoption of the libata scsi driver back in Feisty I've been expecting my **ide drive to show up as 'sda', yet that hasn't happened **(except for the small fact that 8.04 install does now see my cd/dvd as 'scd0' instead of hdc in fstab.
  
I wonder why

In the first paragraph you say that ide disks are seen as sda instead of hda. In the second paragraph you say that it is not so. I see a contradiction.

---

### Post by fyo on 2008-05-15
> **bingoUV said:**
> In the first paragraph you say that ide disks are seen as sda instead of hda. In the second paragraph you say that it is not so. I see a contradiction.

There is no contradiction. He's referring separately to his "real" install and his ShipIt Hardy cd.

And can, btw, confirm his observations. Hardy Heron shows my pata disks are sdx as well, instead of the hdx of previous Ubuntus.

---

### Post by logos34 on 2008-05-15
> **fyo said:**
> There is no contradiction. He's referring separately to his "real" install and his ShipIt Hardy cd.

And can, btw, confirm his observations. Hardy Heron shows my pata disks are sdx as well, instead of the hdx of previous Ubuntus.

 
yeah, permanent hard disk install vs. the 8.04 livecd.  although I probably could have phrased it a little clearer.

The only thing I can think of is there is some difference in the libata driver.  Maybe they updated it or something to include more chipsets (although my run-of-the-mill nvidia board is nearly three years old)

---

### Post by woodsby on 2008-06-16
I just noticed something funny.  I installed LinuxMint (based on Hardy) on my laptop in the following partition table:

/dev/hda1     /boot
/dev/hda2     /
/dev/hda3     not used
/dev/hda4     swap

Then I installed Fedora utilizing the first partition above as /boot and the third partition as /.  I didn't install grub with the fedora install.  I rebooted and was taken directly into Mint as expected (since I didn't re-install grub).  I edited the /boot/grub/menu.lst and added an entry to boot the fedora off of /dev/hda3 (i used the hdx layout to match the existing entries for mint).  I then tried to reboot into fedora and got the error "could not find filesystem '/dev/root'".  Booted back into Mint and changed /dev/hda3 to /dev/sda3 and now I am able to boot into Fedora or Mint.  So for the ubuntu/mint side, it's using hdx and on the fedora side of things it's using sdx.

---

### Post by geirha on 2008-06-16
This change from /dev/hd*x* to /dev/sd*x* has been happening at least since feisty (for some). The linux developers are apparently rewriting old pata drivers, and the new drivers get sd*x* names.

[http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce](http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce)

So the old pata-drivers are probably still around, and depending on the order the drivers are loaded, if the old pata-driver is loaded first, it probably "gets" the drive.

---

### Post by logos34 on 2008-06-16
> **geirha said:**
> This change from /dev/hd*x* to /dev/sd*x* has been happening at least since feisty (for some). The linux developers are apparently rewriting old pata drivers, and the new drivers get sd*x* names.

[http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce](http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce)

So the old pata-drivers are probably still around, and depending on the order the drivers are loaded, if the old pata-driver is loaded first, it probably "gets" the drive.

hmm, interesting.  

Since I posted this thread, there have been two kernel updates, -17 and -18, and these both see the drive as 'sda'.  So maybe the updated kernels are now scanning the list of drivers/modules in a different order like you say, and the scsi module is loading before the older pata.

---

### Post by kcponline on 2008-07-10
Funny...I upgraded to Hardy and when I rebooted, it said that all of my drives except for hda1 had bad superblocks or corrupt filesystems.  I had read lots of forum entries about this and the only advice I found was to re-format the drives.  

I renamed all of the drives in fstab from /dev/hdaX and /dev/hdbX to /dev/sdaX and /dev/sdbx and rebooted and it worked!  

Just hope someone else can try this and avoid losing their data.

---

### Post by VMC on 2008-07-10
This topic sure got me sidetracked. There is something about the udev rules, found at "/etc/udev/rules.d", which you can change. there's a lot of info in that directory.. There is a lot of information of the subject of hda/sda change. The kernel is the main reason for the change.

---

