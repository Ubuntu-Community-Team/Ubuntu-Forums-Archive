---
title: "Dowload ubuntu to usb drive"
date: 2014-12-29
forum: General Help
---

### Post by Camilia on 2014-12-29
Instructions [here]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu") say to Open the dash and search for Startup Disk Creator.

I can't figure out how to open the dash or where it is.

Tried right click the usb and search in pc.

Tried to download Pendrivelinux that suggested at the instructions. Stumped for asked to select ubuntu desktop.iso. Browse options just gives me files on usb. Don't want to use them. Guess I need to download ubuntu 1st.

---

### Post by ian-weisser on 2014-12-29
You click that highlighted icon in Step #3. The Ubuntu icon. Or your super (windows) key on the keyboard.

If you don't have that icon, then you're not already running (the Unity version of) Ubuntu, and are using the wrong instructions. You should use the instructions for the OS --or distro of Linux-- that you are currently running.

---

### Post by Camilia on 2014-12-29
Ubuntu has never been put on this pc. P

PC I use for ubuntu is frozen. Hoping to download to usb and reboot frozen pc.

---

### Post by Bucky Ball on 2014-12-29
Try [UNetbootin]("http://unetbootin.sourceforge.net/"). That is pretty reliable. I could be misunderstanding, you can't download the ISO directly to a USB and boot from it. You need a USB creator of some kind, but seems you already know that. So you need a working machine to burn the disk image to USB.

---

### Post by Camilia on 2014-12-29
Well i am muddling through the instructions with a headache. It is slowly becoming clear. Fortunately got a working laptop which has windows os.

Download ubuntu 12.04 from softpedia. Transfering it seeing has broken files. So have to see if can find another 1 to download later

Found downloads on [ubuntu.]("http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/installer-amd64/current/images/trusty-netboot/") Uncertain which 1 to use.

---

### Post by Bucky Ball on 2014-12-29
Get it from the official site [HERE]("http://www.ubuntu.com/download/alternative-downloads"). 

Best and most reliable way is with a torrent download, the links to which you'll find a bit further down that page. 12.04 and 14.04 are both available there.

---

### Post by Mark Phelps on 2014-12-29
Sorry if I misunderstood what you said, but it reads like you are copying files to the USB -- and that is NOT what you want to do.

The process is the following:
1) Download the ISO file of the Linux distro you want -- saving that to a folder on your drive
2) Run the USB Startup Creator app of your choice (I always use the Universable USB Creator from PendriveLinux) and select the ISO file you just downloaded
3) The app will extract the files and folders from the ISO file and write them to the USB stick.

---

### Post by Bucky Ball on 2014-12-29
> **Mark Phelps said:**
> 
The process is the following:
1) Download the ISO file of the Linux distro you want -- saving that to a folder on your drive
2) Run the USB Startup Creator app of your choice (I always use the Universable USB Creator from PendriveLinux) and select the ISO file you just downloaded
3) The app will extract the files and folders from the ISO file and write them to the USB stick.

^^^
This. ;)

---

### Post by Camilia on 2014-12-29
I downloaded ubuntu and Pendrivelinux onto usb drive.
I opened the Pendrivelinux.
In Pendrivelinux browse for ubuntu in usb drive but don't see ubuntu
Downloaded ubuntu to documents.
In Pendrivelinux browse for ubuntu in documents but don't see it.
Nothing is working as it should for me

---

### Post by Bucky Ball on 2014-12-29
Well, Pendrive is no good on the USB. You can't make a bootable USB on the USB that you are using Pendrive from. That needs to be on a hard-drive (or, I suspect, another USB). The USB you are burning the Ubuntu ISO image to needs to be totally blank and formatted as FAT32 (generally). Pendrive then burns the image to that. You then boot from the freshly burnt USB and install.

---

### Post by Camilia on 2015-01-25
> **Mark Phelps said:**
> Sorry if I misunderstood what you said, but it reads like you are copying files to the USB -- and that is NOT what you want to do.

The process is the following:
1) Download the ISO file of the Linux distro you want -- saving that to a folder on your drive
2) Run the USB Startup Creator app of your choice (I always use the Universable USB Creator from PendriveLinux) and select the ISO file you just downloaded
3) The app will extract the files and folders from the ISO file and write them to the USB stick.
Well I have been busy getting dental work done. Now feeling good and trying to burn ubunut onto flash drive. 

I was unsuccessful. 
Downloaded ubuntu onto a flash drive H. 
Downloaded Universable USB Creator from PendriveLinux
After clicking create to flash drive F got message - 
Can not open file H:\ubutu as archive.
Also ubuntu-12.04.5-alternativeamd64.iso.torrent is not supported.

Tried it again. This time after downloading ubuntu sent it to flashdrive h instead of dragging it to the flash drive. It appeared to work. Got message that this ubuntu is not supported after burning to usb drive. Read that it is supported to 2017 though.

Download looked successful but desktop not booting from flash drive. Just have a purple screen even waiting for 10 minutes. Seems I will have to give the PC to son-in-law when I visit this week.

Redid it when I was no long angry with the PC and succeeded. Thanks for all of your help.

In need to reinstall ubuntu onto desktop. Tried to reinstall ubuntu with the USB, which had ISO, used previous to put ubuntu on the hard drive. When I started the PC with the flashdrive in the PC started normal. Thus decided to recreate ISO file on same USB. Was unsuccessful. Got message that : There is not enough disk space! 2MB free, 996MB Needed on F:\drive. Doesn't make sense since it is the same USB I used before. What to do next?

Steps
#1 Reformatted the flashdrive on laptop with windows OS.
#2 Downloaded ubuntu from home page
#3 Downloaded Universal-USB-Installer-1.9.5.9u
#4 Opened Universal-USB-Installer-1.9.5.9
#5 Result get message There is not enough disk space! 2MB free, 996MB Needed on F:\drive

---

### Post by Bucky Ball on 2015-04-22
Wipe the drive and create one FAT32 partition that uses the entire drive and try again. Not sure what you are formatting the USB to or what you are using to try and burn the ISO image to USB. Please inform. 

If that doesn't work, wipe the USB drive leaving unallocated space and try again.

---

### Post by Camilia on 2015-04-22
> **Bucky Ball said:**
> Not sure what you are formatting the USB to or what you are using to try and burn the ISO image to USB. Please inform. 

With the flashdrive on laptop with windows OS I just right click on the flash drive. 

When I put the flash drive in desktop with ubuntu OS it shows as if I have 2 flashdrives in the desktop. Unable to reformat on desktop with gparted. With gparted get this message:Partition(s) 1 on /dev/sdb have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.

This doesn't make sense to me for the ISO was burned onto the hard drive. Put the flash drive up after installing ubuntu. What else can I use to reformat the flashdrive?

---

### Post by dino99 on 2015-04-22
formatting a device ONLY works if that device is unmounted first

---

### Post by Camilia on 2015-04-22
> **dino99 said:**
> formatting a device ONLY works if that device is unmounted firstWell I not able to do that as I did in the past with Gformat.
Gfromat gives me message
artition(s) 1 on /dev/sdb have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use. As a result, the old partition(s) 
will remain in use. You should reboot now before making further changes.

I have the option to cancel or ignore. If I ignore then try to unmount I get message:
Could not unmount /dev/sda1

All the previous steps I did to format the USB are not working. I have read that USB is best to download the ISO, for easy to rewrite.

I am beginning to hate ubuntu. My fonts on top bar are very small. I used Tweek program to try to enlarge them. Now word and excel very big. Tweek page so big I can't get to the end of the page to undo the action. Unable to resize it.

---

