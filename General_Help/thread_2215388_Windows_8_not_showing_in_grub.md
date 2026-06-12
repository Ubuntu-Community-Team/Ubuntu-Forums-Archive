---
title: "Windows 8 not showing in grub"
date: 2014-04-06
forum: General Help
---

### Post by gyan2 on 2014-04-06
i have installed windows 8.1 on ubuntu after this i used boot-repair to fix the boot options.
But after rebooting windows is not showing in the grub list

boot-info url  --  [http://paste.ubuntu.com/7213080](http://paste.ubuntu.com/7213080)

---

### Post by lisati on 2014-04-06
*Thread moved to **General Help**.*

---

### Post by oldfred on 2014-04-06
Windows only boots from the one primary NTFS partition with the boot flag. Second or additional installs put all boot files & configuration into that partition. So your install in sda8 will not normally be bootable except thru sda2.

You also are showing many /grldr files which are from grub4dos which is usually installed by EasyBCD. All those files may be confusing things. They are in sda1, sda2 & sda8.

You also show menu.lst in the NTFS partitions sda1 & sda2. That is from grub legacy and should be removed.
And the rest of grub2 in /grub is also in sda1 which probably should be removed.

> Boot files:        /menu.lst /grub/grub.cfg /grldr /grub.exe /grldr 
                       /grub/core.img /KERNEL.SYS /COMMAND.COM

---

### Post by gyan2 on 2014-04-07
@oldfred should I delete all files in sda1 and boot from sda2 ?

---

### Post by NikTh on 2014-04-07
If you can boot into Ubuntu without problem, you can try to reconfigure grub like this
```
sudo dpkg-reconfigure grub-pc
``` 
and re-install os-prober 
```
sudo apt-get install --reinstall os-prober
```

I didn't see any EFI or GPT on your system, but I saw some weired report about menu.lst which leads to grub-legacy. (?) 

After reconfigure grub-pc, try to update grub 
```
sudo update-grub
``` 
and see if Windows detected properly this time. If not, you can try to mount the Windows partition manually and run `sudo update-grub` again. An example of manual mounting 
```
sudo mount /dev/sda2 /mnt
sudo update-grub
```
**but first**, follow @oldfred advice.

---

### Post by oldfred on 2014-04-07
I would only delete /grldr files & folders. Your sda1 may be a Windows recover or a vendor recovery and any boot files in it may be needed.
And delete grub legacy menu.lst in sda2 and the grub2 files & folders. They should not normally be in a Windows partition. 

The install of grub to the NTFS partition should not have created any issues as long as you do not have duplicate /boot/grub and /Boot/BCD folders. In Windows which is not case sensitive that is one /Boot folder which cannot be duplicated and creates errors. In Linux it is case sensitive so seen as two different folders.

Although I was able to install grub to a Windows NTFS partiton and boot Windows that was in that partition, but that was not a normal install, but a flash drive with both Windows & live ISO as a master repair flash drive. But you have to be extremely careful not to overwrite a PBR or /boot as those are critical for Windows to work.

---

