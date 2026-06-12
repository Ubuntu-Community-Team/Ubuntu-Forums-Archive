---
title: "Hard drive not detected by BIOS after wiping it"
date: 2015-05-06
forum: General Help
---

### Post by tech291083 on 2015-05-06
Hi Friends,

I hope this is the right forum for my question. If not, please feel free to move it to the appropriate one, thanks.

A couple of days ago, I wiped one of my SATA hard drives, which I used to dual boot with Windows 7 and Ubuntu 14.04 LTS Desktop 64 bit distro. I used a tool called dBan v 2.8.8 on Ulitmate Boot CD 5.3.3. After successfully wiping it, dBan also indicated it was a success. My hard drive is not detected by my BIOS. When I boot the pc, it shows me an error **[B][B][B]-  reboot and select proper boot device or insert boot media **[/B][/B][/B]I can't install anything on it. My hard drive is also not detected in BIOS even in my friend's pc.

  The drive was is in perfect working condition, bought just over 15  months ago. Size 250 GB, SATA, internal desktop drive. **[B][B]**[/B][/B]

The wipe/erase was done with the following parameters in place.

Entropy: Linux Kernel (urand) 
PRGN : Mersenne Twister (mt9937ar-cok)
Method: DoD Short
Verify: Last Pass
Rounds: 1

In the past I have wiped my other drives with dBan and have been able to install any OS on them after a successful wiping operation. Each time after wiping a drive, BIOS easily detected the drive. My motherboard is **[SIZE=3]Gigabyte H61M-S1[/SIZE]**.

There are 4 SATA ports in total only 1 is showing a SATA device connected to it, which is DVD Writer. Thanks.

SATA 0 : DVD Writer
SATA 1 : Empty
SATA 2 : Empty
SATA 3 : Empty

I tried all the SATA ports, but the hard drive is not detected in BIOS. I changed the boot order many times, but that has got me no where. I took the BIOS battery out, but it did not help either. While booting I hit the F12 button a few times, and it gave me 3 boot options namely DVD Writer, Ubuntu and Enter Setup ie BIOS. I am a bit surprised as to why this Ubuntu option is here instead of my hard drive name/model no. Please visit the url below it has an image of the options that are made  available to the user by hitting the F12 key. In my case there are only 3  options as mentioned earlier in the same order - DVD Writer, Ubuntu and  Enter Setup. The image at url shows many.

[http://s447.photobucket.com/user/CraigWorden/media/boot.jpg.html](http://s447.photobucket.com/user/CraigWorden/media/boot.jpg.html)

I have a couple of other drives with Windows 7, Fedora 20, Puppy Linux on them as the only OS and they are all detected in the BIOS. I read somewhere that Ubuntu adds a secureboot entry to UEFI like many other Linux distros, so if this is true then I am worried as to how get rid of the same from BIOS boot menu list even after wiping it off my hard drive. Is this Ubuntu entry not allowing my drive to be detected in BIOS? My motherboard supports UEFI as far as I know, but how to deal with this issue?

Thanks.

---

### Post by dino99 on 2015-05-06
that drive probably had the 'boot' flag on, so the boot issue.
you need to boot from gparted live (or ultimate bootcd) to set at least 1 primary partition and 1 extended, and rebuid the 'table partition' first. Then installing ubuntu and grub on /dev/sda

---

### Post by tech291083 on 2015-05-06
> **dino99 said:**
> that drive probably had the 'boot' flag on, so the boot issue.
you need to boot from gparted live (or ultimate bootcd) to set at least 1 primary partition and 1 extended, and rebuid the 'table partition' first. Then installing ubuntu and grub on /dev/sda

You are right, but I tried GParted Live CD and it simply did no detect my hard drive, it says no device found. Same with Ultimate BootCD. I have used GParted Live CD many times in the past to creat partition tables. Thanks.

---

### Post by dino99 on 2015-05-06
then unplug/plug back that device (both sata & power connector); then go to the bios to check the hdd settings and sata ones

if nothing works, then the low level format choice can be tried (but not all hdd accept that) to workaround the oem's table customization, or windows modif
[http://www.softpedia.com/get/System/Hard-Disk-Utils/HDD-Low-Level-Format-Tool.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/HDD-Low-Level-Format-Tool.shtml)
[http://en.wikipedia.org/wiki/Disk_formatting](http://en.wikipedia.org/wiki/Disk_formatting)

---

### Post by sudodus on 2015-05-06
I have used ***DBAN*** too (without problems afterwards). It was possible to create a partition table with ***gparted*** (in a live Ubuntu system).

Can you try to connect that drive to ***another computer***? Maybe it will be found, and you can make a partition table (MSDOS or GPT) at least, and after that check if it is recognized by the computer where you want to use it.

---

### Post by oldfred on 2015-05-06
If BIOS will not show it connected to a SATA port, then no operating system will be able to use it. UEFI/BIOS must report available hardware to operating system.

Check connectors both power & SATA, try another one also. 
Or drive just could have failed after all the dban work? Drives do fail, sometimes suddenly.
Were you having issues with drive and is that why you use dban?

---

### Post by tech291083 on 2015-05-06
I have managed to remove the Ubuntu entry from the boot options in the BIOS, which as accessible by pressing the F12 key during booting. Here are the instructions, which are available on the following site. I used a tool called rEFInd.

[http://askubuntu.com/questions/394199/removing-ubuntu-from-uefi-bios-menu](http://askubuntu.com/questions/394199/removing-ubuntu-from-uefi-bios-menu)

> 
    Download the USB flash drive or CD-R version of rEFInd.
    Prepare a medium with rEFInd, as per the instructions in the files you download.
    Boot the rEFInd medium you prepare.
    Use rEFInd to launch an EFI shell.
    Use the bcfg command in the EFI shell to review your boot options. (bcfg boot dump -v should do the trick.)
    Once you've identified your Ubuntu boot option, use the bcfg command  to remove it, as in bcfg boot rm 3 if the Ubuntu entry is #3 in the  list.

Now, after having removed this Ubuntu entry from Boot Options, I have 2 options left. DVD  Writer and Enter Setup. I thought this Ubuntu entry  was the only reason my BIOS was not detecting my hard drive, but I was wrong, the issue  is till there, unsolved. The drive is still not detected in the BIOS. 
Thanks

> **dino99 said:**
> 
then unplug/plug back that device (both sata & power connector); then go to the bios to check the hdd settings and sata ones


I have done this so many times, but no success, thanks.

> **oldfred said:**
> 
Check connectors both power & SATA, try another one also. 


I checked them so many times. Even changes connectors. Plugged my drive into all the 4 available SATA ports, but no success. I have a brand new pair of SATA connectors, which I also tried.

> 
Or drive just could have failed after all the dban work? 


You may be right, but I have wipe many of my drives with dBan and after each successful wipe each of them have been detected in the BIOS without any problems. So a bit difficult for me to digest the fact that dBan might have failed my drive.

> 
Drives do fail, sometimes suddenly.


This might be the last possibility in my scenario. But yes, very possible.

> 
Were you having issues with drive and is that why you use dban?


No, issue at all. Working perfectly alright. 
Thanks.

> **sudodus said:**
> I have used ***DBAN*** too (without problems afterwards). It was possible to create a partition table with ***gparted*** (in a live Ubuntu system).


Yes, I agree 100%. But this time GParted Live CD is not detecting my drive, saying no devices found.

> 
Can you try to connect that drive to ***another computer***? Maybe it will be found, and you can make a partition table (MSDOS or GPT) at least, and after that check if it is recognized by the computer where you want to use it.

No. I tried in another PC of mine and a friend's as well, but it was not detected in both the machines. So no way, I can create a partition table (MSDOS or GPT) as you mentioned. Thanks

Looks like the the ESP (EFI System partition) on the drive, (if any, I am not sure) was also wiped during the wiping process with dBan. So may be re-installing the ESP (EFI System partition), seems to be the only option left. There must be something that can be done here. So many people must be using dBan etc to wipe their drives from time to time, I guess.
Thanks.

Using the Live Ubuntu 14.04 LTS Desktop CD I did the following in a terminal.

```

ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# lsblk
NAME  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0    11:0    1   964M  0 rom  /cdrom
loop0   7:0    0   922M  1 loop /rofs
root@ubuntu:~# 
root@ubuntu:~# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Problem opening /dev/sda for reading! Error is 2.
The specified file does not exist!
root@ubuntu:~# 
root@ubuntu:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.9G   91M  1.8G   5% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           385M 1012K  384M   1% /run
/dev/sr0        964M  964M     0 100% /cdrom
/dev/loop0      923M  923M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           1.9G  1.1M  1.9G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            1.9G   80K  1.9G   1% /run/shm
none            100M   52K  100M   1% /run/user
root@ubuntu:~# 
root@ubuntu:~# gdisk -l /dev/s
sg0       snapshot  sr0       stdin     
shm/      snd/      stderr    stdout    
root@ubuntu:~# exit

```

Thanks

---

### Post by oldfred on 2015-05-07
Even to create the efi partition with gparted or gdisk, the UEFI has to see a drive.
I might then check to see of drive vendor has and tools or info on your issue.

And UEFI does save entries in its own NVRAM, so until you separately delete those, they often remain.

---

### Post by tech291083 on 2015-05-07
> **oldfred said:**
> 
Even to create the efi partition with gparted or gdisk, the UEFI has to see a drive.


Yes, I agree 100%.

> 
I might then check to see of drive vendor has and tools or info on your issue.


My drive is Samsung - 250 GB, Model - SP2504C (Spin Point series, they call it)


> 
And UEFI does save entries in its own NVRAM, so until you separately delete those, they often remain.


I never knew that, thanks.

---

### Post by sudodus on 2015-05-07
> **oldfred said:**
> ...
I might then check to see of drive vendor has and tools or info on your issue.
...

+1

Something unusual happened to your hard disk drive. Maybe the vendor has a tool to restore it.

---

