---
title: "(Question) Directly editing grub.cfg for background quality &amp; resolution?"
date: 2017-08-10
forum: General Help
---

### Post by brurhh on 2017-08-10
I installed grub2 (I guess?) on a USB drive using 'grub-install' command from a live ubuntu session (16.04) thus creating /boot/grub folder & some grub stuff there, but no grub.cfg file is created, so I borrowed one & put it there (can't remember where I got it)

Because of this there isn't an /etc/grub.d folder nor terminal to set things from there, also grub.cfg won't get updated any time soon so I know I can safely edit it directly.

My problem with this bootloader is the low display resolution & the fact that any background image that I set gets a horrible quality, sharp borders & like 4 or 5 colors but mostly black & white.


Current grub.cfg contents:
insmod vbe
insmod vga
insmod gfxterm
terminal_output gfxterm
loadfont /boot/grub/fonts/unicode.pf2
set gfxmode=1024x768
insmod png
if background_image /boot/grub/background.png ; then
 set color_normal=white/black
 set color_highlight=light-green/black
else
 set menu_color_normal=white/black
 set menu_color_highlight=black/light-gray
fi

set timeout=60

menuentry " " {
etc...


Since I know basically nothing about this, my questions here are:

1. How can I change display resolution?
*set gfxmode= doesnt seem to do anything.

2. How to improve the crappy background quality?
*the .png gets detected & set regardless of the image resolution, but horribly modified.

One solution that I can think is to install a linux system on the usb to have the grub.d files & terminal to modify the grub menu, but I'm sure there should be a simpler & smaller solution.

* I apologize because I tend to write a lot, also because this could be the wrong section, I apreciate any help you could bring.

Thanks.

---

### Post by JKyleOKC on 2017-08-11
Directly editing grub.cfg is hardly ever a good idea, and definitely a BAD one for anyone without lots of experience under the hood, because any error in doing so is likely to make it impossible to boot the system. There's a great little utility called grub-customizer that lets you make all needed changes from a graphic window, and verifies that they don't make the result unusable. You can find it in the repositories (software update) and install.

Meanwhile, you can get to the grub menu, and once there, press "e" to edit the startup parameters. There's also minimal help available; read the hints at the bottom of the grub menu screen.

Fin ally, life will be quite a bit simpler if you install a Linux system on the USB drive so that you have easy access to all its system-maintenance utilities!

Hope this helps a bit!

---

### Post by brurhh on 2017-08-13
Hi! Thanks for your answer, however, once I install linux in the usb & customize the grub menu there, is there any way to remove that system & keep the grub bootloader along with the customizations?

(like deleting everything except /boot ? or copying the necesary files to another partition where I install grub too?)

*by the way I got the resolution working, my only problem now is the background quality.

I ask this because the uses I give to this usb doesn't allow me to assign enough space for a linux system on it:

USB partitions:
1 - Storage (56GB) //FAT
2 - Windows (4GB) //win10 install
3 - Boot (2GB) //grub & linux iso
4 - casper-rw (1GB) //persistent storage for iso

I can resize partition1 to allow a linux install but I already use partitions 3 & 4 to boot a linux system (iso to ram) it would be a waste of space to have another system (that I would not use) using ~4GB just to have a background image during boot.

Using this setup is what fits me best, even though the boot time is a bit longer with toram option.

This is why I asked about editing grub.cfg, even if I screw it up, I can boot linux from my hdd, connect the usb & fix everything from there, no system to mess up, no reinstall, etc.

Again, this would be so easy to solve if I had a system install on the usb, my question is:

If I do that & customize grub to fit my background quality needs, can I delete that system & still have the grub bootloader? (delete it from another linux install)

(I guess deleting linux would not stop grub from booting right? and yes, I mean Delete, not Format)

*Also, is there a reason for the horrible background quality? I use .png, RGB mode & same resolution of gfxmode.

Thanks again.

---

### Post by jsmolka on 2017-08-13
> **brurhh said:**
> Also, is there a reason for the horrible background quality?

Hi! Just an idea ... 

-------- 
 The 'set gfxpayload=keep' facility in GRUB provides smooth graphical handover to the Linux kernel. Unfortunately, this does not work on all systems, resulting in a black or corrupt display. This package provides a blacklist of PCI IDs which fail.

 We maintain this separately from GRUB because it is likely to be updated on a different schedule.

 Canonical provides critical updates for **grub-gfxpayload-lists** until .
--------

---

### Post by oldfred on 2017-08-13
You can just install grub to just about any format on any device.
I have installed it in BIOS mode to NTFS & ext4. And installer is FAT32 with a limited grub just for booting USB flash drive in UEFI mode.

I have in past just installed grub and then had to manually create my own grub.cfg & maintain if changes. But that was mostly for using grub's loopmount to directly boot ISO, but I often added a boot stanza for an install or internal drive. Have not tried using flash drive to boot my UEFI system, though.

       Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

 [http://askubuntu.com/questions/848119/how-to-update-grub-on-a-dual-boot-machine/848614#848614](http://askubuntu.com/questions/848119/how-to-update-grub-on-a-dual-boot-machine/848614#848614)
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
Colors only edit
sudo -H gedit  /lib/plymouth/themes/default.grub

---

