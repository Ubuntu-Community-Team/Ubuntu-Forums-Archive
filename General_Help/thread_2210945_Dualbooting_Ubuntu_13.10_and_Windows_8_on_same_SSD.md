---
title: "Dualbooting Ubuntu 13.10 and Windows 8 on same SSD"
date: 2014-03-13
forum: General Help
---

### Post by KillEmAllx on 2014-03-13
So I have a Zenbook UX32A I bought 3 months ago with Windows 8, which I replaced with Ubuntu 13.10 first day I got it. However, I now need Windows for some programming, minor games and other stuff, so I decided to dualboot.
The laptop has a 128GB SSD, so I was thinking to split it in half. I wiped the disk, partitioned it in two and installed Windows 8 first, and everything went smooth. However, when I was about to install Ubuntu I did not get an option to install alongside Windows, I only got to choose between "Erase disk and install" and "Something else". I didn't want to make partitions for Ubuntu manually (I'm no expert) so I did some research and didn't found any guides or tutorials showing what to do, besides a site saying that you can install Ubuntu and then Windows and then just repair boot.
So I erased the disk again, splited the SSD in two partitions, installed Ubuntu in one partition first and then Windows in the other and then repaired the boot using a live Ubuntu usb and boot-repair. Everything went as expected and I now have a dualbooting laptop.

My questions are:
Is there any better method for doing this? Why didn't Ubuntu detect my Windows installation? Will the systems "kill" eachother and eventually crash by using this method or am I safe?

I started this thread to share what I did and what worked for me, to help people that want to do the same thing. If I had found a thread/guide/tutorial showing how to dualboot if you get no "install alongside option", I would have spared myself hours of frustration.
Cheers!

---

### Post by JayKay3OOO on 2014-03-13
System will never kill each other as they are separate entities that don't understand one another.

Easiest thing for anyone not sure about ubuntu is to either run it in a virtual machine (from windows) or using the application wubi (found inside the ubuntu iso, use 7zip to open the iso and extract the files) to install Ubuntu as an application inside Windows 8. You'll be able to remove it like a normal application too and boot to windows or ubuntu at computer boot without it ever making partitions. It means that if you get bored of having ubuntu then just remove it like any other application on the system.

Ubuntu will have similar performance using this method and you only need make it 20 or 30GB.

---

### Post by oldfred on 2014-03-13
When you reinstalled Windows 8, did you install in UEFI boot mode or BIOS boot mode?
Windows only boots from gpt with UEFI and from MBR(msdos) with BIOS.
Ubuntu will boot from gpt drives with UEFI or BIOS if correct partitions are on drive.
Both Windows & Ubuntu only boot from MBR  with BIOS.

But if drive was gpt and you install Windows in BIOS mode, it converts only part of gpt to MBR. It leaves backup partition table and then Linux tools see both MBR and gpt and get confused. Then installer only offers total reinstall.

Post this to see current partitioning. 

sudo parted -l

---

### Post by KillEmAllx on 2014-03-14
> **oldfred said:**
> When you reinstalled Windows 8, did you install in UEFI boot mode or BIOS boot mode?
Windows only boots from gpt with UEFI and from MBR(msdos) with BIOS.
Ubuntu will boot from gpt drives with UEFI or BIOS if correct partitions are on drive.
Both Windows & Ubuntu only boot from MBR  with BIOS.

But if drive was gpt and you install Windows in BIOS mode, it converts only part of gpt to MBR. It leaves backup partition table and then Linux tools see both MBR and gpt and get confused. Then installer only offers total reinstall.

Post this to see current partitioning. 

sudo parted -l

This is the output:

Modell: ATA SanDisk SD5SF212 (scsi)
Disk /dev/sda: 128GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: gpt


Nummer  Början  ****    Storlek  Filsystem       Namn                          Flaggor
 1      1049kB  512MB   511MB    fat32                                         startbar
 2      512MB   60,6GB  60,1GB   ext4
 3      60,6GB  60,8GB  134MB                    Microsoft reserved partition  msftres
 4      60,8GB  122GB   60,9GB   ntfs            Basic data partition          msftdata
 5      122GB   128GB   6323MB   linux-swap(v1)

Can you please explain? Thanks in advance.

---

### Post by oldfred on 2014-03-16
It looks like both systems are UEFI, best to see all of the details.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by KillEmAllx on 2014-03-17
> **oldfred said:**
> It looks like both systems are UEFI, best to see all of the details.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

I'm not sure if we're talking about the same topic here. My PC works, I can boot to both Windows and Ubuntu. I'm just curious why the Ubuntu installer didn't recognize my Windows installation, and why it didn't show me the "Install alongside" option, as many tutorials and guides suggests. I took a workaround and made two big partitions on my disk, installed Ubuntu, then Windows, then repaired boot with boot-repair and it works, I just want to know why I couldn't do it the simple way... Maybe I'm misunderstanding you, sorry for that haha.

---

### Post by oldfred on 2014-03-17
Did you leave Windows with fast boot on? That is hibernation.
If Windows needs chkdsk or is hibernated, the Linux NTFS driver will not mount the partition, so then it cannot be seen.
Also systems that have Intel SRT use RAID and that has also caused similar issue as RAID drivers are not in desktop installer.
Sometimes even some UEFI/BIOS settings can cause issues.

---

### Post by KillEmAllx on 2014-03-20
Fast boot was off in BIOS.. What settings in UEFI/BIOS can cause problems? Thanks.

---

### Post by LifeEnemy on 2014-03-20
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

I used the above guide for my computer. It's in a similar situation as yours, dual booting off of an SSD. I have a larger HDD installed as well that's split into ntfs and ext4 partitions for storage for each system. The only change I had to make was to be sure that ubuntu was set to boot off of the SDD instead of the HDD (sdb instead of sda in my case).

Hopefully this helps you or a future searcher.

---

### Post by KillEmAllx on 2014-03-20
> **LifeEnemy said:**
> [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

I used the above guide for my computer. It's in a similar situation as yours, dual booting off of an SSD. I have a larger HDD installed as well that's split into ntfs and ext4 partitions for storage for each system. The only change I had to make was to be sure that ubuntu was set to boot off of the SDD instead of the HDD (sdb instead of sda in my case).

Hopefully this helps you or a future searcher.

Thank you for the link, but I find what I did actually a lot easier. The best thing would be if I could install Ubuntu alongside Windows 8 with the "install alongside" option, but for some reason I don't get that option while installing. This is one thing that could maybe make it harder for the avarage user to switch to Ubuntu.

---

### Post by LifeEnemy on 2014-03-20
I'm surprised you have enough space with 2 OSes on just a 128gb drive. I can't say those instructions are easier than what you did, I just liked them because they're very clear.

It's important to note than you need to install Ubuntu in UEFI (rather than BIOS) mode, or it won't work with the Windows install. For reference.

---

