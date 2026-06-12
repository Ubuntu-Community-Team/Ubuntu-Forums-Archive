---
title: "Problems after boot repair"
date: 2019-02-18
forum: General Help
---

### Post by KieranFitzgerald on 2019-02-18
[COLOR=#000000]Ubuntu 14.04 LTS 64 bit.
After fixing a Ubuntu boot problem Windows no longer booted so I did a boot repair from a live USB. This has damaged the boot setup. The original boot menu had 4 or 5 entries. The "repaired" menu has 10 entries 3 for Windows the rest are Ubuntu. When I ran boot repair it turned off secure boot. Windows now boots but the UBUNTU boot options are "mixed up"

The main boot menu option UBUNTU boots a old install on the system while my usual UBUNTU boots from one of the other boot menu entries.

I have created a [/COLOR][COLOR=#000000]Bootinfo summary link below[/COLOR][COLOR=#000000]

[http://paste.ubuntu.com/p/NftSGzYzP9/](http://paste.ubuntu.com/p/NftSGzYzP9/)

How can I fix this please[/COLOR]

---

### Post by Dennis N on 2019-02-18
You have a file 25_custom added to **/etc/grub.d** by boot repair that causes the extra entries. See lines 1193-1214 in posted output. You can disable them by:
```
sudo chmod -x /etc/grub.d/25_custom
```
then 
```
sudo update-grub 
```
to rebuild the grub menu without the 4 extra entries.
Reboot to see updated grub menu.

---

### Post by oldfred on 2019-02-18
Which install is your old install?
You have installs in sda2 and sdc2 and UEFI boot entry for grub.cfg shows it uses UUID of sdc2.

```
       sda1/EFI/ubuntu/grub.cfg:
search.fs_uuid 05a0455f-1fc7-49f7-8455-966b756a9665 root hd2,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg 
    
```

from:
       sudo blkid -c /dev/null -o list 
or

lsblk -f
```
 /dev/sda2        1f623461-b232-492a-ba68-2ecf5eb095cf   ext4  
/dev/sdc2        05a0455f-1fc7-49f7-8455-966b756a9665   ext4 


```

You can either edit /boot/efi/EFI/ubuntu/grub.cfg or reinstall grub when booted into the install you want to have system default to. You also can use Boot-Repair's advanced options to choose an install rather than the default which uses whatever it finds.

---

### Post by KieranFitzgerald on 2019-02-19
The old install is sdc2.
I have booted into sda2 and rerun the boot repair, it still sets scd2 as the first boot item! 
Under advanced options - GRUB location - OS to boot by default the entry is
sda2 (The OS now in use ...........)

 The boot menu looks as before.  I have to select sda2 manually from the menu.
Here is the boot-info

[http://paste.ubuntu.com/p/TWbck9YvtY/](http://paste.ubuntu.com/p/TWbck9YvtY/)

Can I disable the older install in some way to prevent boot repair from detecting it?

I haven't tried Dennis N's suggestion yet.

---

### Post by oldfred on 2019-02-19
You can just edit your grub.cfg in your ESP.
It typically is mounted with not permissions in fstab, but Boot-Repair also changes that.

Change UUID of sdc2 to UUID of sda2
sudoedit /boot/efi/EFI/ubuntu/grub.cfg

I think you have to run the full reinstall of grub in advanced options to get it to change the grub.cfg in the ESP.

I have multiple test installs and newest install always overwrites my main working install, so I edit it.

```
#search.fs_uuid d1b31b73-4357-434c-8024-179f03ab41b6 root hd1,gpt8 
search.fs_uuid 8c92557f-cc60-438b-b1ea-ffea0adf0a1a  root hd0,gpt7
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


```

---

### Post by KieranFitzgerald on 2019-02-20
All working after applying oldfred and Dennis N's suggestions.
Thanks very much

---

