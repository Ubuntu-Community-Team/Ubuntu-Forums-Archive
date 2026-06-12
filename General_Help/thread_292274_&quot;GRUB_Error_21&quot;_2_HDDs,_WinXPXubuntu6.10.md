---
title: "&quot;GRUB Error 21&quot; 2 HDDs, WinXP/Xubuntu6.10"
date: 2006-11-03
forum: General Help
---

### Post by tdoggette on 2006-11-03
I recently dug up an old Maxtor hard drive (~2700MB) that used to have win95 on it. I slaved it to my main drive, a newish PATA Seagate 200GB with winxp on it, and Windows recognized it fine. I booted into a Xubuntu 6.10 CD and installed to the older drive. The install went fine, everything worked, and when I booted, GRUB gave me the choice of three Ubuntu options and WinXP, both of which worked fine.

Here's where the problem is: I wanted to remove the older drive with Xubuntu on it, but when I did and rebooted, GRUB (which did not, so far as I know, exist on this machine prior to the install), started, but did not load, giving
"Grub loading stage 1.5
Grub loading, please wait...
Error 21". 

I'd really like just to be able to go back to my old setup with one drive with winxp and put Xubuntu on another machine, but I can't because my computer is not dependent on having that old drive attached. If I need to I can just back up the data on the Windows drive and format, but I'd much prefer something easier.

This is my first Linux hard drive install, so forgive any ignorance.

((Google informs me: 21 : Selected disk does not exist. This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.))

---

### Post by Herman on 2006-11-03
tdoggette,
If you think you will be plugging and unplgging hard disks again sometime or installing and uninstalling operating systems often, GAG Boot Manager is a good 'Graphical' boot manager (so it's easy and quick to configure), and it is 'operating system independant, (you can run it from a floppy disk or install it to MBR and the first track of your hard disk, so it isn't affected by partitioning changes, or the presence or absence of any particular operating system). :D For info: [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

Or, you could use one of the methods on this page, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
to 'uninstall' (overwrite) Grub's code in your MBR with code to make the MBR point to your Windows bootloader again like before. There are several methods there that should all work, just pick one you like. :D

Finally, you should have a copy of Super Grub Disk around whenever you are working with bootloaders and installing/uninstalling O.S.es, it has the most comprehensive collection of tools yet available for making this kind of work easy, more info, [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Regards, Herman

---

### Post by closer9 on 2006-11-03
If you just want windows on that computer... you need to restore the windows mbr.

Taken from: [http://www.techzonez.com/forums/archive/index.php/t-3975.html](http://www.techzonez.com/forums/archive/index.php/t-3975.html)

"Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer."

Just to be safe make sure your second hard drive is not installed... just the one with windows on it.

---

### Post by h4mx0r on 2006-12-16
I happened to do something similar when installing xubuntu. I had a 250gb HD slave I used for storing multimedia stuff on (hdb), but I wanted to format it and install xubuntu while keeping my previous separate 41gb HD with windows xp (ntfs on hda). The livecd worked perfectly and I ran the install script on desktop. It mentioned something about hd0, don't know what was that. So after I get done I restart computer and on boot it shows only the "GRUB Error 21", no menu at all.

---

### Post by Herman on 2006-12-16
Hello h4mx0r,
It seems as if Grub's stage1 and stage1_5 have been written to the first hard disk alright, but they can't find your second hard disk. The second hard disk's Xubuntu install will have inside it the necessary stage2 files of Grub that are needed for Grub to be able to do anything.
You should be able to use a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") CD-ROM or floppy disk to boot either operating system with for now. That should make you feel a lot more cheerful and also help us find out what might be wrong and maybe even fix it.
250 GB is a nice large hard disk to be added to a machine that came with a 41 GB hard dsk installed.  Would the BIOS date in this computer be earlier than 2002? (You can check that by entering the BIOS and looking in 'product information' or something similar. I am thinking of the 137 GB or 268,435,455 LBAs limitation (28-bit limit)....(September 2001). Could that be possibly anything do do with your problem?
Sometimes the disk is still okay for data or for running an OS that is inside the 137GB limit. 
Is Xubuntu occupying the whole disk or situated at the beginning of the disk, or is in way at the other end, where the BIOS might not be able to 'see' that far?
I'm just guessing here, but I'm trying. If you had a running Xubuntu, or a Linux LiveCD of some kind, I'd be able to ask you for the ouptut from 'sudo fdisk -lu' and other diagnostic commands. This is the best I can do for now.
Regards, Herman :D

---

### Post by manpreet on 2006-12-26
Hello all.  New to Ubuntu and Linux...sorry to say it took me so long, but HEY I'm trying!

I have a similar story: I have a laptop with WinXPPro and a USB HD that wasn't being used so I thought I would be "brave" (maybe stupid) and tried installing KUBUNTU on it. I checked the BIOS and it appeared that I COULD boot from removable media so I figured what the heck.  Well, now even with the drive on and running (the external HD with Kubuntu) I got the error 21 message.  I decided, ok, time to panic.  I installed GAG and I can eventually get back to the original Windows desktop but I am unable to remove GAG because I will not use Kubuntu this way (I am installing it on another dedicated laptop). I have read all over that it's simple to uninstall GAG using a floppy, but 99% of newer notebook pc's do NOT have floppy drives!  What would I do in that case to remove GAG?  I am in the sad state of creating "restore/recovery" CD's from the VIAO as it did not come with the original CD's, instead, it's some built in recovery Windows program...so I don't even think I will have the ability to use the FIXMBR option.  Any advice?

---

### Post by dquinn on 2008-02-18
Hi

Similar problem, after successfully  installing dual boot xp pro / ubuntu on my laptop, decided to add a large sata disk to kids system and then install ubuntu dual boot to that. Sata installed fine under xp pro and i than booted from  live cd-rom to install unbuntu.  Everything seemed to go fine, but when I rebooted,following the ubunto logo screen it just sat there with a black screen.  I then tried to reboot from xp disk and get grub error 21.   Problem is it also wont boot from live cd now.  

I've now tried to remove the SATA disk, but still get error 21, and live cd still won't boot.   Please help before my kids lynch me.

---

### Post by strabes on 2008-02-18
You can reinstall grub using the link in my signature.

---

### Post by dquinn on 2008-02-19
Hi 

Thanks for the advice, my problem is Ubuntu won't now boot from the live CD.  It tries and reaches the Ubuntu logo , but the screen then just goes black.

Any suggestions welcome.

Regards

---

