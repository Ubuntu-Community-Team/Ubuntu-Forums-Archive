---
title: "Use &quot;dd&quot; within the bootloader"
date: 2015-02-19
forum: General Help
---

### Post by brian48 on 2015-02-19
Hi everyone,

   I know I have managed this before, but I can't remember how and trying to search the web for "dd" next to "bootloader" or "grub" just floods me with the standard use of dd to install or work on the bootloader.
   I have a very specific multiboot scenario involving a corporate encrypted Windows which occupies the entire disk and needs its bootloader untouched in the MBR. I manage to multiboot anyway by switching the first sector of the disk between two versions. I can give more details on this but it is besides the point right now. So, I keep copies of the two versions of MBR in a bootable USB drive and I can switch the computer between one state and the other by copying each file to the start of /dev/sda.
   So, what I am trying to do is accomplish this switch without fully booting a heavy OS (like the live USB). My head keeps circling around the idea that "dd" was available as a built-in command in grub but I see it is not. I can't find it in syslinux or as a com32 module or anything of the sort.
   Ideally the menu of the bootable USB would be something like:

                    - Boot from disk as is
                      (localboot or similar)
                    - Switch to corporate MBR
                       dd if=mbr_corp.bin of=/dev/sda
                       reboot
                    - Switch to personal MBR
                       dd if=mbr_pers.bin of=/dev/sda
                       reboot

   To accomplish this all I am missing is the ability to write the MBR from a file within GRUB (or whatever bootloader). As I said, I know for a fact I used to do this on an older laptop but I cannot, for the life of me, remember how! :)

   Hopefully one of you gurus in the forum can point me on the right direction.

Thanks in advance!

---

### Post by oldfred on 2015-02-19
Why not just keep Corporate MBR in MBR and have Ubuntu MBR in flash drive. Then if flash drive is plugged in you boot it, if not you boot internal drive?

Restore offical MBR, the install Ubuntu to sdb.

       sudo grub-install /dev/sdb

But grub does remember where to reinstall on major updates. You need to check and perhaps change or remove it. If all entries are cleared then the update entry will be empty and no update will occur. 

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by brian48 on 2015-02-21
I found it! it was grub4dos, not official grub that has dd natively as a command!

First of all, thanks for the advice oldfred. That would do fine in a normal partition scenario but here the corporate Windows occupies the entire disk and is encrypted. So, no shrinking of the NTFS partition is possible to propertly install the second OS. What comes next is rated R, I know, but what I did was create a huge contiguous file within the corporate Windows to "reserve" the space, find it's physical location on disk and then hijack that space for the Ubuntu partitions. So, these partitions can never exist together since they would overlap. When in corporate mode, there is only the one huge Win partition and when in personal mode, there is a group of partitions designed to protect the space really used by Win and have ext4 and swap within the hijacked space. This has the added benefit of being relatively stealth while in Windows (except for the one suspiciously large file of course, but when read within the encrypted Windows that shows as garbage), and I also don't need the flash drive to boot each time, just to switch (which I do less frequently than booting).

In any case, if anyone wants more details on this ugly dangerous thing I am doing feel free to ask. My original concern is answered with "grub4dos".

Thank you all.

Bye!

---

