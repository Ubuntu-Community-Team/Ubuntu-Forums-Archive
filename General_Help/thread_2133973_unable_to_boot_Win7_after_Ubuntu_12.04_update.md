---
title: "unable to boot Win7 after Ubuntu 12.04 update"
date: 2013-04-09
forum: General Help
---

### Post by crazy4cats on 2013-04-09
I've been searching for a while for a solution and couldn't find one through that I feel is specific to what is going on. (Probably through a lack of understanding.)

I have a HP envy 4-1043CL laptop with a 500GB HDD + 32GB SSD. It came with windows 7 and I have duel booted it with Ubuntu 12.04 LTS 64bit. The whole system was working wonderfully and I was able to access Win7 and Ubuntu, then after the recent updates for Ubuntu the windows 7 partitions have stopped appearing on the grub boot load screen. I have looked around and ran the boot-repair tool.
here is the output of the file
[URL="http://paste.ubuntu.com/5693498/"]
http://paste.ubuntu.com/5693498/[/URL]

ive also run sudo update-grub
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
done
```

I'm unsure what I need to do next.

---

### Post by oldfred on 2013-04-09
It looks like you have a standard BIOS based install, but HP has its repair files as efi or you have to use UEFI to make recovery or pairs from HP?

I do not see the issue either. Os-prober is not seeing sda2, which is your Windows install. But it should be creating a boot from sda1 which has boot files & boot flag. Boot-Repair often copies boot files from the Windows boot partition as a backup, but then grub finds both sda1 & sda2 as bootable.

Normally if there are file issues the BootInfo shows errors. But is the 32GB drive a Windows cache using Intel SRT? That uses RAID and can confuse grub and os-prober.

If you just add a boot stanza to 40_custom will it boot Windows?

       gksudo gedit /etc/grub.d/40_custom
sudo update-grub

Copy this into 40_custom:
```
 menuentry "Windows 7 (loader) (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 682E8B5A2E8B2064
chainloader +1
}

```

---

### Post by crazy4cats on 2013-04-09
oldfred thank you for your quick reply. Yes the 32GB SSD is a windows cache for using Intel SRT I had turned it off(I believe this got rid of the raid-0 because GParted could then see the drives) during the initial installation of Ubuntu. I had turned back on Intel SRT through Intel's rapid storage technology on my SSD after the installation of Ubuntu and everything  seemed to work properly. Perhaps having it on during the update was not  good. The code that you have provided worked to get my computer to boot  into Windows. If I were to turn off Intel RST and then run a tool such  as boot-repair would it successfully find all of the partitions for  grub?

---

### Post by oldfred on 2013-04-09
Possiblity. Part of the issue with RAID is that it writes meta-data onto the drive. Then  Linux thinks it is RAID. They were supposed to add RAID drivers to desktop installer, since they did away with the alternative installer. I think the install now works with RAID, but grub sees the meta-data. Grub installs into the RAID with RAID drivers not to a MBR, so then grub does not install or install correctly.

Most have had to remove meta-data, install grub, then restore Intel SRT which seems to work. But you may have issues any time there is a kernel or grub update.

       Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by crazy4cats on 2013-04-10
Thank you so much for your help oldfred and your fast responses. Everything is working very nicely.

---

