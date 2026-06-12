---
title: "Problem with HDD and booting. Error: hd0 out of disk."
date: 2012-12-19
forum: General Help
---

### Post by 1grouchy on 2012-12-19
Hello guys, need your help.

Some time ago problem started to happen with HDD. When I try to boot to Ubuntu he informs me that check disk is needed, and sometimes I must do it manualy fsck to finish the boot.

Now, its bigger problem. After a 10 min of booting and only blank screen I shut it down with power button. Now I have following errors:

Boot From BBS-HARDDISK...
error: hd0 out of disk.
error: no suitable mode found.
error: no video mode activated.

After I skip that, I got BLACK SCREEN GRUB (not regular) with options:
to start one version of kernel only
and 
recovery for that version.

Neither option is not working. Only get message:

error: hd0 out of disk.
Press any key to continue... and when I press it then machine freeze


When I try to enter grub rescue and type "ls" i got message:
error unknown filesystem.

Over and over...

Any idea about how to solve this problem.

Thanks in advance.

---

### Post by 1grouchy on 2012-12-20
New moments.

I manage to access partitions with Live CD and with fdisk -l command got this output:
[SIZE=2][COLOR=Gray]/dev/sda1   *        2048   157288447    78643200    7  HPFS/NTFS/exFAT
/dev/sda2       157288448   530769919   186740736    7  HPFS/NTFS/exFAT
/dev/sda3       530769920   560062463    14646272   83  Linux
/dev/sda4       560064510   625141759    32538625    5  Extended
/dev/sda5       560064512   567875583     3905536   82  Linux swap / Solaris
/dev/sda6       567877632   625141759    28632064   83  Linux[/COLOR][/SIZE]


I think that Linux is on partition sda3, so I try to reinstall GRUB first.[SIZE=2][COLOR=Gray]
$ mount /dev/sda3 /mnt
$ grub-install --root-directory=/mnt /dev/sda
[/COLOR][/SIZE] 
It says that operation was succesfull, after reboot, same error.

I can do clean installation of Ubuntu and Windows but that is a last option, because I want to learn something, not to avoid problems with solutions like everything from scratch.

So if anyone can help, I will be grateful.

---

### Post by oldfred on 2012-12-20
I would try Boot-Repair which is a gui to do what you just did, but it can also make a report. You might from Boot-Repair try the full uninstall of grub and reinstall of grub.

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemic")

Or manual commands:
       
 Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2 info & full chroot version - also METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD
chroot version:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

