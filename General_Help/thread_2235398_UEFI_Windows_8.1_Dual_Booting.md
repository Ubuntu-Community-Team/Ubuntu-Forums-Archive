---
title: "UEFI Windows 8.1 Dual Booting"
date: 2014-07-20
forum: General Help
---

### Post by Spirrwell on 2014-07-20
Alright, I've looked around, and I know there's a decent amount of information on this already using boot-repair and etc. However, I haven't gotten it to work. Originall I was dual booting Windows 8.1 and SteamOS, each on their own separate hard disk. Which when I did that, I had to do a lot of work to make it work properly with the U-EFI stuff. I actually would manually boot to the SteamOS hard drive and just by default boot into Windows, which I like. But I decided to try out Ubuntu 14.04, as SteamOS is still a bit painful to work with at the moment.

I completely eradicated my SteamOS HDD and replaced it with Ubuntu. I knew I shouldn't have trusted the automatic way. As it installs GRUB to each hard drive. So now I'm stuck in Ubuntu... I've tried boot-repair, sudo update-grub, and even switching back to U-EFI+Legacy in the BIOS to boot the Windows 8 DVD to try fixing it there with bootrec /fixmbr, to no avail. Also, I believe I may have screwed something up with the boot-repair. I don't know. 

Here's some screenshots of GParted, as I'm really lacking in knowledge as to how this is fixed. I'm not familiar enough with how the whole EFI thing works. Also I apologize for the large image size right now, as I'm not sure if the Ubuntu forums automatically shrinks it down.

[IMG]http://i.imgur.com/EJX4Kys.png[/IMG]

[IMG]http://i.imgur.com/74uQSdi.png[/IMG]

Really, any guidance on how I could at least boot back into Windows 8.1 would be largely helpful. Also I did disable fasboot in Windows 8.1 a while back before I installed Ubuntu, because I know the problems it causes... I've experienced them before. Also I noticed that the boot-repair program appears to have one of those copy+paste links for information, so if I should attempt a boot-repair again, let me know, and I'll add the link. Any help is appreciated!

---

### Post by slooksterpsv on 2014-07-20
Your EFI partition is on the second drive... if you reinstalled Windows 8.1 and didn't do EFI it should have created the MBR information on there. Now I suspect that isn't the case in this situation, here's a few things you can try:
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

You'll have to either point the EFI to the /dev/sdb drive, or do a complete reinstall. Unless you could get 100+MB behind the /dev/sda partition and create an EFI partition and recreate it in the steps in the post above. Try that.

---

### Post by Spirrwell on 2014-07-20
Thanks I'll look into that, but I was wondering if it was possible that with boot-repair I screwed it up? Because there's a 128 MB partition for Windows already and it's an "unknown" filesystem. Now it doesn't suprise me that there would be something like that for system reserve, but I thought that was usually FAT32... I could be mistaken, rather tired. But thank you! I'll look into it some more!

---

### Post by slooksterpsv on 2014-07-20
Ahhh that unknown partition could be either the Q: partition or the EFI, I'm betting on the Q: the reserve partition Windows creates. If you run boot-repair, and just gather the info that'll give us more insight on what that partition is.

---

### Post by Spirrwell on 2014-07-20
Alright, as requested, I attempted another boot-repair and here was the final output from it:
```
An error occurred during the repair.

Please write on a paper the following URL:
http://paste2.org/992D7IaU

In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com 

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (250GB) disk!

The boot files of [The OS now in use - Ubuntu 14.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)
```

In case you pass it in that block of text there, the paste link for the output is here [http://paste2.org/992D7IaU](http://paste2.org/992D7IaU)

Also I took a screenshot of where I believe I might have messed things up initially. Originally, when I used boot-repair I wanted to go the automatic route. However it complained about GPT being detected and whatnot. It still does this and I have to modify the advanced settings to this in order for it to work:

[IMG]http://i.imgur.com/z9M0snY.png[/IMG]

Also, I have tried changing the OS to boot by default thing, to Windows, however this didn't do a bit of good either.

Here are my system specifications in case they are needed for any reason.

[COLOR=#FF4500][FONT=Verdana]MOBO: MSI Z87M GAMING[/FONT][/COLOR]
[COLOR=#1E90FF][FONT=Verdana]CPU: Intel® Core&#8482; i7-4770K[/FONT][/COLOR]
[COLOR=#32CD32][FONT=Verdana]GPU: EVGA GTX 660 Ti[/FONT][/COLOR]
[COLOR=#FF0000][FONT=Verdana]RAM: Ripjaws X 8GB (2 x 4GB) DDR3 2133[/FONT][/COLOR][COLOR=#FF0000][FONT=Verdana]MHz[/FONT][/COLOR]

---

### Post by slooksterpsv on 2014-07-20
From all of that information, it's not finding a Windows EFI Boot. My scope on modifying the EFI Partition is limited, but if the contents of the EFI partition contains elements for the Windows EFI and can point it to the other HDD, you may be able to resolve it without needing a Windows 8 DVD/USB. My suggestion is if you have a Windows 8 DVD or USB to boot from it and try to repair the EFI for Windows. Again I'm limited in helping on that matter.

---

### Post by oldfred on 2014-07-21
Typical Windows UEFI partitions. The msreserved partition is unformatted space that you do not normally see, but is required by Windows. Since unformatted gparted & other tools have issues with it and may show errors due to lack of formatting. If booting grub from gpt with BIOS a bios_grub partition is also unformatted space and gives the same errors.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

With gpt Windows only boots in UEFI mode.
But Windows will install its boot files to the drive set as boot in UEFI/BIOS. So if you installed Windows to your 1TB drive but had the 250GB drive set as boot in UEFI/BIOS Windows may have put the efi partition with Windows efi boot files on it. Then you may have erased that with the Ubuntu install to the 250GB drive.

Sometimes it is better to physically disconnect a drive to make sure a system cleanly installs to only that one drive. And that is what you want so if one drive fails you can still boot the other from UEFI/BIOS boot menu or one time boot key.

I suggest an efi partition on every drive for that reason. And make sure when you install that the boot loader is installed to that drive. With Windows it is setting default drive before install. With Ubuntu you have to use Something Else and specific which drive to install boot files into. All auto installs with Ubuntu install boot files to drive seen by UEFI/BIOS as sda. And some promote a flash drive to sda which really confuses things as installer is then corrupted (as installer) and is required to boot internal system.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

