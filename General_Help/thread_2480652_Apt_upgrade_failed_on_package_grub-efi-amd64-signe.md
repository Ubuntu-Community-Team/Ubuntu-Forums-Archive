---
title: "Apt upgrade failed on package grub-efi-amd64-signed on non UEFI system - ubuntu serve"
date: 2022-11-05
forum: General Help
---

### Post by cheezykins on 2022-11-05
I have a non UEFI system with 2 disks in raid 1 using MDADM


/dev/md0 is a mirror of /dev/sda1 and /dev/sdb1 and contains the swap partition
/dev/md1 is a mirror of /dev/sda2 and /dev/sdb2 and is mounted as /boot
/dev/md2 is a mirror of /dev/sda3 and /dev/sdb3 which consists of the rest of the disk space and is mounted as /
/dev/sda4 and /dev/sdb4 both contain a grub bios partition. (partition table entries are not in disk order as noted by fdisk, this is the first partition on the disks)


I have apt currently failing due to an error in grub-efi-adm64-signed:


```

Setting up grub-efi-amd64-signed (1.182~22.04.1+2.06-2ubuntu10) ...
mount: /var/lib/grub/esp: special device /dev/sda15 does not exist.
dpkg: error processing package grub-efi-amd64-signed (--configure):

```


which is stopping me from doing anything with apt. I can find no references to /dev/sda15 anywhere on any filesystem so I am at a loss as to where it is getting /dev/sda15 from, but as I'm also not using UEFI I am loathe to just mark a random other partition as somewhere to install the EFI stuff, and you can't point it at an MDADM disk anyway. You can't just remove the package as it is considered critical to ubuntu.

I can see nothing even vaguely related in dmesg, syslog or journalctl.

Any help resolving this would be appreciated.

Further information:

lsb_release:


```

Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
```


fdisk -l output: [https://pastebin.com/XhdfEXgw](https://pastebin.com/XhdfEXgw)
mdadm output: [https://pastebin.com/DXQeuQu4](https://pastebin.com/DXQeuQu4)
full apt run: [https://pastebin.com/AugtKL7r](https://pastebin.com/AugtKL7r)

---

### Post by cannfoddr on 2022-11-05
I am hitting a similar issue:

mount: /var/lib/grub/esp: special device /dev/disk/by-id/ata-QEMU_HARDDISK_QM00007-part1 does not exist.
dpkg: error processing package grub-efi-amd64-signed (--configure):

that device doesnt exist in the path and I cant figure out where the system is getting that name from?

---

### Post by oldfred on 2022-11-05
If you are BIOS booting, you should not be installing grub-efi-amd64-signed.
The BIOS version is grub-pc.

sudo apt install grub-pc grub-common

Do you have an ESP - efi system partition defined in fstab? on sda15?

cat /etc/fstab

Also UEFI will not have this entry in this file:
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc

---

### Post by cheezykins on 2022-11-05
It's not one installed by me, it comes pre-installed with ubuntu, that's why apt wont let me remove it.

fstab:

```

proc /proc proc defaults 0 0
# /dev/md/0
UUID=b7426809-8495-4471-ba3b-19881cd817bf none swap sw 0 0
# /dev/md/1
UUID=db4d691c-9c51-4e4e-bd94-0698639cdc5a /boot ext3 defaults 0 0
# /dev/md/2
UUID=5fc9ad3f-6077-49e6-a650-f3e59b9fda0b / ext4 defaults 0 0

```

I'm definitely not running on UEFI

```

user@systemname ~ $ sudo efibootmgr
EFI variables are not supported on this system.
user@systemname ~ $ sudo ls /sys/firmware/efi
ls: cannot access '/sys/firmware/efi': No such file or directory

```



Interestingly your debconf-show command does show the erroneous drive

```

chris@systemname ~ $ sudo debconf-show grub-pc
* grub-pc/install_devices: /dev/disk/by-id/ata-ST4000NM0245-1Z2107_ZC19XRT4, /dev/disk/by-id/ata-ST4000NM0245-1Z2107_ZC19XRDY
* grub-pc/install_devices_empty: false
* grub-efi/install_devices: /dev/sda15

```

But I have no idea where it has got it from, this computer has never had a /dev/sda15.

Essentially it looks like I need to remove that final grub-efi/install_devices entry, but I'm not actually sure how to do that.

Searching says I should just be able to do a dpkg-reconfigure grub-pc but that tells me that it is not installed.

---

### Post by oldfred on 2022-11-05
[FONT=arial]I have not looked at my [/FONT][FONT=monospace][FONT=arial][COLOR=#000000]sudo debconf-show grub-pc for ages as it never used to show anything related to efi, just BIOS boot.
But I now see multiple efi entries and in mine most are empty or a few not correct as I do have UEFI install, but it does not show devices.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1891680](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1891680)
Says fixed in grub 2.02, but grub is now 2.06, so not sure if grub even using that file?

I thought now they installed both grub-pc & grub-efi-amd64, to make it easier to convert from BIOS to UEFI boot. 
[/COLOR][/FONT]
[/FONT]

---

### Post by cheezykins on 2022-11-05
I've removed the grub-efi config entries pointing to the erroneous drive from debconf and apt has now completed, the efi package warns about not being installed but grub pointing at i386-pc says it is installed fine. I'll wait until the system is quiet tonight for a reboot to see if it actually boots lol.

Thanks for your help oldfred, you've pointed me exactly where I needed to look. Hopefully I haven't bricked the server! :)

At least I have backups of the debconf if I need to boot into recovery media.

Edit: SUCCESS! It came back up without issue.

---

### Post by oldfred on 2022-11-05
Glad that worked & good to know that it did work.

---

### Post by cannfoddr on 2022-11-06
for me the key was the debconf cache - I went to the config cache end removed the entries for the non-existent drive and everything is now working

---

### Post by kabongo on 2022-11-12
> **cheezykins said:**
> 

Edit: SUCCESS! It came back up without issue.

Nice! I have the same, or a similar problem. Can you please describe how you edited/removed the debconf entries?

I tried:
[FONT=courier new]```
debconf-show grub-pc
debconf-get-selections | grep grub-pc
debconf-get-selections | grep grub-pc > debconf_grub-pc.txt   # backup of settings
echo PURGE | debconf-communicate grub-pc                      # remove all grup-pc settings
dpkg-reconfigure grub-pc                                      # accept defaults, device(s): select main device(s) e.g. /dev/sda  (without numbers)

debconf-show grub-pc                                          # efi entries like "sda15" still here :-(

```[/FONT]

Thanks a lot!

---

### Post by kabongo on 2022-11-12
Ok I figured it out.  [https://www.ullright.org/ullWiki/show/ubuntu-20-04-apt-error-mount-var-lib-grub-esp-special-device-dev-sda15-does-not-exist-dpkg-error-processing-package-grub-efi-amd64-signed-configure-installed-grub-efi-amd64-signed-package-post-installation-subprocess-returned-status-32](https://www.ullright.org/ullWiki/show/ubuntu-20-04-apt-error-mount-var-lib-grub-esp-special-device-dev-sda15-does-not-exist-dpkg-error-processing-package-grub-efi-amd64-signed-configure-installed-grub-efi-amd64-signed-package-post-installation-subprocess-returned-status-32)

```
[FONT=courier new]debconf-show grub-pc
debconf-get-selections | grep grub-pc
debconf-get-selections | grep grub-pc > debconf_grub-pc.txt   # backup of settings
cp debconf_grub-pc.txt debconf_grub-pc-modified.txt
vi debconf_grub-pc-modified.txt                               # Remove all "grub-efi" lines, save and exit
echo PURGE | debconf-communicate grub-pc                      # remove all grup-pc settings
debconf-set-selections debconf_grub-pc-modified.txt           # Restore only valid settings
debconf-show grub-pc


[/FONT][FONT=courier new]mv /var/cache/debconf /var/cache/debconf.bak                  # Remove debconf cache, it will be rebuilt automatically
dpkg --configure -a                                           # I think I was asked if we want to leave grub unconfigured -> "yes"
dpkg-reconfigure grub-pc                                      # Accept defaults, device(s): select main device(s) e.g. /dev/sda, /dev/sdb  (without numbers)
update-grub
apt purge grub-efi
apt update
apt dist-upgrade
reboot
    [/FONT]
```

---

