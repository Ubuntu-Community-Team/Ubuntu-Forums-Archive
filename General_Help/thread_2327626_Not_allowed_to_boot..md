---
title: "Not allowed to boot."
date: 2016-06-12
forum: General Help
---

### Post by Omar_Jair on 2016-06-12
So, apparently there is another forum thread but since its abandoned I decided to open a new one, the exact same issue, ubuntu is my main OS on my Toshiba Satellite C-55B sadly whenever i burn a disk image which by the way it's a pain to use brasero since its hell buggy and practically useless, or mount an iso on a USB ubuntu seems to "Block" my boot options, i know it is not bios related because i set it to boot from CD/DVD and/or USB first and it doesn't seem to work, i also can read disks perfectly fine on my laptop so, is there a way to fix this? or if i need to reinstall i will get stuck forever on a broken system?

---

### Post by deadflowr on 2016-06-12
This thread:
[http://ubuntuforums.org/showthread.php?t=2325478]("http://ubuntuforums.org/showthread.php?t=2325478")
?

---

### Post by Omar_Jair on 2016-06-12
xD no, one even more antique

---

### Post by X-RED_Tech on 2016-06-13
Can you post the link to that thread?

Without more info I can only tell that booting an installation media happens (or not) before Ubuntu or any other OS is loaded.
It's all in the BIOS/UEFI and often the one-time-boot key, if available, gives better results and you can assure it is booting (or trying to boot) from the drive you want.
Bad media won't boot, of course, and the BIOS/UEFI will then default to the next boot device which is most likely the HDD or SSD with Ubuntu installed thus giving you the impression Ubuntu is involved but it isn't.

---

### Post by Omar_Jair on 2016-06-14
Is there any good Linux CD Burner? ive done an experiment, if i burn the disk on my windows 10 machine i can boot however using brasero or the boot media creator to burn DVD's or USB sticks the results do not boot, is there any alternatives for it that are not k3b? i dont wanna pollute my unity desktop with KDE stuff.
The following link is the thread i was talking about 
[http://ubuntuforums.org/showthread.php?t=2327542&p=13502874#post13502874](http://ubuntuforums.org/showthread.php?t=2327542&p=13502874#post13502874)

---

### Post by Bucky Ball on 2016-06-14
Create a USB with UNetbootin. A quick search will find it.

With the machine off, USB plugged in, boot the machine and hit F12 to get you to the boot device menu (not the BIOS). Is the USB appearing there? If not, there is something wrong to start with that doubtful has anything to do with how you're burning the image. Do you have 'USB mass storage devices' enabled in the BIOS, if that option is there anywhere?

With UNetbootin, you need to wipe the USB first. I generally remove all partitions on the USB, rewrite the partition table and create one FAT32 partition that uses the entire USB (I use Gparted for all this). You _MUST_ have a FAT32 partition on the USB before moving on to UNetbootin where you will select your ISO, your target device, then create the Ubuntu installer USB.

---

### Post by oldfred on 2016-06-14
Try both of these boot parameters instead of quiet splash, you add like nomodeset
intel_idle.max_cstate=1 pci=nomsi 

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
You could have these issues.
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3) 

Just about every Asus needs the pci=nomsi boot parameter.
      
 Asus x55u UEFI change to BIOS discuses boot keys esp & f2
[URL="http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html"]http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html
[/URL]
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499) 

But you also have a Celeron that I think is Bay Trail, so you may need this also:

 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail) 

[URL="http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html"]
[/URL]

---

### Post by Omar_Jair on 2016-06-14
I know it is something with ubuntu because every single disk i burnt here does not work, maybe i found something that linux can't do properly xD

---

### Post by Bucky Ball on 2016-06-15
Or something to do with the way the disk is burnt or its being booted. Have you tried it on another machine?

---

### Post by jimmy-frydkaer on 2016-06-15
> **Omar_Jair said:**
> Is there any good Linux CD Burner? ive done an experiment, if i burn the disk on my windows 10 machine i can boot however using brasero or the boot media creator to burn DVD's or USB sticks the results do not boot, is there any alternatives for it that are not k3b? i dont wanna pollute my unity desktop with KDE stuff.
The following link is the thread i was talking about 
[http://ubuntuforums.org/showthread.php?t=2327542&p=13502874#post13502874](http://ubuntuforums.org/showthread.php?t=2327542&p=13502874#post13502874)

Have you tried K3B? It somewhat resembles Neoburn.

---

### Post by Bucky Ball on 2016-06-15
> **jimmy-frydkaer said:**
> Have you tried K3B?

> **Omar_Jair said:**
> ... is there any alternatives for it that are **not k3b**? i dont wanna pollute my unity desktop with KDE stuff.

Pays to read the thread. The OP clearly does not want to use K3B, and I don't blame them. It drags in a ton of KDE dependencies, as do most things in the repos that start with 'K' ... :|

---

### Post by ajgreeny on 2016-06-15
Try **xfburn** which uses different libraries etc etc to carry out the burn; I have found it to be very reliable.

---

### Post by nametwodotfour on 2016-06-15
the best way i personally like to put an iso onto a usb is to either dd it from my mac or on windows use universal usb installer or on linux just use gnome disk utility, restore image option 

dd command:
> $ sudo dd if=/dev/disk2 of=backup.my.sdcard-18-oct-2015.img.dd bs=512

---

### Post by ajgreeny on 2016-06-15
Please use the default colour and font for your posts; I could hardly read the code that you showed.

---

### Post by Bucky Ball on 2016-06-15
> **nametwodotfour said:**
> the best way i personally like to put an iso onto a usb is to either dd it from my mac or on windows use universal usb installer or on linux just use gnome disk utility, restore image option 

dd command:

dd, also known as 'disk destroyer', takes no prisoners and one false move will obliterate the target device, even if it's the wrong one, no questions asked. You get one chance at it. There is no 'Are you sure this is the correct device?' or any other niceties. You choose a target and hit 'go'!

Safer, and still using dd under the hood, is [mkusb]("https://help.ubuntu.com/community/mkusb").

You might also want to have a [look through this]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by Omar_Jair on 2016-06-18
Did try booting it on several computers by now, no results at all, had to do the popular USB method by now, K3B will install KDE dependencies or so on my Ubuntu flavour or can those get all cleaned up if i decide to uninstall it?

---

### Post by Bucky Ball on 2016-06-18
There is absolutely nothing special about K3B. xfburn, Brasero and any number others mentioned ... they all do exactly the same thing as K3B does when it comes to burning a disk image. 

For USB, UNetbootin, Universal USB Installer, and the list goes on. There is really nothing special about k3b, except it will drag in a whole load of KDE dependencies. No, don't know if you can get rid of everything if you can uninstall, but suspect, with some effort, it might be possible. Others may know more definitively.

---

### Post by Omar_Jair on 2016-06-18
I did a test and noticed something odd, i tried burning 2 DVD's one on my windows machine and the other here on linux, one disk looks like it was written upside down, the pale part is from center to out but the linux one has a pale "Halo" and leaves the center unwritten, is it my disk thing? or am i using a wrong burning option?

---

### Post by banceu_sergiu_ione on 2016-06-19
I've always fallowed  this: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) for CD, right click on .iso and select the ' Write to Disc... ' and as Bucky Ball said UNetbootin for USB type.
Check that the DVD was burned properly : [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD) , just open the DVD and make sure it had not copy the .iso but extracted the files.
Go for a clean and full install, don't border with partition wile install. You can use GParted after to partition your HDD as you like.

---

### Post by Omar_Jair on 2016-06-19
Thanks for the link :) (I do write iso properly xD i know its not drag and drop)

---

