---
title: "Bootable Linux Backup"
date: 2013-10-31
forum: General Help
---

### Post by kevinannies5 on 2013-10-31
Hello all,

I'm new to this Forum. 

I am trying to create a bootable backup partition of my 13.10 install but i'm having issues. Here is my scenario.

Partition table

```
    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
                            Primary   Free Space                           1.05*
    sda1        Boot        Primary   ext4                            149999.01*
                            Pri/Log   Free Space                           0.85*
    sda5        NC          Logical   swap                              8106.55*
    sda6        NC          Logical   ext4                            142000.26*
    sda7        Boot        Logical   ext4                             50001.48*
```

sda1 is my /
sda5 is my swap
sda6 is my /home
sda7 is my intended backup /

I booted my system from a live USB and copied the entire contents of sda1 to sda7 as below:

```
sudo mkdir /mnt/UBUNTU
sudo mkdir /mnt/BACKUP_UBUNTU
sudo mount /dev/sda1 /mnt/UBUNTU
sudo mount /dev/sda7 /mnt/BACKUP_UBUNTU
sudo cp -frv /mnt/UBUNTU/* /mnt/BACKUP_UBUNTU
```

Next I changed the Grub config a little by adding a # as follows
```
/etc/default/grub
#GRUB_HIDDEN_TIMEOUT=0
```

I identified my disk UUID's
```
/dev/sda1: UUID="496730c6-2942-4546-bc5d-65c1e17b7c70" TYPE="ext4" 
/dev/sda5: UUID="44503fd8-e2c2-492d-a7d2-d5f4f7e04d11" TYPE="swap" 
/dev/sda6: UUID="fe7af56f-11bb-453b-bd6b-2dd8cb72d551" TYPE="ext4" 
/dev/sda7: UUID="d411f4cf-82e8-43e3-863a-805ddaae563d" TYPE="ext4" 
```

I then edited the file /etc/grub.d/40_custom and added a menu entry (copying something similar from the /boot/grub.cfg file and changing the parameters slightly.
```

  #!/bin/sh
       exec tail -n +3 $0
       # This file provides an easy way to add custom menu entries.  Simply type the
       # menu entries you want to add after this comment.  Be careful not to change
       # the 'exec tail' line above.
       menuentry 'UBUNTU 13.10 - BACKUP' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-d411f4cf-82e8-43e3-863a-805ddaae563d' {
       recordfail
       load_video
       gfxmode $linux_gfx_mode
       insmod gzio
       insmod part_msdos
       insmod ext2
      set root='hd0,msdos7'
       if [ x$feature_platform_search_hint = xy ]; then
         search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  d411f4cf-82e8-43e3-863a-805ddaae563d
       else
         search --no-floppy --fs-uuid --set=root d411f4cf-82e8-43e3-863a-805ddaae563d
       fi
        linux /boot/vmlinuz-3.8.0-32-generic root=d411f4cf-82e8-43e3-863a-805ddaae563d ro
           initrd /boot/initrd.img-3.8.0-32-generic
       }
```

I then update grub doing the following:


```

grub-mkconfig
sudo update-grub

```
Finally I edit the /etc/fstab file on sda7 to look like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=d411f4cf-82e8-43e3-863a-805ddaae563d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=fe7af56f-11bb-453b-bd6b-2dd8cb72d551 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=44503fd8-e2c2-492d-a7d2-d5f4f7e04d11 none            swap    sw              0       0

```

At this point I don't think i've missed anything so I attempt to boot the system up and get this message:
```
Begin: Running /scripts/init-premount ...done
Begin: Mounting root file system ... /init: line 250 arithmetic syntax error
Kernal panic - not syncing: attempted to kill init! exitcode=0x00
```

Now i'm really stumped. Anyone able to give me a hint as to where to look?

Note: Using the Advanced options for Grub give me an alternative option to boot into sda7 as running grub update dymamically detects the kernal and partition on sda7 but when selecting it, It just boots me into sda1, so this looks wrong to me.

---

### Post by carlwsnyder on 2013-10-31
I think you are attempting something not supported by Ubuntu.  I don't think the method you used to create your backup is supported for a single disk system.  First, only one bootable partition is supported per drive, period.  If you have multiple drives with bootable partitions, you are supposed to select the disk drive you wish to use by BIOS/UEFI, and this would allow you to clone your /dev/sda1 setup, but to another drive.  After all, if you can't boot from your normal install on a single drive system, you would not be able to boot from your backup, either!  How would you get to GRUB?

If you want to create a duplicate of your install on a single drive system and select it from GRUB, simply do a second installation, use **dpkg -l** (that is a lower case L) to get a list of your installed packages and copy your /home folder/partition.

Better yet would be a second drive, whether USB or internal, large enough for your installation.

---

### Post by kevinannies5 on 2013-10-31
Hiya, 
Good spot. i removed the boot flag from sda7 on my partition  table(though this didin't fix it). You're right, only the first sector of a disk is bootable (MBR).  Grub is installed into the MBR. However I am simply piggy backing grub  and modifying it to boot me into sda7. I just want an instantly bootable backup system I can use to test new updates/drivers etc. I got past my original problem  and simplified the bloated grub.cfg entry to something like this:

```
menuentry 'UBUNTU 13.10 - BACKUP' {
        insmod gzio
        insmod ext2
       set root='hd0,7'
        linux /boot/vmlinuz-3.8.0-32-generic root=/dev/sda7 ro
        initrd /boot/initrd.img-3.8.0-32-generic
}
```

I removed the UUID's and reffered to it directly as sda7. I also removed the msdos bit (Ubuntu uses it by default for some reason).
Simplicity is the way forward :-)

I now get past the kernal panic and my root filesystem mounts along with my swap partition and the rc scripts kick in. 

I now have the familiar issue of the boot process hanging at "Stopping System V runlevel compatibility".

---

### Post by oldfred on 2013-10-31
It looks like you have changed most of the entries. It usually is grub & fstab that need the new UUIDs. But grub also remembers where to reinstall on major updates and you may get issues if the install in sda7 installs its grub into the MBR.

I think if you uncheck everything then it will not reinstall.
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

You can simply grub entry even more. If install in sda7 updates kernel you have to change version to match.

      
 I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

If installing the same version, you may be ok sharing /home, but if any differences you may end up changing your main install as all your user settings are in /home. I have many installs, but keep /home inside my / (root) but then have all the data folders in a data partition. Sometimes I may copy some settings from one install to anther but usually just experiment with different settings so I do not want any of the old settings anyway.

---

### Post by warp99 on 2013-10-31
I believe that you need to chroot into sda7 and update-initramfs before you can boot to that partition. I forgot offhand how to do this, but there are plenty of guides in the wild.

---

### Post by kevinannies5 on 2013-11-01
Hi, Thanks for the responses. I have taken them onboard. When I get further or potentially resolve I will post my solution. May take a week or 2 though. Thanks. I didint' think about the initramfs but will investigate

---

