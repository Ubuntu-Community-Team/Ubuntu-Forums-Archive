---
title: "Chroot How-to update for efi systems"
date: 2017-09-06
forum: General Help
---

### Post by vidtek on 2017-09-06
In 2014 I did a simple tutorial for repairing grub2 boot failures using a chroot environment.  here: [https://ubuntuforums.org/showthread.php?t=2289087]("https://ubuntuforums.org/showthread.php?t=2289087")

This is an update for more modern systems.   

*&#65279;#### Boot to your live dvd/cd ensure the same architecture 32/64 bit is important .....From live dvd change root password  (saves having to do sudo) *
```

mint@mint ~ $ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
mint@mint ~ $ su
Password: 
```

[I]#### Get the device names for your efi and linux partition This is my setup, yours will be different.
[/I]
```
mint mint # blkid
/dev/sda1: LABEL="SYSTEM" UUID="B60D-32FF" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="6d09393a-d11d-4a7e-9638-566b2b7ec749"       *#### EFI partition*
/dev/sda3: LABEL="w10" UUID="D006D1BA06D1A1B0" TYPE="ntfs" PARTUUID="fdd8d8c1-3781-49ca-bfad-683f48c97353"                                    *#### my windows 10 partition*  
/dev/sdb1: LABEL="data" UUID="F2E89BB2E89B7397" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1ce6123a-1742-4ca4-9b71-c495bca489af"  *#### my data partition*
/dev/sdc1: LABEL="tv" UUID="6E66CE4866CE112F" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="d9118715-a532-4b4f-8ba0-01fe09c65398"    #### my media partition
/dev/sdd1: LABEL="MULTISYSTEM" UUID="65F1-D88E" TYPE="vfat" PARTUUID="300fa8d0-01"                                                            #### this live pendrive partiton
/dev/loop0: UUID="2017-06-29-12-08-24-00" LABEL="Linux Mint 18.2 KDE 64-bit" TYPE="iso9660" PTUUID="68783b88" PTTYPE="dos"                    #### this live pendrive partiton                                                              
/dev/loop1: TYPE="squashfs"                                                              						      #### this live pendrive partiton	
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="43852976-bf57-4529-8270-e79250147ad3"					      #### windows system partition	
/dev/sda4: PARTUUID="5051ddbb-5210-4a06-8d8b-a118df3f07ca"                                                                                    *#### legacy bios unused partition*
/dev/sda5: UUID="1a3fdcc8-9e28-4095-8d7b-9e09fbc56ad2" TYPE="ext4" PARTUUID="4c431bce-ca10-4920-afec-726808f6864c"                            ***#### LINUX PARTITION***
/dev/sda6: UUID="fb717962-1a1e-4a3b-9c45-1b1181ada463" TYPE="swap" PARTUUID="7b044993-325f-4c6f-9026-b445d5a3799c"                            *#### swap partition*
/dev/sda7: LABEL="home" UUID="9afe46e7-60d5-44ae-b73b-adde2d7617fd" TYPE="ext4" PARTUUID="55f3f4ae-48a9-4156-841a-ad44405639eb"		      [I]#### Home partition                                                                                                        
[/I]
```
[I]#### Setup chroot environment
[/I]
```
mint mint # mount /dev/sda5 /mnt                                                                                   
mint mint # mount /dev/sda1 /mnt/boot/efi                                                                            
mint mint # mount --bind /dev /mnt/dev                                                                                 
mint mint # mount --bind /dev/pts /mnt/dev/pts                                                                          
mint mint # mount --bind /proc /mnt/proc
mint mint # mount --bind /sys /mnt/sys
```

[I]####  Chroot command, (note the /bin/bash environment variable is only sometimes required, it will occasionally fail without it)
[/I]
```
mint mint # chroot /mnt /bin/bash
```

[I]#### Now we are in a chroot environment, we issue the commands to repair grub2 
[/I]
```
mint / # grub-install /dev/sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
```
```

mint / # update-grub
Generating grub configuration file ...
using custom appearance settings
Found linux image: /boot/vmlinuz-4.10.0-30-generic
Found initrd image: /boot/initrd.img-4.10.0-30-generic
Found linux image: /boot/vmlinuz-4.8.0-53-generic
Found initrd image: /boot/initrd.img-4.8.0-53-generic
File descriptor 24 (/dev/rfkill) leaked on lvs invocation. Parent PID 4971: /bin/sh
  /run/lvm/lvmetad.socket: connect failed: No such file or directory
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.                 *#### I have no idea what this error means, it doesn't affect the repair.*
Adding boot menu entry for EFI firmware configuration
done
```

*#### Press ctrl+d to exit the chroot, or just type quit or exit.*
```

mint / # exit
```

[I]#### Cleanly unmount the chroot
[/I]
```
mint mint # umount /mnt/dev/pts
mint mint # umount /mnt/dev
mint mint # umount /mnt/proc
mint mint # umount /mnt/sys
mint mint # umount /mnt/boot/efi
mint mint # umount /mnt
mint mint # 
```

[I]####  Reboot and you are done.  You should now have your grub2 boot screen.  I always run update-grub after the linux system boots to add entries not added in chroot.

[/I]

---

### Post by deadflowr on 2017-09-06
There is zero reason to create or set a root password in a live session.
just run
```
 sudo -i
```
and you'll be able to run an interactive root session until you either quit the terminal or type exit to exit the root session.

---

### Post by vidtek on 2017-09-06
> **deadflowr said:**
> There is zero reason to create or set a root password in a live session.
just run
```
 sudo -i
```
and you'll be able to run an interactive root session until you either quit the terminal or type exit to exit the root session.

Deadflowr-

It is just the way I always have done it since the 1990s.  I suppose we all have our little ways which seem weird to others.  By the way, thanks for tidying my post, you make it look so much better!

Cheers, Tony.

---

