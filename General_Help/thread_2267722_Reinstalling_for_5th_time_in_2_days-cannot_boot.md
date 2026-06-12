---
title: "Reinstalling for 5th time in 2 days-cannot boot"
date: 2015-03-03
forum: General Help
---

### Post by Rupsa_Saha on 2015-03-03
As the title suggests, i cannot boot into Ubuntu. laptop (Toshiba Portege R930) contains no other OS, since i deleted everything after dual boot failed. I still cannot get it to boot. If i run live boot from USB, i can see that Lubuntu is installed on the primary partition. Gparted looks like this : [IMG]http://i.imgur.com/SGSYGGF.png?1[/IMG]
 after i used [https://help.ubuntu.com/community/MasterBootLoader](https://help.ubuntu.com/community/MasterBootLoader)
What am i doing wrong?

---

### Post by ajgreeny on 2015-03-03
Why mess around with that link?  Why not just install in the simple way with your live DVD or USB.

I have not read any detail of that link, but as far as I can see your problem is that there is no root partition in your installation; I am not even sure how you managed to get through the install without root defined in the installer first.

Forum member sudodus has put together a very useful thread for users which I think you may find very useful.
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by kerry_s on 2015-03-03
> **ajgreeny said:**
> Why mess around with that link?  Why not just install in the simple way with your live DVD or USB.

I have not read any detail of that link, but as far as I can see your problem is that there is no root partition in your installation; I am not even sure how you managed to get through the install without root defined in the installer first.

Forum member sudodus has put together a very useful thread for users which I think you may find very useful.
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

root's in the encrypted lvm. but yeah weird setup, no need for master boot as it's not multi os setup

---

### Post by Rupsa_Saha on 2015-03-04
Thanks for your replies. I only tried it after nothing seemed to work. Well, that doesn't work too. I tried a fresh install, and boot-repair info is now this : [http://paste.ubuntu.com/10523105](http://paste.ubuntu.com/10523105) Any help from this?

---

### Post by kerry_s on 2015-03-04
your drives a mess. if it was me, when you get to partitioning select manual(something else ?), the last option.
i would keep the first 1 "sda1/vfat" cause that's your uefi boot, the rest i would delete(-), then create(+) 1 partition ext4, mount as root(/) for the rest of the drive. 

that's it click install, keep it simple.

lucky for me my computers old enough i don't have to deal with uefi.

---

### Post by oldfred on 2015-03-04
Your original post shows an efi partition and the LVM install. That is required if you want full drive encryption, otherwise it just is another way to partition that some advanced users prefer.

You now show standard partitions in Summary report, but somehow have grub legacy 0.97 in MBR. I did not then that even worked with gpt partitioned drives and UEFI systems.

Toshiba now are like many others and only boot Windows in UEFI mode. But there are work arounds.  Since you do not have Windows you can just rename grub to read Windows in UEFI, so it thinks you are booting Windows or as those who dual boot you can rename bootx64.efi which is a hard drive boot file to really be grub. Systems seem to "let you" still boot hard drive, so that also works.

Your / (root) also looks a bit small at 10GB. I use about 11GB of my 25GB / partition. But that includes /home which is about 2GB with all other data in data partitions.

          C:  Use efibootmgr if only Ubuntu, not dual boot, install to make Windows UEFI description boot grub or shim file
         sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
       If you have Windows to restore Windows boot entry:
         sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
              A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot
          Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
     Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)
         From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
         sudo mount /dev/sda1 /mnt
         only if /EFI/Boot not already existing, run the mkdir command,
        sudo mkdir /mnt/EFI/Boot
        sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
         If new folder created, the bootx64.efi will not exist, skip backup command
             sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
         make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
             sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi
           
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
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

