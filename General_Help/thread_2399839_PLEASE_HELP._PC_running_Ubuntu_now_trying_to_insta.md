---
title: "PLEASE HELP. PC running Ubuntu now trying to install windows 10"
date: 2018-08-30
forum: General Help
---

### Post by jayngo23 on 2018-08-30
Hey I've tired multi times. Even with different usb's. I purchased this pc with no OS so I installed ubuntu But my main goal is to run windows 10 fully. My pc right now is running Ubuntu and I just download windows 10 iso from Microsoft page.

I've made the partition in the hdd to install windows 10 but the thing is every time I try and boot my pc using the USB I cannot. I can't ever see the windows setup. When I try it boot pc using USB it just goes to Ubuntu screen

---

### Post by Autodave on 2018-08-30
Hopefully someone else will be able to help you doing what you want to do, but I have never heard of anyone successfully installing Windows when there is another OS already on the disc.  Your best bet is to wipe the disc, install Windows, use the Windows tools to shrink the Win partition, turn off secure boot and fast boot, install Linux.

---

### Post by missmoondog on 2018-08-30
you MUST install windows first then linux. no way around it. once you have windows installed you can install linux and the installer will give you the option of how much hard drive space to use for the linux install. no need to really create a partition for linux before hand even.

you may have to do what Autodave says above about secure boot and fast boot though.

---

### Post by oldos2er on 2018-08-30
Backup any files you want to save now; installing Windows will likely wipe out your current data. I agree with the advice to install Windows first.

---

### Post by HermanAB on 2018-08-30
Simple really.

Install Virtualbox or KVM, then install Win10 as a virtual machine.

---

### Post by monkeybrain20122 on 2018-08-30
> **HermanAB said:**
> Simple really.

Install Virtualbox or KVM, then install Win10 as a virtual machine.

+1

---

### Post by Kris_M on 2018-08-30
download 1803 iso (from MS and boot to it and install windows. I don't know if it will install alongside linux, but it will certainly make it look like linux has disappeared - you will have to run rescatux or the like to re-install grub and get a dual boot linux/win10.  be careul what you tell win while installing or it will happily format the whole HD/ssd.

---

### Post by oldfred on 2018-08-30
UEFI or BIOS?
New hardware will be UEFI, but how you boot install media UEFI or BIOS/CSM/Legacy is then how it installs for both Ubuntu & Windows.
And Windows is very particular about partitioning.
It only installs & boots in UEFI mode from gpt partitioned drives.
And it only installs and boots in BIOS boot mode from MBR partitioned drives.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

While it is possible to install Windows after Ubuntu, you have to understand partitioning and boot modes and some of the limits placed on each.
That is why the standard suggestion and for most newer users, installing Windows first is easiest and then installing Ubuntu in same boot mode is a bit easier.

If high end hardware & not wanting to game the Virtual install is a good option. But system is not quite as fast as you are sharing resources.

---

### Post by olaf.jorgensen on 2018-08-31
This problem i also had before, just download and install woeusb it works every time . 

update: dident read that you want to dualboot, sorry nvm my reply

---

### Post by webmiester on 2018-09-02
> **jayngo23 said:**
>  When I try it boot pc using USB it just goes to Ubuntu screen

Wait, what is on your USB?  Is it Linux.  Because if what is in you USB is a bootable Ubuntu system, then it surely will boot into Linux.

Or did you mean that you placed the windows ISO in the USB, and tried booting from it?  If so it is possible that you computer isn't actually booting from the USB, it is booting off the hard disk with the installed Ubuntu in the hard disk.  In this case, enter your BIOS setup and make sure that USB is the first priority for booting.

If your USB is the priority and you placed Windows ISO into the USB and still not booting, maybe the Windows ISO in the USB is not bootable, so your computer reverts back to hard disk boot up.  Did you just copy the windows ISO into the USB or did you set it up using a disk utility such as "Rufus"?  You might need a program to make the ISO bootable on the USB.  I'm familiar with Rufus but Rufus runs on Windows.  I think Unetbootin might work and I think it has an Ubuntu version, I'm not sure.  But you need a utility like this to make your USB bootable.


What these types of programs do is make the ISO file into something bootable.  A .iso file is not bootable.  If it remains as a .iso, a computer wouldn't know what to so with it when it sees it on bootup, so your computer will revert back to booting from the hard disk. Programs like Rufus will open up the iso file and decompress.some of the files to make a boot partition and other requirements to make your CD,DVD, or USB bootable, so that your computer can boot into it.

Prepare to lose your Ubuntu Partition though if windows installer runs perfectly from the USB.  You can just reinstall ubuntu afterwards, so it's ok 

I hope this helps.

---

### Post by HermanAB on 2018-09-02
Err... Ubuntu ISO files have been bootable for years already.  Canonical did eventually wake up and smelled the coffee...

---

