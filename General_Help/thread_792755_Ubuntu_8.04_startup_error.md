---
title: "Ubuntu 8.04 startup error"
date: 2008-05-13
forum: General Help
---

### Post by jamesn on 2008-05-13
Hi, Im a complete beginner to linux and ubuntu, but I have recently installed from the live cd, and had played around for a bit, getting to know the system. I have dual booted with vista as that is the main OS I use for games etc.

I started Ubuntu today and got this error I was wondering if anyone was able to shed some light or give a fix on this for me:




Booting 'ubuntu 8.04 kernel 2.6.24-16-generic'

Filesystem is ntfs, partition type 0x7

kernel /boot/vmlinuz -2.6.24-16-generic root=UUID=E8B0C331B0C30552 loop=/ubuntu

error 15: File not found

press any key to continue





when I press a key it gives me a choice between ubuntu, ubuntu recovery and mem test ubuntu, all of which give me the same error, the only things i can do is select one of the other two options, that is vista or vista recovery.

Thanks for your help, it seems strange seeing as I have not made any major changes and its just started and i cannot boot into ubuntu now.

---

### Post by housam on 2008-05-13
reinstall [[COLOR="Red"]_grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?")

---

### Post by enbuyukfener on 2008-05-13
Ah, that happened on another computer I installed Ubuntu on, I thought it was because of the constant updating of development kernels (this was months ago on hardy alpha versions).

My fix was to edit the grub menu items and change the partition number which was incorrectly set to 7 instead of 6. I think it is the same numbers on yours judging by the output.

I can't recall exactly how to do it, but I think you highlight Ubuntu in the grub menu, press "e" to edit and change root hd(0,7) to root hd(0,6) and then press enter and then "b" to boot into the system. To make the change permanent, edit the /boot/grub/menu.lst file or download the startup-manager package and set it through its GUI.

EDIT: Or what housam said if the above doesn't work or if you don't want to bother with it :D

---

### Post by jamesn on 2008-05-13
ok, tried the second reply, but couldnt find the option, going to try the grub method now, thanks very much for your help, I will see what happens.

---

### Post by jamesn on 2008-05-13
Sorry Im a bit confused, when i boot from the live cd i tried 

find /boot/grub/stage1

but it gives error 15 file not found

i assume this is because it is the demo of ubuntu maybe?

I wanted to keep the windows bootloader rather than grub, but the directions dont seem to help, this is what i tried:


"Preserving Windows Bootloader

The method shown above puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root partition. But you probably won't want that, if you use a third-party boot manager like Boot Magic or System Commander. (The original poster also suggested that this would be useful to restore the Grub menu after a re-ghosting.) In that case, use this alternative.

This alternative, used without a third-party boot manager, will not cause Ubuntu to boot.

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines. Note that you should have mounted the partition which has your Linux system before typing this command. (e.g. In Knoppix Live CD partitions are shown on the desktop but they're not mounted until you double-click on them or mount them manually)

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD. "

and step 4 gave the error response. Is there anything I can do short of reinstalling? Im just super confused about how grub works, I didnt partition, I installed inside windows if that helps at all. I got confused on the partitioner, as I say Im very new to this.

---

### Post by housam on 2008-05-13
try to inter the grub page using sudo :
```
sudo grub
```
then :
```
find /boot/grub/stage1
```
it should give you a result as (hd0,1)or something like that.

Also post the result of :
```
sudo fdisk -l
```
where -l is a small L

---

