---
title: "partition problem"
date: 2013-08-21
forum: General Help
---

### Post by brandon6 on 2013-08-21
I am trying to install ubuntu on my new asus notebook. but the first time I tried, it didn't use a big enough partition, so it failed. It left me with all these other little partitions I think, and I am unsure of which ones I can delete, in order to add them back to my window's partition, in order to properly partition it so I can install ubuntu. a screenshot is posted below

---

### Post by oldfred on 2013-08-21
Windows has several required partitions. Do not delete any of these:
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

Also do not use Windows to create partitions for Ubuntu. It cannot create Linux partitions. But do use Windows disk tools to shrink the Windows partition and reboot before install so Windows can update its internal data to its new size with chkdsk.

It looks like d: & e: are RAW which is an unformatted partition in Windows. But Windows cannot see Linux partition so editing partitions with the Windows partition tools can be dangerous if Linux is already installed. Use gparted instead to create partitions.

Make sure you have turned off fast boot or hibernation that Windows always has on.

See link in my signature for tips & links to sites on UEFI install with screenshots so you have a better idea what you are doing.

---

### Post by brandon6 on 2013-08-21
Here are some screen shots of the partitions, when I am in ubuntu. do I need all of those partitions? I've never had any trouble with installing ubuntu on any other computer. So I'm a little lost. Right now I am running a scan on my c Drive. It said there was an error, so it was going to try and correct it. But I don't know if that has anything to do with this.

---

### Post by oldfred on 2013-08-21
Gparted will show an error if you have not turned off fast boot or hibernation. It will also have errors if you did not resize from Windows and reboot so it can run chkdsk. Windows has to be in working order to dual boot with Ubuntu.

Do not install grub to sda7 partition. With UEFI you install to the efi partition. I think if you just select sda with UEFI it automatically uses the efi partition. But if booted in BIOS mode it will then incorrectly install grub2's boot loader to the PBR or partition boot sector of the efi partition. Make sure you are in UEFI mode. How you boot install media is how it installs. If you started with a grub menu and black screen then you are in UEFI mode. If purple screen and accessibility icons then you are in BIOS mode.

What partitions do you want for Ubuntu. Default is just / (root) and swap. But separate data or /home is usually suggested.

---

### Post by brandon6 on 2013-08-21
don't know the difference, so it doesn't matter. I am going to be using Ubuntu as my main OS, I am a CS student, and really only need window's, for Office. I am just trying to be careful, so that I don't do something that will mess up the computer. Usually I would just try different things, but I am trying to be extra careful.

---

### Post by brandon6 on 2013-08-21
So can I just shrink my window's partition, and put ubuntu on there? instead of messing with my other partitions? Because I'm pretty sure I'll end up doing something wrong.

---

### Post by oldfred on 2013-08-21
Use Windows to shrink the Windows main partition. And reboot several times so it can update size by running chkdsk.
Then you should be able to install in the unallocated space. Auto install will just create / & swap. If you want separate /home or data partitions you have to use Something else or manual install.

---

### Post by brandon6 on 2013-08-21
What mount point do I want to use? I think I may have it working, once I select this.

---

### Post by brandon6 on 2013-08-21
I picked / as the mount point, and it said it successfully installed, but I can't boot into it. My window's partition is still fine. When I am looking at the partitions on window's, there is a new one 'f' drive. and it is not formated. Do I need to format it and do it again?

---

### Post by oldfred on 2013-08-21
Do not attempt to do anything from Windows, it cannot see Linux partitions. 

You should be able to go into UEFI menu and choose ubuntu. Some examples others have posted.

---

### Post by brandon6 on 2013-08-21
not trying to do it through windows, I am doing it through the ubuntu installation. it shows that ubuntu is on there, on the partition that I created, after freeing space. But I think the mount point i chose was wrong, because when it boots, it just boots into windows 8, without giving me a choice. write now, I am in the  installation type menu, and I have the partition selected.  what should I select for use as? right now i have it as ext4, Than I checked format partition, and I don't know which to chose for mount point.

---

### Post by oldfred on 2013-08-21
Ubuntu needs as a minimum two partitions. One is / (root) and the other is swap.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by brandon6 on 2013-08-21
I didn't do anything through window's besides free up space.  right now I am in the installation type menu, and I have the partition selected that I want to use. I have the edit partition box up, and I need to know what option I should chose for 'Use as', right now I have it as ext4, and I have formate partition checked, then I need to know what to pick for 'mount point' right now I have / chosen.

---

### Post by brandon6 on 2013-08-21
Right now, I am in edit partition, for the selected partition that I want to use. I need to know what to select for 'usa as', right now I have ext4 selected. I have formate partition checked, and I need to know what to select for 'mount point', right now I have / selected.

---

### Post by brandon6 on 2013-08-21
sorry, thought my post weren't going through. didn't see the second page at the bottom.

---

### Post by brandon6 on 2013-08-22
I was successful in installing ubuntu, I reinstalled it, over the free space I allocated, that said ubuntu was on. I got the menu that ask me what I want to boot into, and when I pick ubuntu, it works fine. but when I pick window's 8, I get an error. I can boot into windows, if I go into the system setup, and change windows to the first boot option, but than it just boots straight into windows. I can live with this, seeing as I will mostly be using ubuntu, but just curious. Is there a way around this so that I don't have to change the boot order each time?

---

### Post by oldfred on 2013-08-22
There is a bug in grub2's os-prober that only creates the old BIOS style chain load entries which will not work with UEFI. Bug report has manual methods to add correct chainload or you can just use Boot-Repair and it will add correct entries.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

