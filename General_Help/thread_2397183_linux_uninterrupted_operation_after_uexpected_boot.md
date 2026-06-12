---
title: "linux uninterrupted operation after uexpected booted external drive disconnection"
date: 2018-07-26
forum: General Help
---

### Post by joann-morris on 2018-07-26
My current portable setup consisted of an external hard drive used as a  bootable usb disk. I have multiple distros on it (ubuntu 17 and 18) and it works well  except when the hard drive is accidentally disconnected. Linux brings up  tty and outputs error messages. I am still to be able to re-mount  the hard drive (by plugging it in again) but tty logs the hard drive mounted as a different  device (/dev/sdY instead of /dev/sdX). **Is there a method to insure that linux continues to operate without reboot even after re-mounting root device?**

---

### Post by oldfred on 2018-07-26
Do not use device like /dev/sdc.
I used to use device, but am changing to using labels. Ubuntu by default uses UUID to avoid those type of issues.
       [https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config) 

If loopmounting ISO.
```

menuentry "Ubuntu 18.04.1 Bionic Daily amd64" {
    set isofile="/bionic-desktop-amd64.iso"
    insmod part_gpt
    search --label iso_ssd --no-floppy --hint hd0,gpt5
    loopback loop (${root})$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram
    initrd (loop)/casper/initrd.lz
}
```

My external SSD when plugged in changes my grub entry from hd1 to hd2. I was manually editing but kept forgetting if USB flash drive or SSD or both plugged in and then which number I have to use.

Normally if sdb, it should be hd1, but external SSD as sdc becomes hd0.
```
menuentry "Cosmic 18.10 on sdb12 test" {
    search --set=root --label cosmic_b --hint hd2,gpt12
    configfile /boot/grub/grub.cfg
}

```

Shows labels, each time I reinstall & reformat a partition I have to reset label. 
```

fred@bionic-z97:~$ lsblk -f
NAME    FSTYPE LABEL       UUID                                 MOUNTPOINT
sda                                                             
&#9500;&#9472;sda1  vfat   EFI         FD76-E33D                            /boot/efi
&#9500;&#9472;sda2                                                          
&#9500;&#9472;sda3  ext4   trusty      45de38c8-6748-4634-b207-628d9aa8b42b 
&#9500;&#9472;sda4  swap               3af6a910-59f8-4719-b58c-2e7484d435f0 
&#9500;&#9472;sda5  ext4   iso_ssd     695d18b5-16f8-4e9c-bf66-675a12da5a26 /media/fred/iso_
&#9500;&#9472;sda6  ext4   xenial      255a2800-b871-4fdf-a809-16987e64b8b3 
&#9492;&#9472;sda7  ext4   bionic      8c92557f-cc60-438b-b1ea-ffea0adf0a1a /
sdb                                                             
&#9500;&#9472;sdb1  vfat   ESP_B       68CD-3368                            /media/fred/ESP_
&#9500;&#9472;sdb2                                                          
&#9500;&#9472;sdb3  ext4               76dc1759-fff1-419e-85a8-978b35537b0b 
&#9500;&#9472;sdb4  ext4   data        a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data
&#9500;&#9472;sdb5  ext4   backup      084de40f-8ffd-4af1-97b1-8a60cdd9aab4 
&#9500;&#9472;sdb6  ext4   iso_hdd     7f360ddc-d9fb-4a40-b17a-f2d5af6b61ed 
&#9500;&#9472;sdb7  swap               a7750d57-5381-421b-82fa-b53194ab45c2 [SWAP]
&#9500;&#9472;sdb8  ext4   debian      cf713b4c-6d8d-4289-b152-fc54051213e8 
&#9500;&#9472;sdb9  ext4   artful      fabeeda1-ad36-4300-a7f8-73afba118f37 
&#9500;&#9472;sdb10 ext4   bionicb     819db222-6f4f-42d5-8b20-491bdc09693c 
&#9500;&#9472;sdb11 ntfs   test        02FA0DAC185DDA7E                     
&#9492;&#9472;sdb12 ext4   cosmic_b    6ee4e5b7-cd2f-43f7-bf48-508980d29277 
sdc                                                             
&#9500;&#9472;sdc1  vfat   EFI_SSD64   7B30-5ACA                            /media/fred/EFI_
&#9500;&#9472;sdc2                                                          
&#9500;&#9472;sdc3  ext4   bionicSSD64 2c25bc79-df54-400f-8df3-e6bc15ff7bc2 /media/fred/bion
&#9492;&#9472;sdc4  ext4   cosmicSSD   6606bab7-0ecb-47cb-9b05-7a010ebbc9bd /media/fred/cosm
```

---

### Post by joann-morris on 2018-08-01
Thanks for the response. I didn't clearly explain the issue I was having. I have fstab configured using uuid and I don't think manual grub entries can solve the problem since linux has already booted. I am able to boot and use ubuntu off of the external hard disk all fine. what is going on is that when the external hard disk is accidentally disconnected, linux brings up the console (that doesn't respond to keyboard/mouse input events) and prints error messages like this...
[ATTACH=CONFIG]280629[/ATTACH](initial messages when unplugged and probe messages)
[ATTACH=CONFIG]280633[/ATTACH](more messages...)

and when I re-plug the external hard drive, I see that the hard disk mounts on /dev/sdb (originally on /dev/sda). My hunch is that since the external hard disk was mounted on / and wasn't properly unmounted, linux still thinks the hard drive is there but can't be reached. I believe that if I can make the kernel somehow believe that the newly re-plugged hard drive is /dev/sda (or the original drive mounted on /), linux can resume operations. It seems that some part of the kernel has already been loaded on to ram because devices are still able to mount and linux still seems to be searching for the root device. also note the time stamps in seconds on the far left of the each log entry (10,000 seconds...); ya I believe if the computer still has power, the kernel on ram will continue to unrelentingly probe for the root device (some dedication huh).
[ATTACH=CONFIG]280628[/ATTACH](same as top but after re-plugging drive twice(notice messages on the bottom))
[ATTACH=CONFIG]280630[/ATTACH](back to probeing for root device)

I have noticed that even if I were to re-plug the external hard drive during a certain time during the boot process, linux boots properly.  I can do more experiments if needed  

[ATTACH=CONFIG]280634[/ATTACH](re-plugging during the logs before welcome to ubuntu 17.04 message doesn't hinder boot)
what I ultimately wish for is that on the unexpected event of disconnection of the external hard drive, I can re-plug the external hard drive and resume linux operation as if it wasn't disconnected.
what are my options? Is there a method to do this? do I need a custom kernel?

---

