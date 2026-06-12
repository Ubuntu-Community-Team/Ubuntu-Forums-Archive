---
title: "ubuntu 16.04 boot issue"
date: 2017-05-14
forum: General Help
---

### Post by pagno2 on 2017-05-14
Hello
I have a triple boot ubuntu 16.04, ubuntu 17.04 and windows 10.
I set the bios in order to boot with ubuntu and then choose one of the three different OS.
Two issues:
1. during boot a black screen appears (see attached jpg) saying "failed to claim resource 1 ..." then nothing really happens as I can enter the grub menu and choose the OS to start with
2. the ubuntu 17.04 is top of the list, don't know how to change and let automatically boot with 16.04 (actually third of the list).
GA

---

### Post by oldfred on 2017-05-14
Is this UEFI boot?
It sounds like an error on Windows and then booting into Ubuntu.

In /EFI/ubuntu is a 3 line grub.cfg if booting with UEFI. That controls which version of Ubuntu it searches for to find rest of grub.
Or you can change default boot in grub menu. But would be booting from the one in /EFI/ubuntu/grub.cfg.

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by pagno2 on 2017-09-05
Hi oldfred
sorry but I am quite a newby.
I neither know what EI/UEFI is nor how to check the details.
GA

---

### Post by oldfred on 2017-09-05
Please use Ubuntu live installer and add the Boot-Repair ppa and run it. 
Link above has details on using ppa and Boot-Repair.

---

### Post by pagno2 on 2017-09-05
This is the link that came out
[http://paste2.org/](http://paste2.org/)
looks too short to me
GA

---

### Post by pagno2 on 2017-09-05
Ok I did it again and a long txt window popped out.
It looks like it has interesting information. It is very long though.
Should I paste it all here or only a part of it?
GA

---

### Post by oldfred on 2017-09-05
If it did not give a unique id/auto upload into pastebin, manually copy it to a pastebin site. 
Best to see entire report and usually too long to post.

---

### Post by pagno2 on 2017-09-05
published on my site

[http://www.ilnaturalista.it/uploads/2/3/0/2/23021194/boot_test](http://www.ilnaturalista.it/uploads/2/3/0/2/23021194/boot_test)

---

### Post by oldfred on 2017-09-05
You need to understand difference with UEFI & BIOS.
  UEFI boot: how does that actually work, then?
[https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/)
[http://blog.uncooperative.org/blog/2014/02/06/the-efi-system-partition/](http://blog.uncooperative.org/blog/2014/02/06/the-efi-system-partition/)
[http://superuser.com/questions/496026/what-is-the-difference-in-boot-with-bios-and-boot-with-uefi](http://superuser.com/questions/496026/what-is-the-difference-in-boot-with-bios-and-boot-with-uefi)
~/Documents/LinuxDocs 


 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
Your install in sda6 17.04 shows mounting of the ESP - efi system partition which is your sda2.
But your install in sda8, does not show mounting of ESP. And you have grub installed to MBR and a bios_grub partition.
Or 17.04 is installed in UEFI boot mode and 16.04 is installed in BIOS boot mode.

UEFI & BIOS are not really compatible. Or once you start booting in one mode you cannot switch modes. Or grub can only boot other installs in same boot mode.

You can dual boot with one UEFI and one BIOS, but have to only boot from UEFI boot menu, often f10 or f12, check your manual. 
But really better to convert 16.04 to UEFI boot mode. You can use Boot-Repair from 16.04 and do a total un-install/reinstall of grub2. BIOS used grub-pc and UEFI uses grub-efi-amd64.

Another issue with more than one Ubuntu install in UEFI mode is that in the ESP is only one /EFI/ubuntu folder. So most recent install will be default boot. But only difference is a 3 line grub.cfg in the /EFI/ubuntu that refers to full grub.cfg in an install.
Suggest backing up ESP before any changes. But I have restored /EFI/ubuntu/grub.cfg and manually edited the grub.cfg to change default boot. And then use grub.cfg from default install to boot other Ubuntu installs.

---

### Post by pagno2 on 2017-09-05
How about just erasing the 17.04 partition? Would it help?
GA

---

### Post by oldfred on 2017-09-05
You can, but still need to convert 16.04 to UEFI boot. Or only boot from UEFI.
Some older UEFI did also require you to turn on/off settings in UEFI to change to CSM/BIOS/Legacy boot. Most now will boot in correct mode just from UEFI boot menu as long as UEFI Secure boot is off.

---

### Post by pagno2 on 2017-09-06
OK
I attentively read some of the articles and since I have two PCs I've decided to use windows and ubuntu separately.
Now I just have to go back to a single OS partition (plus the data dedicated partition) and change the ubuntu 16.04 boot from BIOS to UEFI. Isn't it?
GA

---

### Post by oldfred on 2017-09-06
Yes, you can use Boot-Repair's advanced option to totally reinstall grub. You have to be sure to boot Ubuntu live installer in UEFI mode.

I always  suggest fully backing up Windows, that way if later you want Windows back you can, or if you want to sell system, buyer may want Windows.
One user always immediately removes unused Windows HDD and purchases a new SSD for Ubuntu only. Later sells system with "new" Windows.

If you remove Windows you have lots of NTFS partitions, You may just want to reinstall?

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by pagno2 on 2017-09-10
In the end I decided to erase the disk and fresh install ubuntu 16.04.3.
Is EFI synonymous with UEFI? In the install process no UEFI was available.
GA

---

### Post by oldfred on 2017-09-10
EFI is the original version released by Intel & used by Macs.
UEFI is the newer version.

[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

