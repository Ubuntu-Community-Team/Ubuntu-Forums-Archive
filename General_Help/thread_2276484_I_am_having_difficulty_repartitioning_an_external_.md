---
title: "I am having difficulty repartitioning an external hard drive"
date: 2015-05-02
forum: General Help
---

### Post by swampwiz on 2015-05-02
Here is my situation.  I am a usual Windows, and only use Ubuntu or other Linux stuff when I absolutely have to.  I used GParted to change from my system's Window 8 OS to Windows 7, and I had to do it by using Tuxboot to create a bootable stick drive.  I have also made a stick drive for Ubuntu.  (Is there anyway to run GParted via Ubuntu?)  Anyway, this disk has some type of corruption problem, and virtually every freeware application that supposedly can recover data simply locks uphangs.  Even File Explorer hangs up when the icon for the hard drive is clicked!  Fortunately, I had just done a big backup to another drive, and only had a few new files that I needed to recover, which I was able to do with an app that only limits to 1 GB (which was enough for me!)  Unfortunately, those apps only do flie recovery, and not partitioning.

So, I want to use the hard drive again.  I should say that when in Ubuntu, this drive does not have any problems.  Unfortunately, when I use the Tuvxboot-GPartedLive stick drive (which is set to automatically execute GPartedLive), GPartedLive hangs!  All I need to do is to partition this hard drive in NTFS.  I would even do in Windows, but it seems that I am running into the same hang problem with apps that are supposed to be able to do partitions!  It seems that Ubuntu is the only OS that recognizes the partition on this drive (although I would like to completely clean this drive.)

I welcome any advice.  I should be considered someone who would need to read "Linux For Dummies" to understand any jargon or commands.  Many thanks

---

### Post by sudodus on 2015-05-02
The boot stick for Ubuntu can be used to run Ubuntu live (for testing), and to install Ubuntu into an internal drive, and it can be used to repair the system in an internal drive. ***Gparted*** is already installed in the boot stick for Ubuntu, so it is easy to start using it :-)

There could be hardware problems (a bad disk, bad electronics, bad RAM memory) as well as software problems (for example a corrupted file system), that makes it hard to manage the internal drive. You can start checking the S.M.A.R.T. information (in the BIOS/UEFI menu) or with some linux hardware, for example you can install smartmontools (temporarily into the live Ubuntu system) and run smartctl.

---

### Post by swampwiz on 2015-05-03
How do I access GParted from Ubuntu?

---

### Post by pmi2 on 2015-05-03
It might be a good idea to first verify that you can actually boot and run Ubuntu from the USB stick that you created, including some basic programs, like the file manager, terminal, "Disks" etc.  You probably can, but just in case.. ;)

Then, I would use "Disks" (a.k.a. GNOME Disks), to do some simple checks, like look at the SMART parameters saved on your hard drive. 

 The same Disks window that displays the SMART parameters also gives you access to running some simple self tests on the disk, which is something you can do before you run GParted.  The reason for running at least a simple test first, is because using a partition editor on a faulty disk can cause some really bad results...

After that, if GParted is installed on your stick drive, you can run GParted either from the Dash, or by opening a terminal and typing "gksu gparted", and then providing your password at the prompt.

Summary:

1) Make sure you can run Ubuntu from the usb stick
2) Use "Disks" to look at the SMART parameters
3) Use "Disks" to run at least one simple disk test
4) Run GParted only if everything else seems to work

---

### Post by Mark Phelps on 2015-05-03
Did you repartition the drive for Windows using GParted?  And, when you then installed Win7, did you reformat the drive?

If you answered Yes to the first and No to the second, then unfortunately, you probably have an unstable filesystem in Win7.  Even though GParted CAN format an NTFS partition, it is best to use Windows to do that.  

Your best bet at this point would be to reinstall Win7, and this time, either use Windows to create and format the partition, or, leave the partition in place and use the Windows installer to reformat it as part of the installation.

---

### Post by oldfred on 2015-05-03
Also is system UEFI with gpt partitioning? If Windows 8 was original system from vendor then it is.

But default install of Windows 7 seems be be BIOS. You have to convert to flash drive and make a few changes to make it an UEFI installer.
If you let Windows install  in BIOS mode and drive was gpt Windows converts to MBR(msdos) but does it incorrectly. It leaves backkup gpt partition table, MBR has no backup. But then all Linux tools have issues with drive as it is part MBR and part gpt, so assume drive is blank or needs total reformat/repartition. You can use fixparts to repair drive if that is the case.

Post this from terminal in live installer:
sudo parted -l

---

