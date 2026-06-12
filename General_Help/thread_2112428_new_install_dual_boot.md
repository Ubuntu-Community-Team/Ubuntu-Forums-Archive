---
title: "new install dual boot"
date: 2013-02-04
forum: General Help
---

### Post by ewaynec on 2013-02-04
I just built a new computer, Gigabyte motherboard and Intel i5 processor. I started with a fresh Windows 7 installation on a new 1Tbt hard drive then loaded Lucid on the old 500 Gbt hard drive, also a fresh installation. I had 7 working good before starting the lucid install. Lucid installed and worked, but now there is no windows. I could not get it to boot. I tried everything I can think of or find searching the web. I found several repair disc for lucid. I tried loading 12.04, 32 bit and 64 bit, also 10.04 32 bit and 64 bit. I have 4 different repair disk with utilities to fix Grub, and they all work. but when I get Ubuntu working I lose Windows, then I repair windows and lose Ubuntu. I have gone back and forth for nearly 2 weeks. I don't remember what I have not tried, I have tried so much. It's not supposed to be this hard. Until I get some viable ideas on what to do next I will leave it as it is now, with Windows 7 working. 
  BTW the last thing I tried was to put Both on the same hdd. I split the 1Tbt hdd and put both OS's on one drive, that is where it is now.

---

### Post by oldfred on 2013-02-04
If it is an i5 processor, your motherboard is probably UEFI/BIOS or it can be either one. 
Both Windows & Ubuntu install in UEFI mode if the install media is booted in UEFI mode or install in BIOS mode if you boot in BIOS mode. But both have to be installed in the same mode to dual boot.

Best to see details from BootInfo report:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by ewaynec on 2013-02-05
Oldfred,
  I read very carefully your post and the links you provided, as well as some more things I found along the way. As of right now I have neither OS working. Windows will not load, and when I try the recovery, it says the files in the recovery do not match the ones on the disc. It is the same disc I just loaded Windows with. I made a "repair disk" and it will not load, It says disc error.
  Linux, I have in front of me seven bootable repair disk for Linux, and none of them work. Most of them put me back to "Grub Rescue", whatever that is, I cannot find any help for it.
  I think you were on to something about the Bios/UEFI, it changes almost every time I re-boot. On the boot options menu there are sometimes 6 choices for boot options as well as different options for HDD, CD, Network. One time there was only one choice for boot options and none of the others. I tried every combination of options I could think of, with no good results.
  Right now I have removed 10.04 from the 1Tbt hdd and installed 12.04 64 bit on the 500gbt hdd. I am about ready to re-install windows and completely remove linux. 
  From what I have been reading about Grub, no one knows why it works or how to fix it. everything is "try this and see if it works, if it doesn't file a bug report". That is just not good enough.
  Is there anything I haven't tried yet?
     Wayne

---

### Post by oldfred on 2013-02-05
If you have installed Ubuntu 12.10 it will work with secure boot. I think UEFI was only starting to work with Ubuntu with 11.10. The LTS version 12.04 will get update to the same grub version as 12.10 with the next point release in about 2 weeks.

Not sure how you installed Windows. BIOS or UEFI.

Post link to BootInfo as it will show details of your install. Yes with UEFI and secure boot we are learning. And every vendor has idiosyncrasies than can make it "fun" to try to figure out issues. 

Even you may not think you are booting and then you may run into video issues or other boot parameters that prevent a full boot.  But almost every system can be made to work.

---

### Post by ewaynec on 2013-02-05
I tried the 12.10 secure boot with boot repair. It would not let me by the "no internet", so I can't send the bootinfo. I read where it was possible to go on without Internet but I never found a way, and when I tried it closed. The internet driver is a tarball, so...
  I don't know how to tell if Windows or Linux is installed UEFI. I just installed it and I don't remember either asking. I thought UEFI was a boot system, Like BIOS. How do I load any system in UEFI or BIOS?
  I am too stubborn to give up on this, but I am close.
    Thanks, Wayne

---

### Post by oldfred on 2013-02-06
With UEFI you should see multiple boot options. With BIOS it used to be just hard drive, DVD or flash. 

In UEFI menu you should be able to turn off secure boot. Some have a UEFI on setting which means UEFI without secure boot and that turns off secure boot. Some also have a BIOS boot setting which may not work if secure boot is on as there is no BIOS secure boot.

But I think most systems will show the Ubuntu install flash drive with two boot options, one UEFI/efi and the other legacy/BIOS/CSM or whatever. And how you boot is how it installs.

But it is easier to just have Ubuntu in same mode as Windows as Windows only boots in UEFI mode with gpt partitioning and with BIOS you have to have MBR(msdos) partitioning. So unless you want to reinstall Windows you need to have Ubuntu in same mode. And Boot-Repair can easily convert an Ubuntu install from BIOS to UEFI or vice-versa.

BootInfo report will tell us how you installed. Also if first or second partition is efi and partitioning is gpt then you have UEFI.

This will show how partitioned or you can look with gparted.
       sudo parted /dev/sda unit s print

---

### Post by ewaynec on 2013-02-08
Since your last post I have re-installed both 12.04 and Windows 7, several times. Each time I load Windows I cannot get Linux to work, when I load Linux I cannot get Windows to work. Installing Windows corrupts GRUB. Installing GRUB corrupts Windows MBR. I have removed the drive containing Linux, installed Windows as the only OS and I will leave like that. You can call this solved if you want, but I do not.

---

### Post by ewaynec on 2013-02-08
I have spent the last 2 weeks trying to get this computer set up like I wanted. I have learned some things I didn't know and re-affirmed some things that I did know. Dispelled some things that I thought I knew.
  I learned the next time I buy a computer I will buy one already assembled and working. I learned how to fix the MBR in Windows. I re-affirmed that Linux is not something to take serious. It is fun to play with and interesting to learn, but if you want to use it in any productive way it is a great disappointment. I also know there are a lot of people who do take Linux seriously, but to most it is something to play with. In (almost) every post, the answer to a problem will be, "Try this and see if it works". Most of the time it doesn't.
  I have been using Ubuntu since 7.10, with 8.04 I scrapped Windows and went exclusively Ubuntu. (My wife still used Windows) I have been using computers since the TI-99. My first PC had MSDOS 33. I worked on Computerized Telephone systems (CBX) using UNIX. I made the mistake of thinking that I could use Linux instead of Windows. Windows still does a lot of things that Linux will not, and as aggravating as Windows is, it is more productive and easier to use that Ubuntu.
  As of right now, I have my new computer working with Windows 7. I took Linux out. It is still installed on a hdd lying on my desk. I still have the old computer that I may put it in and play with it some, but Linux will never again be my primary OS. It is just too hard to work with. I think I know quite a bit about computers but I do not want to spend a lot of time "Trying " something when I need it to work now. It is impossible to learn because there are no factual documentation, no set way of doing anything. 
  There are a lot of people who will give help on Linux, and a lot who will offer help and give more problems. When you do a search on a problem, you do not see a answer. You see a lot of people with a similar problem. If I have a problem, I want a answer. There are no answers, only trial and error. A lot Linux enthusiast will say "why don't you go back to Windows?" I say OK!

---

### Post by davidvandoren on 2013-02-08
Best way to install a dual boot on modern pc with two hard drives is to ...
physically disconnect one of the drives and install either system windows or ubuntu.
Then disconnect this drive and reconnect the other. Install the second os and reboot. Finish all updates etc. 
Shut down the pc and reconnect the other drive. 
Now choose your os at boot from the bios or depending motherboard press the F11  or F12 at  boot and choose your drive to boot from.

---

### Post by ewaynec on 2013-02-08
I did exactly as you said, and when I boot, GRUB takes over and does not boot windows and does away with the MBR in Windows. Then I repair the MBR and set that drive in BIOS to boot, it corrupts GRUB. I have to remove the Windows drive to fix GRUB, and I have to remove the Linux drive to repair Windows. I put them both in and boot with the Linux drive (GRUB) and here we go again.

---

### Post by oldfred on 2013-02-08
You never posted the BootInfo report so we could make specific suggestions. 

And if you have UEFI that has made it much more difficult as either Windows or Ubuntu may try to install in BIOS or UEFI and they do not work dual booting then.

---

### Post by ewaynec on 2013-02-08
Now again you are saying I didn't do what you said, when you are the one not paying attention. Neither 10.04 or 12.04 has network capabilities so there is no way to send it. I explained this in an earlier message. I looked for a driver, Atheros says they do not make one for linux, but I did look everywhere I could find and found nothing.
  This is all moot, because I have removed Linux and have no plans to put it back.

---

### Post by oldfred on 2013-02-08
Vendors almost never provide drivers.  Quick goolge search found these two suggestions, but it does not look as easy and automatic as most.

[http://askubuntu.com/questions/205582/how-do-i-get-an-atheros-ar8162-working](http://askubuntu.com/questions/205582/how-do-i-get-an-atheros-ar8162-working)
[http://askubuntu.com/questions/217361/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller-on-64-bit-12](http://askubuntu.com/questions/217361/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller-on-64-bit-12)

---

