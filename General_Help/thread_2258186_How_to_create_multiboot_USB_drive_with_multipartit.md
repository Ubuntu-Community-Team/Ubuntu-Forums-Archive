---
title: "How to create multiboot USB drive with multipartition manually ?"
date: 2014-12-25
forum: General Help
---

### Post by mr-roozbeh on 2014-12-25
Hi 
I try to create a USB drive with multipartition that can boot several iso images and show them in grub boot menu to choose from it .
there are several programs for create a multiboot USB like 'multibootusb' but these programs put all iso images in one partition and use live iso images not to install distros to USB .
with gparted create 4 patitions in my flash drive . For parted magic live iso , clonezilla iso , install tails distro and boot , yes boot part is in separate partition .
now I want to boot from USB and when grub menu's load show me a list of installed distro ( tails ) and added live iso images ( parted magic ... ) that I put them in the partitions .

Is any solution to do that ?

thanks

---

### Post by yancek on 2014-12-25
Not all distributions can be booted from an iso directly by Grub2.  Ubuntu and most of its derivatives can as can Parted Magic.  I don't know about Clonezilla or Tails.  You could extract them and copy them to a partition and boot that way.  You would need to install Grub2 to the master boot record pointing to the boot partition.  I don't use separate boot partitions so can't help with that part.  The entry below worked for me with this older version of Parted Magic which you would need to modify to suit your version.  The entry below shows Parted Magic on the first partition so you would need to also change that.  The grub.cfg file would simply need to point to the specific partition.  The second entry below boots and extracted version of clonezilla.

> menuentry "Parted Magic"{
loopback loop (hd0,1)/pmagic_2012_05_30.iso
linux (loop)/pmagic/bzImage
initrd (loop)/pmagic/initrd.img
}

menuentry "Clonezilla" {
set root=(hd0,1)
linux /live-hd/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" ip=frommedia nosplash live-media-path=/live-hd bootfrom=/dev/sdb1 toram=filesystem.squashfs
initrd /live-hd/initrd.img
}

---

### Post by oldfred on 2014-12-25
I am not quite sure why you want separate partitions.
If booting the ISO it is easier if they all are in one partition. Or do you want full installs in each separate partition to boot from one common grub?

Is system UEFI or BIOS?

This is all on one partition.
 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by mr-roozbeh on 2014-12-26
yancek and oldfred thank you .
I decide to do this because most programs like 'multibootusb' make a multiboot usb tipycally with one partition and with live iso images but anyone can't add live iso from other partitions to boot menu and
also they can't add installed disros like xubuntu or puppy to boot menu . yes making one partition with only live iso images is common and easy . 
In this [link]("http://www.linuxuser.co.uk/tutorials/dual-boot-usb-drive-tutorial") show how to create dual boot USB drive with installed distro (Ubuntu , Fedora) . Now I want to add the path of other live iso in other partition
to this grub menu . I don't sure that it's possible .
However I go to read your links and hope to do this .

---

### Post by C.S.Cameron on 2014-12-26
Starting with a MultiBootUSB install, I would think that if you put your iso's on separate partitions and edited their paths in grub.cfg it might work.
I have not tried this, but I have added persistence partitions, (casper-rw and home.rw), and that worked.
Using separate partitions might  be a way to get persistence for more than one OS at a time on a multiboot disk.

---

### Post by oldfred on 2014-12-26
I just install grub to flash drive and add my own entries. If directly booting flash drive BIOS reports boot drive as drive 0 so grub will always see it as hd0.
I have years ago added Puppy and then installed and added Puppy boot to grub on hard drive.
For those without examples somewhere on Internet, may not be bootable. ISO does have to be configured for loopmount. But some of those can have kernel extracted and boot kernel & then use its own kernel to boot. I have not done that.

If you use one of the scripts that uses grub2, then you should be able to manually add your own entry to grub.cfg to boot an ISO. One of the issues with any ISO is all the parameters. I often have had to open ISO and look at its syslinux boot parameters and copy those into my grub.cfg.

Each of these commands are ones I used to install grub to flash drive. The I manually created grub.cfg and copied ISO to flash drive in /iso folder. I have not been consistent so sometimes used /ISO, /iso, /boot/ISO etc. So then when I copy my boot stanza from one flash drive to another it does not work and I have to edit grub. Best to be consistent in mount location.

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

---

### Post by yancek on 2014-12-26
> can't add live iso from other partitions to boot menu and also they can't add installed disros like xubuntu or puppy to boot menu 

You should be able to chainload to another partition and boot either an iso file (if it is bootable), an extracted iso or an installed system.  With Grub2 installed on the second partition of a drive I can chainload to the first partition and boot all the systems on that partition.  The entry below is what I use to chainload to the Grub menu on the first partition so if you have Puppy or Xubuntu on another partition, that should work.

> menuentry 'Boot Partition One' {
    insmod part_msdos
    set root='(hd0,msdos1)'
    chainloader +1
}

---

### Post by yancek on 2014-12-27
If you are going to have an actual install of Xubuntu, I would suggest using its Grub bootloader to boot the various iso files on another partition.  I tested this booting from Grub2 on Ubuntu 14.04 which is on sdb8 and booting the iso of Zorin which was on sda5 so not only on a different partition but a different hard drive.  It booted but because I have an Nvidia driver, I needed the nomodeset option which you may not need.  If you're still trying this, you might try modifying the menuentry below to suit your particular partition and iso.

> menuentry "Boot Zorin from sdb8" {
        loopback loop (hd0,5)/zorin-os-9-core-32.iso
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/zorin-os-9-core-32.iso nomodeset quiet splash --
    initrd (loop)/casper/initrd.lz
}

---

### Post by oldfred on 2014-12-27
One of the issues of booting grub on one drive which is always hd0, is then what is the other drive(s). Mine even change depending on whether flash drive is plugged in or not. I often had to experiment or manually edit the grub (hdX,1) entry with several Xs to find correct one.

---

### Post by yancek on 2014-12-27
> One of the issues of booting grub on one drive which is always hd0, is  then what is the other drive(s). Mine even change depending on whether  flash drive is plugged in or not. I often had to experiment or manually  edit the grub (hdX,1) entry with several Xs to find correct one. 		

I've had similar experiences. Changing ports for an external confuses things.  I also had the experience of installing a version of Mint on an external drive which showed the external as sda and the internal as sdb even though both were attached during the install.  

I was experimenting with this yesterday with a flash drive and tried entries similar to the one I posted on Zorin above and all failed with unknown filesystem error, you need to load the kernel first.  Both partitions were FAT32.  I tried booting several different extracted Linux versions on partition one from Grub2 on partition two and got the same error.  Interestingly, to me at least, booting extracted versions of Linux on partition two with Grub Legacy on partition one booted just fine.

I think the OP would be better off doing an actual install of Xubuntu as he mentioned and then should be able to boot from other partitions.  Still there is the fact that many Linux distributions cannot be booted directly as an iso file.  I don't think I've come across one yet that can't be booted after being extracted and copied to a partition.

---

### Post by yancek on 2014-12-29
I think there was a problem with the previous flash drive as I tried another flash drive and was able to boot a Mint iso from the first partition and Precise Puppy from the second partition with the entries below.  Puppy was extracted (loop mounted) then copied to the partition.

> menuentry "Linux Mint 17" {
    loopback loop (hd0,1)/linuxmint-17-mate-32bit-v2.iso
    linux (loop)/casper/vmlinuz  boot=casper iso-scan/filename=/linuxmint-17-mate-32bit-v2.iso quiet splash --
    initrd (loop)/casper/initrd.lz
}
menuentry "Precise Puppy" {
    set root='(hd0,2)'
    linux /precise/vmlinuz pmedia=cd
    initrd /precise/initrd.gz
}

---

