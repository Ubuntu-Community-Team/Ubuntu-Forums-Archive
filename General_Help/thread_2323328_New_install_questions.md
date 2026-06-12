---
title: "New install questions"
date: 2016-05-04
forum: General Help
---

### Post by kreasonos on 2016-05-04
Hello friends, I am a new Linux user, using Ubuntu Mate 16.04, and after installing on my thinkpad (did a fresh install wiping the drive), I noticed that upon startup I still get the Lenovo logo, does that mean the Lenovo Bios is still installed? I thought everything was wiped when doing the clean install? If not, what else remains on the disk besides the Linux OS? Also, I noticed my drive is still using lots of space, another thing that confuses me. When I saw the Linux OS was only 1.5ish GBs I was under the impression that I would have nearly my entire drive space available. But, as it is, I'm showing I have (systen/pref/hardware/disks), 3 partitions, 1 is 537MBs w/532 free, 2 is 247GBs w/237 free, 3 is 8.5 GBs w/ nothing showing free. I've installed a couple apps I needed like ST and Chrome, but other than that, does this sound right? Oh, and for some reason software boutique/adobe flash player wouldn't install but Chrome seems to be fine without it. Anyone know what's up with that? Thanks everyone and glad to be here. Windows 10 was a nightmare for me (driver bugs).

---

### Post by Impavidus on 2016-05-04
1: The entire hard drive was wiped. It wasn't actually overwritten, but it was formatted. The Lenovo logo however is not on the hard drive. The bios (or UEFI more likely nowadays), including the Lenovo logo, is stored on a chip on the motherboard. That was not wiped during the Linux install. Nothing however remains on the hard drive.

2: The Ubuntu installation disk may be 1.5GB, but the actual system after installation is larger than that. During installation things are unpacked. The partitions you see are probably an EFI boot partition (small, at the beginning of the disk), the root partition (the big one with the OS, on a fresh installation about 10GB in use) and the swap partition. The swap partition doesn't contain any files, but can be used as additional memory (which is rarely needed on today's computers with lots of memory) or to hibernate. So that sounds about right.

3: I don't know why the software centre (or what is it called nowadays?) cannot install Adobe flash player. How did you try to install exactly? What was the error message? But Chrome doesn't mind, because Chrome has its own flash player build in.

---

### Post by kreasonos on 2016-05-04
Wow, thank you so much for the detailed answers. 

3. It's called "software boutique." I tried installing it from there by clicking "install." The error message I can't recall but it's working now. 

Also, for some reason Ubuntu Mate 16.04 isn't showing my city and state in the system/admin/timeanddate, so I had to use a different place with the same time. Is it possible to add a new city and state?

---

### Post by Bucky Ball on 2016-05-04
Try doing an update/upgrade and get everything up to date if you haven't already and see if that makes any difference and what problems are left.

@Impavidus: Software Boutique is a Mate thing. :)

---

### Post by kreasonos on 2016-05-04
I updated from system/admin/software updater, and I still don't see Houston or even Dallas on there. There aren't many central time zones at all. Is there another place I can run an update from?

---

### Post by Bucky Ball on 2016-05-04
*Thread moved to **General Help**.*

You downloaded Ubuntu Mate [from here]("https://ubuntu-mate.org/download/")?

---

### Post by kreasonos on 2016-05-04
Yep. 
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04

---

### Post by kreasonos on 2016-05-04
The other thing I noticed is when I got to places/computer and click on the disk to show the properties, it says "unknown." I thought that was strange. Any idea why it's saying "unknown?"

[IMG]http://pic90.picturetrail.com/VOL2183/2324039/24719594/412464865.jpg[/IMG]

[IMG]http://pic90.picturetrail.com/VOL2183/2324039/24719594/412464864.jpg[/IMG]

---

### Post by Dennis N on 2016-05-04
> **kreasonos said:**
> I updated from system/admin/software updater, and I still don't see Houston or even Dallas on there. There aren't many central time zones at all. Is there another place I can run an update from?

I doesn't matter where the updates come from. The various servers other than the main one are called mirrors. You can have the updater run the "select best server" test to find the fastest connection and select that server to use for your updates.

---

### Post by kreasonos on 2016-05-04
I fixed the time! Yay! Do you know why the disk is saying unknown? The "file system" at least shows volume "known" and computer as computer:///. Is that right or is there something wrong?

---

### Post by Dennis N on 2016-05-04
> **kreasonos said:**
> I fixed the time! Yay! Do you know why the disk is saying unknown? The "file system" at least shows volume "known" and computer as computer:///. Is that right or is there something wrong?

**Places > Computer** will show the partitions on the computer's disks. **Properties** shows information if the partition is already mounted* when you open the window for "Computer". Attached is a screenshot of what it shows on mine.

* or you can mount the desired partition from within the Places > Computer window, then View > Reload (or use the Reload Icon (curved arrow) to reload). Then, right-click > properties will display the information shown.

---

### Post by kreasonos on 2016-05-04
Is the partition supposed to be mounted? I guess mine isn't then? When I right click it and click mount is says unable to.

---

### Post by Dennis N on 2016-05-04
Yes, you can mount the partitions from the side-pane of the Places > Computer window - they are listed under Devices. Then you need to reload: View > Reload or click the reload icon (curving arrow). Then you can get the Properties of items in the main window with right-click > properties.

---

### Post by kreasonos on 2016-05-04
The file system is set to open with caja and when I log into my server it's also by default set to open with caja, but the SSD image is the only one without anything to open it with. Any idea what's on it? What's the difference between it and the file system?

---

