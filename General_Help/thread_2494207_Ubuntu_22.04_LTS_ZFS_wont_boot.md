---
title: "Ubuntu 22.04 LTS ZFS wont boot"
date: 2024-01-08
forum: General Help
---

### Post by ca-scribner on 2024-01-08
Hi everyone,

Came to by running computer today and the lock screen was frozen.  When I restarted, the computer said I had no bootable device installed.  I can see the boot drive in BIOS, but it doesn't show as a boot option.  I've since booted on a live usb and started poking around, but I'd appreciate a nudge in the right direction.The machine was running ubuntu 22.04.  On install (I think originally as a 20.04 install), I chose full disk encryption.  

 I ran boot-repair and got [the following]("https://paste.ubuntu.com/p/RtPr5Nh73C/"):
```

boot-repair-4ppa2075                                              [20240108_1425]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk part_msdos fshelp fat ntfs exfat
    ---------------------------------------------------------------------------

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub/grub.cfg /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       zfs_member
    Boot sector type:  -
    Boot sector info: 

nvme0n1p4: _____________________________________________________________________

    File system:       zfs_member
    Boot sector type:  -
    Boot sector info: 

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: TigerLake-LP GT2 [Iris Xe Graphics] from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 23.10, mantic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 03.10(3.16) from INSYDE Corp.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,2001,2002,2003
Boot0000* Linpus lite    HD(1,MBR,0xc86b9,0x800,0x728f800)/File(\EFI\Boot\grubx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

a9c517741ac31962d7feb152948ad1ee   nvme0n1p1/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/BOOT/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   nvme0n1p1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    grubenv-ok,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: B6CD0765-01BB-4AEE-B81D-09E4E811A06A
           Start        End    Sectors  Size Type
nvme0n1p1    2048    1050623    1048576  512M EFI System
nvme0n1p2 1050624    5244927    4194304    2G Linux swap
nvme0n1p3 5244928    9439231    4194304    2G Solaris boot
nvme0n1p4 9439232 1953525134 1944085903  927G Solaris root
Disk sda: 57.28 GiB, 61505273856 bytes, 120127488 sectors
Disk identifier: 0x000c86b9
     Boot Start       End   Sectors  Size Id Type
sda1  *     2048 120127487 120125440 57.3G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:61.5GB:scsi:512:512:msdos: USB  SanDisk 3.2Gen1:;
1:1049kB:61.5GB:61.5GB:fat32::boot, lba;
nvme0n1:1000GB:nvme:512:512:gpt:Samsung SSD 970 EVO Plus 1TB:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:2685MB:2147MB:::swap;
3:2685MB:4833MB:2147MB:zfs::;
4:4833MB:1000GB:995GB:zfs::;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE      UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                           
&#9492;&#9472;sda1      vfat        10E8-1969                            000c86b9-01                          UBUNTU 23_1 
nvme0n1                                                                                                       
&#9500;&#9472;nvme0n1p1 vfat        680C-6402                            57e4d738-860c-4c28-acd1-fda575f846ed             EFI System Partition
&#9500;&#9472;nvme0n1p2 crypto_LUKS 54b9a209-72c0-4ded-9ded-b10f9564d087 5666973e-7f8b-1841-a6de-d2112bd2cf3e             
&#9500;&#9472;nvme0n1p3 zfs_member  493191063445844317                   5b071324-e0aa-1847-a7a4-327192b4f1f9 bpool       
&#9492;&#9472;nvme0n1p4 zfs_member  6153821987050407745                  9ce2f3c6-a683-9941-9ae0-a469a45ea6d4 rpool       

Mount points (filtered): _______________________________________________________

                           Avail Use% Mounted on
/dev/nvme0n1p1            496.7M   3% /mnt/boot-sav/nvme0n1p1
/dev/sda1                  52.4G   8% /cdrom
efivarfs                     51K  70% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p1            vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda1                 vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

====================== nvme0n1p1/grub/grub.cfg (filtered) ======================

Revert system only   gnulinux-${root_dataset}-${kversion}
Ubuntu 22.04.2 LTS   gnulinux-rpool/ROOT/ubuntu_6oi4rd-5.19.0-50-generic
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 680C-6402 root 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

================= nvme0n1p1: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             grub/grub.cfg                                  1

====================== sda1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on nvme0n1p2




================================ ZFS activation ================================

dpkg-query -W -f=${Version} zfsutils-linux : 2.2.0~rc3-0ubuntu4
zpool export -f -a 

zpool import -N -R /mnt rpool 
zpool import -N -R /mnt bpool 
zpool import -N -f -R /mnt/boot-sav/zfs bpool 
zpool import -N -f -R /mnt/boot-sav/zfs rpool 
cryptsetup -v open /dev/zvol/rpool/keystore zfskey Command failed with code -4 (wrong device or file specified).
zfs load-key -a 
zfs mount  
zfs mount -a 
Error: could not activate ZFS. Please report this message to boot.repair@gmail.com
zpool list after activation
no pools available

zfs list


=================== findmnt (filtered) after ZFS activation ====================

SOURCE           FSTYPE        SIZE   USED AVAIL USE% TARGET
/dev/sda1        vfat         57.3G   4.8G 52.4G   8% /cdrom




Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

Confirmation request before suggested repair: __________________________________

Warning: ZFS not activated correctly. Repair will fail unless you mount the pools on /mnt/boot-sav/zfs before continuing. Please report this message to boot.repair@gmail.com
You may want to retry after mounting your encrypted partitions so that the tool can verify their contents. (cryptsetup open)
Are you sure you want to continue anyway?

```

Which I think is saying that it can't tell me much without decrypting the data?  Or is there something else about the boot mount that is bad before this?  I've tried doing `cryptsetup luksopen /dev/nvme0n1p2 crypted_nvme` but when I put in the password I'd usually use at boot it says "No key available with this passphrase".  

Any tips appreciated

---

### Post by MAFoElffen on 2024-01-08
If this was installed as Encrytped ZFS from the Ubunut Installer, please follow these instructions. Those are my notes. If you have any questions, just ask.

---

### Post by ca-scribner on 2024-01-09
Thanks [COLOR=#000000]MAFoElffen for the quick reply.  Is there a link missing from your message?  Maybe I'm missing something.

Thanks![/COLOR]

---

### Post by #&amp;thj^% on 2024-01-09
While you wait for MAFoElffen this link may help you: [https://ubuntuforums.org/showthread.php?t=2491426](https://ubuntuforums.org/showthread.php?t=2491426)
If your unsure on anything please wait for help.

---

### Post by ca-scribner on 2024-01-09
ty 1fallen!

I've gone through that thread and I think done everything.  It actually made me wonder if my bpool might have filled up as you noted there (mine has threatened to fill up in the past), but my boot-repair info did not include the same disk usage and I wasn't sure how else to get the info.

I started down this route
```

zpool export -a
zpool import -N -R /mnt rpool
zpool import -N -R /mnt bpool

```

but both rpool and bpool say "cannot import X: one or more devices is currently unavailable"

I've tried `cryptsetup luksopen /dev/nvme0n1p2 crypted_nvme` but it fails with "No key available with this passphrase".  I think the other commands MAFoElffen suggests require the cryptsetup to have succeeded, although I might be wrong.

I'm poking around wondering if the header or keystore for the drive has been corrupted?  I'm confused why the passcode would be rejected during `cryptsetup luksopen`.  Just to check my method, I've tried doing the same thing on another system and it seemed to work fine (it would accept my passcode and say `Cannot use device /dev/zd0 which is in use (already mapped or mounted).` which I think made sense since the device was already mounted)

---

### Post by ca-scribner on 2024-01-09
I'm also not sure how all this connects with the computer not seeing the drive as a boot drive at all, but I dont have a lot of experience in this area so maybe this is normal

---

### Post by #&amp;thj^% on 2024-01-09
Boot Repair has issues with encrypted ZFS the maintainer is working on it, but has not mentioned anything else.
This part "not seeing the drive as a boot drive at all" is a new problem mostly seen on 23.10 Mantic, and according to MAFoElffen just showed up in jammy as well 22.04.
I'm currently running Noble 24.04 on ZFS Root with no issues[COLOR="#FF0000"], *NOTE*[/COLOR] Noble is in a Development state currently not recommended for production/Stable.
The Boot issue is something I just reinstall to fix.I do have back-ups so NO data is lost. But wait for MAFoElffen he has good results with mucking about with Boot issues

BTW I do monitor bpool alot:
```
zfs list | grep -e "bpool" -e "Avail"
bpool                                              339M  1.42G    96K  /boot
bpool/BOOT                                         338M  1.42G    96K  none
bpool/BOOT/ubuntu_yr0agi                           338M  1.42G   338M  /boot

```

---

### Post by MAFoElffen on 2024-01-09
I'm one of the contributors to boot-repair and boot-info... especially for LUKS, other encryption matters, and all matters on ZFS That GitHub is my latest notes for ZFS.

Lets back up, and I'll explain this a little differently... Boot from an Ubuntu 22.04.3 LTS Installer Live USB... Open FireFox and get back to the this thread. Open a Terminal Session.
```

sudo su -
zpool export -a
zpool import -f -N -R /mnt rpool
zpool import -f -N -R /mnt bpool

```
Editted order. /dev/zd0 doesn't appear until after rpool is imported...
```

cryptsetup open -v /dev/zvol/rpool/keystore keystore-rpool
mount /dev/mapper/keystore-rpool /media
ls /media/system.key
cat /media/system.key | zfs load-key -L prompt rpool

```
We used that keyfile to unlock rpool
```

zfs mount $(zfs list | grep -m1 -e '^rpool\/ROOT\/ubuntu_' | awk '{print $1}' )
zfs mount $(zfs list | grep -m1 -e '^bpool\/BOOT\/ubuntu_' | awk '{print $1}' )
zfs mount -a
ount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
cd /mnt
chroot /mnt /bin/bash --login
mount -a

```
Tell me how that goes...

---

### Post by ca-scribner on 2024-01-10
So far, I'm breaking at the start

```

cryptsetup open -v /dev/zvol/rpool/keystore zfskey
Device /dev/zvol/rpool/keystore does not exist or access denied.
Command failed with code -4 (wrong device or file specified).

```

Posting this right away in case there was a typo maybe, but I'll poke around and see if maybe things were named differently on my end

---

### Post by #&amp;thj^% on 2024-01-10
Just to be sure, did you lead with "sudo su -"  before the cryptsetup open -v  ?
```
 #whoami
root

```

---

### Post by ca-scribner on 2024-01-10
Good question, but yes:

```

whoami
root

```

Actually I think boot-repair tried to run the same thing and hit the same issue:

```

================================ ZFS activation ================================

dpkg-query -W -f=${Version} zfsutils-linux : 2.2.0~rc3-0ubuntu4
zpool export -f -a 

zpool import -N -R /mnt rpool 
zpool import -N -R /mnt bpool 
zpool import -N -f -R /mnt/boot-sav/zfs bpool 
zpool import -N -f -R /mnt/boot-sav/zfs rpool 
cryptsetup -v open /dev/zvol/rpool/keystore zfskey Command failed with code -4 (wrong device or file specified).
zfs load-key -a 
zfs mount  
zfs mount -a 
Error: could not activate ZFS. Please report this message to boot.repair@gmail.com
zpool list after activation
no pools available

```

---

### Post by #&amp;thj^% on 2024-01-10
Dang this is not looking good then. :(

Still wait for MAFoElffen though I want him to see this.
You may still be salvageable, when this happened to me due to a bad update (Development only) Nothing could find or see a "bpool" but your dose. I ?think? that's the good news.
I'm booted and unlocked but:
```
sudo cryptsetup -v open /dev/zvol/rpool/keystore zfskey
No usable token is available.
Enter passphrase for /dev/zvol/rpool/keystore: 
Cannot use device /dev/zvol/rpool/keystore which is in use (already mapped or mounted).
Command failed with code -5 (device already exists or device is busy).

```

```
 sudo zfs get keystatus rpool 
[sudo] password for me: 
NAME   PROPERTY   VALUE        SOURCE
rpool  keystatus  available    -

```

```
 sudo zfs get keylocation rpool 
NAME   PROPERTY     VALUE                                  SOURCE
rpool  keylocation  file:///run/keystore/rpool/system.key  local

```

---

### Post by MAFoElffen on 2024-01-10
Please post the results of this within CODE Tags
```

sudo cryptsetup luksDump /dev/zvol/rpool/keystore

```
That should have been the command if it was created with 22.04 and the LUKS Container is LUKS2... 

I'll just go on a bit further, for the just cases if I am working before you post back, so 1fdallen or you can decide, if that just says LUKS or LUKS1...

In that case do (as root)
```

cryptsetup -v luksOpen /dev/zvol/rpool/keystore zfskey
# OR
sudo cryptsetup -v open -t 1 /dev/zvol/rpool/keystore zfskey

```
For LUKS1 containers that was used if installed with 20.04 instead of 22.04...

---

### Post by ca-scribner on 2024-01-10
Thanks for the help, MAFoElffen.  Here are the results:

```

sudo cryptsetup luksDump /dev/zvol/rpool/keystore
Device /dev/zvol/rpool/keystore does not exist or access denied.

cryptsetup -v luksOpen /dev/zvol/rpool/keystore zfskey
Device /dev/zvol/rpool/keystore does not exist or access denied.
Command failed with code -4 (wrong device or file specified).

sudo cryptsetup -v open -t 1 /dev/zvol/rpool/keystore zfskey
Device /dev/zvol/rpool/keystore does not exist or access denied.
Command failed with code -4 (wrong device or file specified).

```

Now that you mention 20.04, I can't recall for sure but I think this machine started as something other than 22.04 and was later upgraded to 22.04.  It might have started as 21.04 or 21.10, and later upgraded through to 22.04

---

### Post by ca-scribner on 2024-01-10
/dev/zvol doesn't exist on the machine atm (while booting from a 22.04 live usb).  Could it be under another name or need something to make it available?

---

### Post by MAFoElffen on 2024-01-10
I'm spinning up an default installed 22.04.3 ZFS encrypted install right now...

I think I might have a type on that for the device name... BRB.

---

### Post by MAFoElffen on 2024-01-10
Ammended destrustions fro 22.04.3... In the comments (#) are just what should be the expected output)
```

sudo su -

zpool import -f -N -R /mnt rpool

cryptsetup open -v /dev/zvol/rpool/keystore keystore-rpool
#No usable token is available.
#Enter passphrase for /dev/zvol/rpool/keystore: 
#Key slot 0 unlocked.
#Command successful.

ls /dev/mapper
#control  keystore-rpool

ls /dev/zvol/rpool/keystore
#/dev/zvol/rpool/keystore

find / -name keystore 2>/dev/null
#/dev/rpool/keystore
#/dev/zvol/rpool/keystore

file /dev/rpool/keystore
#/dev/rpool/keystore: symbolic link to ../zd0

mount /dev/mapper/keystore-rpool  /media

ls /media
#lost+found  system.key

zpool import -f -N -R /mnt bpool

cat /media/system.key | zfs load-key -L prompt rpool

zfs mount $(zfs list | grep -m1 -e '^rpool\/ROOT\/ubuntu_' | awk '{print $1}' )

zfs mount $(zfs list | grep -m1 -e '^bpool\/BOOT\/ubuntu_' | awk '{print $1}' )

zfs mount -a

mount --make-private --rbind /dev  /mnt/dev

mount --make-private --rbind /proc /mnt/proc

mount --make-private --rbind /sys  /mnt/sys

mount --make-private --rbind /run  /mnt/run

cd /mnt

chroot /mnt /bin/bash --login

mount -a

```

---

### Post by MAFoElffen on 2024-01-11
Tell me how that goes for you... (Also updated post #8) That should get you into the chroot, where you can do what you need to do... Like Reinstall grub & update the intramfs images.

Alibi - Since you installed from 20.04... You still may have to use "cryptsetup luksOpen", intead of "cryptsetup open", but we'll see about that.

Then after you are through, after all, then to exit it safely, do
```

exit
mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
    xargs -i{} umount -lf {}
zpool export -a
reboot

```

---

### Post by ca-scribner on 2024-01-11
Did a restart just to make sure I hadn't done anything funny.  To confirm, I'm running a live usb of 22.04.3 lts.  Here is what I see when executing the first command:

```

sudo su -
root@ubuntu:~# zpool import -f -N -R /mnt rpool
cannot import 'rpool': one or more devices is currently unavailable

```

Any idea what I'm missing?  thanks!

---

### Post by #&amp;thj^% on 2024-01-11
ca-scribner have you tried yet to make a rEFInd USB drive and try to boot from that drive?
This Link will start the Download:
[https://sourceforge.net/projects/refind/files/0.12.0/refind-flashdrive-0.12.0.zip/download](https://sourceforge.net/projects/refind/files/0.12.0/refind-flashdrive-0.12.0.zip/download)

---

### Post by ca-scribner on 2024-01-11
No I have not, I've not used that tool before.  I just made one and will play around with it shortly.  Anything in particular I should look out for, or just see if I can get something going in general?  My experience with EFI, boot, etc, is minimal

---

### Post by #&amp;thj^% on 2024-01-11
Just boot to the USB drive, and from there it will show you possible boot options.

I'm very curious as to how Ubuntu lost it's way to see a boot-able system.

---

### Post by ca-scribner on 2024-01-11
when I'm in the rEFInd menu on boot and go to Manage EFI Boot Order, all it gives me are USB, CD, and Network.  No mention of my main drive.  

In the BIOS the computer does see the drive, and if booted on a live USB I do see some info about the drive as well.  But if I go to my Boot Manager I don't see the drive :/

---

### Post by #&amp;thj^% on 2024-01-11
That's what I thought, I see no way to get in your system now, but if you have good backups (and you should) a reinstall is the best course of action now. :(

I would of suggested importing your "rpool" from another installed system but the results would be the same as in all the above posts.

---

### Post by ca-scribner on 2024-01-11
Poking around a bit more in case it helps someone...

Disk is discoverable in fdisk
```

sudo fdisk -l

...
Disk /dev/nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 970 EVO Plus 1TB            
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B6CD0765-01BB-4AEE-B81D-09E4E811A06A

Device           Start        End    Sectors  Size Type
/dev/nvme0n1p1    2048    1050623    1048576  512M EFI System
/dev/nvme0n1p2 1050624    5244927    4194304    2G Linux swap
/dev/nvme0n1p3 5244928    9439231    4194304    2G Solaris boot
/dev/nvme0n1p4 9439232 1953525134 1944085903  927G Solaris root

...

```

blkid shows
```

sudo blkid
/dev/nvme0n1p1: UUID="680C-6402" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="57e4d738-860c-4c28-acd1-fda575f846ed"
/dev/nvme0n1p3: LABEL="bpool" UUID="493191063445844317" UUID_SUB="934484222053174471" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="5b071324-e0aa-1847-a7a4-327192b4f1f9"
/dev/nvme0n1p4: LABEL="rpool" UUID="6153821987050407745" UUID_SUB="14470870218067292293" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="9ce2f3c6-a683-9941-9ae0-a469a45ea6d4"
/dev/sda1: LABEL="UBUNTU 22_0" UUID="DC1E-7100" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="0f9daad5-01"
/dev/loop1: TYPE="squashfs"
/dev/nvme0n1p2: UUID="54b9a209-72c0-4ded-9ded-b10f9564d087" TYPE="crypto_LUKS" PARTUUID="5666973e-7f8b-1841-a6de-d2112bd2cf3e"
/dev/loop8: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"

```

If I try to mount the first partition, I do see some things...
```

sudo mkdir -p /mnt/nvme/p1
sudo mount /dev/nvme0n1p1 /mnt/nvme/p1
ll /mnt/nvme/p1
total 12
drwxr-xr-x 4 root root 4096 Jan  1  1970 ./
drwxr-xr-x 3 root root   60 Jan 11 18:39 ../
drwxr-xr-x 5 root root 4096 Mar 27  2023 EFI/
drwxr-xr-x 5 root root 4096 Jul 26 10:41 grub/



```

More details on what is in there (not sure if anything is missing?)
```

/mnt/nvme/p1/
/mnt/nvme/p1/grub
/mnt/nvme/p1/grub/gfxblacklist.txt
/mnt/nvme/p1/grub/unicode.pf2
/mnt/nvme/p1/grub/x86_64-efi
/mnt/nvme/p1/grub/x86_64-efi/load.cfg
/mnt/nvme/p1/grub/x86_64-efi/http.mod
/mnt/nvme/p1/grub/x86_64-efi/bfs.mod
/mnt/nvme/p1/grub/x86_64-efi/play.mod
/mnt/nvme/p1/grub/x86_64-efi/hdparm.mod
/mnt/nvme/p1/grub/x86_64-efi/diskfilter.mod
/mnt/nvme/p1/grub/x86_64-efi/memdisk.mod
/mnt/nvme/p1/grub/x86_64-efi/cpio_be.mod
/mnt/nvme/p1/grub/x86_64-efi/legacycfg.mod
/mnt/nvme/p1/grub/x86_64-efi/ntfscomp.mod
/mnt/nvme/p1/grub/x86_64-efi/tr.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_arcfour.mod
/mnt/nvme/p1/grub/x86_64-efi/usbtest.mod
/mnt/nvme/p1/grub/x86_64-efi/luks2.mod
/mnt/nvme/p1/grub/x86_64-efi/video_cirrus.mod
/mnt/nvme/p1/grub/x86_64-efi/bswap_test.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_serpent.mod
/mnt/nvme/p1/grub/x86_64-efi/nilfs2.mod
/mnt/nvme/p1/grub/x86_64-efi/relocator.mod
/mnt/nvme/p1/grub/x86_64-efi/lsefi.mod
/mnt/nvme/p1/grub/x86_64-efi/bufio.mod
/mnt/nvme/p1/grub/x86_64-efi/efifwsetup.mod
/mnt/nvme/p1/grub/x86_64-efi/elf.mod
/mnt/nvme/p1/grub/x86_64-efi/trig.mod
/mnt/nvme/p1/grub/x86_64-efi/xzio.mod
/mnt/nvme/p1/grub/x86_64-efi/bitmap.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_rfc2268.mod
/mnt/nvme/p1/grub/x86_64-efi/videotest_checksum.mod
/mnt/nvme/p1/grub/x86_64-efi/minix3_be.mod
/mnt/nvme/p1/grub/x86_64-efi/password_pbkdf2.mod
/mnt/nvme/p1/grub/x86_64-efi/cpio.mod
/mnt/nvme/p1/grub/x86_64-efi/video.mod
/mnt/nvme/p1/grub/x86_64-efi/ntfs.mod
/mnt/nvme/p1/grub/x86_64-efi/zfs.mod
/mnt/nvme/p1/grub/x86_64-efi/videotest.mod
/mnt/nvme/p1/grub/x86_64-efi/ufs1_be.mod
/mnt/nvme/p1/grub/x86_64-efi/minix2.mod
/mnt/nvme/p1/grub/x86_64-efi/gfxmenu.mod
/mnt/nvme/p1/grub/x86_64-efi/tga.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_des.mod
/mnt/nvme/p1/grub/x86_64-efi/part_amiga.mod
/mnt/nvme/p1/grub/x86_64-efi/shift_test.mod
/mnt/nvme/p1/grub/x86_64-efi/hfspluscomp.mod
/mnt/nvme/p1/grub/x86_64-efi/terminfo.mod
/mnt/nvme/p1/grub/x86_64-efi/ldm.mod
/mnt/nvme/p1/grub/x86_64-efi/zstd.mod
/mnt/nvme/p1/grub/x86_64-efi/loopback.mod
/mnt/nvme/p1/grub/x86_64-efi/xnu.mod
/mnt/nvme/p1/grub/x86_64-efi/ls.mod
/mnt/nvme/p1/grub/x86_64-efi/file.mod
/mnt/nvme/p1/grub/x86_64-efi/sleep.mod
/mnt/nvme/p1/grub/x86_64-efi/hashsum.mod
/mnt/nvme/p1/grub/x86_64-efi/progress.mod
/mnt/nvme/p1/grub/x86_64-efi/usbserial_usbdebug.mod
/mnt/nvme/p1/grub/x86_64-efi/raid6rec.mod
/mnt/nvme/p1/grub/x86_64-efi/loadbios.mod
/mnt/nvme/p1/grub/x86_64-efi/jpeg.mod
/mnt/nvme/p1/grub/x86_64-efi/xnu_uuid_test.mod
/mnt/nvme/p1/grub/x86_64-efi/gptsync.mod
/mnt/nvme/p1/grub/x86_64-efi/spkmodem.mod
/mnt/nvme/p1/grub/x86_64-efi/newc.mod
/mnt/nvme/p1/grub/x86_64-efi/fat.mod
/mnt/nvme/p1/grub/x86_64-efi/configfile.mod
/mnt/nvme/p1/grub/x86_64-efi/cbfs.mod
/mnt/nvme/p1/grub/x86_64-efi/odc.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_sha1.mod
/mnt/nvme/p1/grub/x86_64-efi/luks.mod
/mnt/nvme/p1/grub/x86_64-efi/cbtime.mod
/mnt/nvme/p1/grub/x86_64-efi/random.mod
/mnt/nvme/p1/grub/x86_64-efi/lzopio.mod
/mnt/nvme/p1/grub/x86_64-efi/geli.mod
/mnt/nvme/p1/grub/x86_64-efi/cmp.mod
/mnt/nvme/p1/grub/x86_64-efi/lssal.mod
/mnt/nvme/p1/grub/x86_64-efi/afsplitter.mod
/mnt/nvme/p1/grub/x86_64-efi/smbios.mod
/mnt/nvme/p1/grub/x86_64-efi/normal.mod
/mnt/nvme/p1/grub/x86_64-efi/lspci.mod
/mnt/nvme/p1/grub/x86_64-efi/pgp.mod
/mnt/nvme/p1/grub/x86_64-efi/xfs.mod
/mnt/nvme/p1/grub/x86_64-efi/usbms.mod
/mnt/nvme/p1/grub/x86_64-efi/macbless.mod
/mnt/nvme/p1/grub/x86_64-efi/btrfs.mod
/mnt/nvme/p1/grub/x86_64-efi/part_plan.mod
/mnt/nvme/p1/grub/x86_64-efi/gfxterm.mod
/mnt/nvme/p1/grub/x86_64-efi/functional_test.mod
/mnt/nvme/p1/grub/x86_64-efi/all_video.mod
/mnt/nvme/p1/grub/x86_64-efi/extcmd.mod
/mnt/nvme/p1/grub/x86_64-efi/videoinfo.mod
/mnt/nvme/p1/grub/x86_64-efi/crc64.mod
/mnt/nvme/p1/grub/x86_64-efi/dm_nv.mod
/mnt/nvme/p1/grub/x86_64-efi/test_blockarg.mod
/mnt/nvme/p1/grub/x86_64-efi/lsmmap.mod
/mnt/nvme/p1/grub/x86_64-efi/part_sunpc.mod
/mnt/nvme/p1/grub/x86_64-efi/chain.mod
/mnt/nvme/p1/grub/x86_64-efi/part_bsd.mod
/mnt/nvme/p1/grub/x86_64-efi/afs.mod
/mnt/nvme/p1/grub/x86_64-efi/hexdump.mod
/mnt/nvme/p1/grub/x86_64-efi/ohci.mod
/mnt/nvme/p1/grub/x86_64-efi/search_fs_file.mod
/mnt/nvme/p1/grub/x86_64-efi/part_acorn.mod
/mnt/nvme/p1/grub/x86_64-efi/pbkdf2.mod
/mnt/nvme/p1/grub/x86_64-efi/minicmd.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_twofish.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_seed.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_cast5.mod
/mnt/nvme/p1/grub/x86_64-efi/signature_test.mod
/mnt/nvme/p1/grub/x86_64-efi/part_dvh.mod
/mnt/nvme/p1/grub/x86_64-efi/romfs.mod
/mnt/nvme/p1/grub/x86_64-efi/part_msdos.mod
/mnt/nvme/p1/grub/x86_64-efi/lsacpi.mod
/mnt/nvme/p1/grub/x86_64-efi/iorw.mod
/mnt/nvme/p1/grub/x86_64-efi/uhci.mod
/mnt/nvme/p1/grub/x86_64-efi/eval.mod
/mnt/nvme/p1/grub/x86_64-efi/ufs2.mod
/mnt/nvme/p1/grub/x86_64-efi/tpm.mod
/mnt/nvme/p1/grub/x86_64-efi/strtoull_test.mod
/mnt/nvme/p1/grub/x86_64-efi/rdmsr.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_tiger.mod
/mnt/nvme/p1/grub/x86_64-efi/lsefimmap.mod
/mnt/nvme/p1/grub/x86_64-efi/usbserial_pl2303.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_rijndael.mod
/mnt/nvme/p1/grub/x86_64-efi/hfsplus.mod
/mnt/nvme/p1/grub/x86_64-efi/terminal.mod
/mnt/nvme/p1/grub/x86_64-efi/linuxefi.mod
/mnt/nvme/p1/grub/x86_64-efi/minix3.mod
/mnt/nvme/p1/grub/x86_64-efi/regexp.mod
/mnt/nvme/p1/grub/x86_64-efi/efi_uga.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_crc.mod
/mnt/nvme/p1/grub/x86_64-efi/acpi.mod
/mnt/nvme/p1/grub/x86_64-efi/cs5536.mod
/mnt/nvme/p1/grub/x86_64-efi/jfs.mod
/mnt/nvme/p1/grub/x86_64-efi/adler32.mod
/mnt/nvme/p1/grub/x86_64-efi/efi_gop.mod
/mnt/nvme/p1/grub/x86_64-efi/exfat.mod
/mnt/nvme/p1/grub/x86_64-efi/password.mod
/mnt/nvme/p1/grub/x86_64-efi/crypto.mod
/mnt/nvme/p1/grub/x86_64-efi/part_dfly.mod
/mnt/nvme/p1/grub/x86_64-efi/search_fs_uuid.mod
/mnt/nvme/p1/grub/x86_64-efi/squash4.mod
/mnt/nvme/p1/grub/x86_64-efi/xnu_uuid.mod
/mnt/nvme/p1/grub/x86_64-efi/usbserial_ftdi.mod
/mnt/nvme/p1/grub/x86_64-efi/bsd.mod
/mnt/nvme/p1/grub/x86_64-efi/mmap.mod
/mnt/nvme/p1/grub/x86_64-efi/cbtable.mod
/mnt/nvme/p1/grub/x86_64-efi/ahci.mod
/mnt/nvme/p1/grub/x86_64-efi/test.mod
/mnt/nvme/p1/grub/x86_64-efi/sleep_test.mod
/mnt/nvme/p1/grub/x86_64-efi/syslinuxcfg.mod
/mnt/nvme/p1/grub/x86_64-efi/cat.mod
/mnt/nvme/p1/grub/x86_64-efi/gzio.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_whirlpool.mod
/mnt/nvme/p1/grub/x86_64-efi/macho.mod
/mnt/nvme/p1/grub/x86_64-efi/offsetio.mod
/mnt/nvme/p1/grub/x86_64-efi/ufs1.mod
/mnt/nvme/p1/grub/x86_64-efi/search_label.mod
/mnt/nvme/p1/grub/x86_64-efi/procfs.mod
/mnt/nvme/p1/grub/x86_64-efi/f2fs.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_blowfish.mod
/mnt/nvme/p1/grub/x86_64-efi/video_colors.mod
/mnt/nvme/p1/grub/x86_64-efi/gfxterm_background.mod
/mnt/nvme/p1/grub/x86_64-efi/msdospart.mod
/mnt/nvme/p1/grub/x86_64-efi/fixvideo.mod
/mnt/nvme/p1/grub/x86_64-efi/probe.mod
/mnt/nvme/p1/grub/x86_64-efi/fshelp.mod
/mnt/nvme/p1/grub/x86_64-efi/pcidump.mod
/mnt/nvme/p1/grub/x86_64-efi/usb.mod
/mnt/nvme/p1/grub/x86_64-efi/tftp.mod
/mnt/nvme/p1/grub/x86_64-efi/backtrace.mod
/mnt/nvme/p1/grub/x86_64-efi/at_keyboard.mod
/mnt/nvme/p1/grub/x86_64-efi/cryptodisk.mod
/mnt/nvme/p1/grub/x86_64-efi/usbserial_common.mod
/mnt/nvme/p1/grub/x86_64-efi/udf.mod
/mnt/nvme/p1/grub/x86_64-efi/testload.mod
/mnt/nvme/p1/grub/x86_64-efi/mul_test.mod
/mnt/nvme/p1/grub/x86_64-efi/halt.mod
/mnt/nvme/p1/grub/x86_64-efi/scsi.mod
/mnt/nvme/p1/grub/x86_64-efi/cpuid.mod
/mnt/nvme/p1/grub/x86_64-efi/cbls.mod
/mnt/nvme/p1/grub/x86_64-efi/nativedisk.mod
/mnt/nvme/p1/grub/x86_64-efi/net.mod
/mnt/nvme/p1/grub/x86_64-efi/legacy_password_test.mod
/mnt/nvme/p1/grub/x86_64-efi/efinet.mod
/mnt/nvme/p1/grub/x86_64-efi/mpi.mod
/mnt/nvme/p1/grub/x86_64-efi/multiboot.mod
/mnt/nvme/p1/grub/x86_64-efi/cmp_test.mod
/mnt/nvme/p1/grub/x86_64-efi/json.mod
/mnt/nvme/p1/grub/x86_64-efi/usb_keyboard.mod
/mnt/nvme/p1/grub/x86_64-efi/zfsinfo.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_dsa.mod
/mnt/nvme/p1/grub/x86_64-efi/priority_queue.mod
/mnt/nvme/p1/grub/x86_64-efi/lvm.mod
/mnt/nvme/p1/grub/x86_64-efi/sfs.mod
/mnt/nvme/p1/grub/x86_64-efi/ext2.mod
/mnt/nvme/p1/grub/x86_64-efi/png.mod
/mnt/nvme/p1/grub/x86_64-efi/tar.mod
/mnt/nvme/p1/grub/x86_64-efi/gfxterm_menu.mod
/mnt/nvme/p1/grub/x86_64-efi/datetime.mod
/mnt/nvme/p1/grub/x86_64-efi/aout.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_md5.mod
/mnt/nvme/p1/grub/x86_64-efi/video_fb.mod
/mnt/nvme/p1/grub/x86_64-efi/hello.mod
/mnt/nvme/p1/grub/x86_64-efi/hfs.mod
/mnt/nvme/p1/grub/x86_64-efi/minix2_be.mod
/mnt/nvme/p1/grub/x86_64-efi/loadenv.mod
/mnt/nvme/p1/grub/x86_64-efi/help.mod
/mnt/nvme/p1/grub/x86_64-efi/time.mod
/mnt/nvme/p1/grub/x86_64-efi/mdraid1x.mod
/mnt/nvme/p1/grub/x86_64-efi/part_gpt.mod
/mnt/nvme/p1/grub/x86_64-efi/true.mod
/mnt/nvme/p1/grub/x86_64-efi/datehook.mod
/mnt/nvme/p1/grub/x86_64-efi/read.mod
/mnt/nvme/p1/grub/x86_64-efi/minix_be.mod
/mnt/nvme/p1/grub/x86_64-efi/linux16.mod
/mnt/nvme/p1/grub/x86_64-efi/raid5rec.mod
/mnt/nvme/p1/grub/x86_64-efi/cmdline_cat_test.mod
/mnt/nvme/p1/grub/x86_64-efi/disk.mod
/mnt/nvme/p1/grub/x86_64-efi/setpci.mod
/mnt/nvme/p1/grub/x86_64-efi/setjmp.mod
/mnt/nvme/p1/grub/x86_64-efi/testspeed.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_camellia.mod
/mnt/nvme/p1/grub/x86_64-efi/memrw.mod
/mnt/nvme/p1/grub/x86_64-efi/wrmsr.mod
/mnt/nvme/p1/grub/x86_64-efi/reboot.mod
/mnt/nvme/p1/grub/x86_64-efi/lsefisystab.mod
/mnt/nvme/p1/grub/x86_64-efi/part_apple.mod
/mnt/nvme/p1/grub/x86_64-efi/archelp.mod
/mnt/nvme/p1/grub/x86_64-efi/pbkdf2_test.mod
/mnt/nvme/p1/grub/x86_64-efi/font.mod
/mnt/nvme/p1/grub/x86_64-efi/appleldr.mod
/mnt/nvme/p1/grub/x86_64-efi/multiboot2.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_rmd160.mod
/mnt/nvme/p1/grub/x86_64-efi/div_test.mod
/mnt/nvme/p1/grub/x86_64-efi/parttool.mod
/mnt/nvme/p1/grub/x86_64-efi/ehci.mod
/mnt/nvme/p1/grub/x86_64-efi/gettext.mod
/mnt/nvme/p1/grub/x86_64-efi/keystatus.mod
/mnt/nvme/p1/grub/x86_64-efi/exfctest.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_rsa.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_md4.mod
/mnt/nvme/p1/grub/x86_64-efi/ata.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_idea.mod
/mnt/nvme/p1/grub/x86_64-efi/ctz_test.mod
/mnt/nvme/p1/grub/x86_64-efi/reiserfs.mod
/mnt/nvme/p1/grub/x86_64-efi/keylayouts.mod
/mnt/nvme/p1/grub/x86_64-efi/bitmap_scale.mod
/mnt/nvme/p1/grub/x86_64-efi/serial.mod
/mnt/nvme/p1/grub/x86_64-efi/linux.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_sha256.mod
/mnt/nvme/p1/grub/x86_64-efi/part_sun.mod
/mnt/nvme/p1/grub/x86_64-efi/mdraid09_be.mod
/mnt/nvme/p1/grub/x86_64-efi/zfscrypt.mod
/mnt/nvme/p1/grub/x86_64-efi/affs.mod
/mnt/nvme/p1/grub/x86_64-efi/echo.mod
/mnt/nvme/p1/grub/x86_64-efi/minix.mod
/mnt/nvme/p1/grub/x86_64-efi/search.mod
/mnt/nvme/p1/grub/x86_64-efi/morse.mod
/mnt/nvme/p1/grub/x86_64-efi/video_bochs.mod
/mnt/nvme/p1/grub/x86_64-efi/setjmp_test.mod
/mnt/nvme/p1/grub/x86_64-efi/div.mod
/mnt/nvme/p1/grub/x86_64-efi/pata.mod
/mnt/nvme/p1/grub/x86_64-efi/date.mod
/mnt/nvme/p1/grub/x86_64-efi/boot.mod
/mnt/nvme/p1/grub/x86_64-efi/mdraid09.mod
/mnt/nvme/p1/grub/x86_64-efi/cbmemc.mod
/mnt/nvme/p1/grub/x86_64-efi/blocklist.mod
/mnt/nvme/p1/grub/x86_64-efi/iso9660.mod
/mnt/nvme/p1/grub/x86_64-efi/gcry_sha512.mod
/mnt/nvme/p1/grub/x86_64-efi/moddep.lst
/mnt/nvme/p1/grub/x86_64-efi/command.lst
/mnt/nvme/p1/grub/x86_64-efi/fs.lst
/mnt/nvme/p1/grub/x86_64-efi/partmap.lst
/mnt/nvme/p1/grub/x86_64-efi/parttool.lst
/mnt/nvme/p1/grub/x86_64-efi/video.lst
/mnt/nvme/p1/grub/x86_64-efi/crypto.lst
/mnt/nvme/p1/grub/x86_64-efi/terminal.lst
/mnt/nvme/p1/grub/x86_64-efi/modinfo.sh
/mnt/nvme/p1/grub/x86_64-efi/core.efi
/mnt/nvme/p1/grub/x86_64-efi/grub.efi
/mnt/nvme/p1/grub/fonts
/mnt/nvme/p1/grub/fonts/unicode.pf2
/mnt/nvme/p1/grub/locale
/mnt/nvme/p1/grub/locale/en_GB.mo
/mnt/nvme/p1/grub/locale/en_AU.mo
/mnt/nvme/p1/grub/locale/en@quot.mo
/mnt/nvme/p1/grub/locale/en_CA.mo
/mnt/nvme/p1/grub/grubenv
/mnt/nvme/p1/grub/grub.cfg
/mnt/nvme/p1/EFI
/mnt/nvme/p1/EFI/ubuntu
/mnt/nvme/p1/EFI/ubuntu/grubx64.efi
/mnt/nvme/p1/EFI/ubuntu/shimx64.efi
/mnt/nvme/p1/EFI/ubuntu/mmx64.efi
/mnt/nvme/p1/EFI/ubuntu/BOOTX64.CSV
/mnt/nvme/p1/EFI/ubuntu/grub.cfg
/mnt/nvme/p1/EFI/BOOT
/mnt/nvme/p1/EFI/BOOT/BOOTX64.EFI
/mnt/nvme/p1/EFI/BOOT/fbx64.efi
/mnt/nvme/p1/EFI/BOOT/mmx64.efi
/mnt/nvme/p1/EFI/Insyde

```

---

### Post by ca-scribner on 2024-01-11
Yeah my backup situation is... so-so.  The really important stuff is backed up, but there's some important-ish stuff not :/

---

### Post by MAFoElffen on 2024-01-11
Dump the information like like this:
```

sudo zdb

```
Look i the section that starts in column 1, with rpool. Look under children > path to look for the drives to see what might be missing with that error you were getting when you tried to import rpool.

---

### Post by ca-scribner on 2024-01-12
I get

```

sudo zdb
cannot open '/etc/zfs/zpool.cache': No such file or directory

ll /etc/zfs
total 10
drwxr-xr-x 4 root root   76 Aug  7 22:56 ./
drwxr-xr-x 1 root root  600 Jan 11 18:25 ../
drwxr-xr-x 2 root root  369 Aug  7 22:56 zed.d/
-rw-r--r-- 1 root root 9450 Jan 18  2023 zfs-functions
drwxr-xr-x 2 root root  648 Aug  7 22:56 zpool.d/


```

I might have gotten a little further on importing... using the UUID for /dev/nvme0n1p4 from (everything below using `sudo su -`)

```

lkid
/dev/nvme0n1p1: UUID="680C-6402" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="57e4d738-860c-4c28-acd1-fda575f846ed"
/dev/nvme0n1p3: LABEL="bpool" UUID="493191063445844317" UUID_SUB="934484222053174471" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="5b071324-e0aa-1847-a7a4-327192b4f1f9"
/dev/nvme0n1p4: LABEL="rpool" UUID="6153821987050407745" UUID_SUB="14470870218067292293" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="9ce2f3c6-a683-9941-9ae0-a469a45ea6d4"
/dev/sda1: LABEL="UBUNTU 22_0" UUID="DC1E-7100" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="0f9daad5-01"
/dev/loop1: TYPE="squashfs"
/dev/nvme0n1p2: UUID="54b9a209-72c0-4ded-9ded-b10f9564d087" TYPE="crypto_LUKS" PARTUUID="5666973e-7f8b-1841-a6de-d2112bd2cf3e"
/dev/loop8: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs

```

I can do:
```

zpool import -f -d /dev/disk/by-uuid/6153821987050407745
   pool: rpool
     id: 6153821987050407745
  state: ONLINE
status: The pool was last accessed by another system.
 action: The pool can be imported using its name or numeric identifier and
    the '-f' flag.
   see: https://openzfs.github.io/openzfs-docs/msg/ZFS-8000-EY
 config:

    rpool                  ONLINE
      6153821987050407745  ONLINE

```

and same for bpool:

```

zpool import -f -d /dev/disk/by-uuid/493191063445844317 -R /mnt
   pool: bpool
     id: 493191063445844317
  state: ONLINE
status: The pool was last accessed by another system.
 action: The pool can be imported using its name or numeric identifier and
    the '-f' flag.
   see: https://openzfs.github.io/openzfs-docs/msg/ZFS-8000-EY
 config:

    bpool                 ONLINE
      493191063445844317  ONLINE

```

I'm not sure if it did anything though.  It looked like from your outputs that `zpool import -f ...` is silent, but for me it keeps spitting out the pool, id, etc details.

---

### Post by #&amp;thj^% on 2024-01-12
> **ca-scribner said:**
> 

I'm not sure if it did anything though.  It looked like from your outputs that `zpool import -f ...` is silent, but for me it keeps spitting out the pool, id, etc details.

The "-f" flag is force.
Is it still spitting more out?
```
zdb
tank:
    version: 5000
    name: 'tank'
    state: 0
    txg: 11419
    pool_guid: 10926758658995060061
    errata: 0
    hostid: 550019688
    hostname: 'parrot'
    com.delphix:has_per_vdev_zaps
    vdev_children: 1
    vdev_tree:
        type: 'root'
        id: 0
        guid: 10926758658995060061
        create_txg: 4
        com.klarasystems:vdev_zap_root: 129
        children[0]:
            type: 'disk'
            id: 0
            guid: 10795441740398861942
            path: '/dev/sda2'
            whole_disk: 0
            metaslab_array: 256
            metaslab_shift: 32
            ashift: 11
            asize: 499564150784
            is_log: 0
            create_txg: 4
            com.delphix:vdev_zap_leaf: 130
            com.delphix:vdev_zap_top: 131
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data
        com.klarasystems:vdev_zaps_v2

```

---

### Post by ca-scribner on 2024-01-12
for some reason I cannot edit my previous message, but there was a minor typo.  I had done `zpool import -f -d /dev/disk/by-uuid/6153821987050407745 -R /mnt` (the `-R /mnt` was missing).  

I'll restart and walk through things again in case something was path dependent, but yes running with `-f` still put info that info I pasted to the terminal

---

### Post by #&amp;thj^% on 2024-01-12
> **ca-scribner said:**
> for some reason I cannot edit my previous message, but there was a minor typo.  I had done `zpool import -f -d /dev/disk/by-uuid/6153821987050407745 -R /mnt` (the `-R /mnt` was missing).  
yep we knew that>>>`-R /mnt` but is nice that you show others the left out part. :)
> **ca-scribner said:**
> 
I'll restart and walk through things again in case something was path dependent, but yes running with `-f` still put info that info I pasted to the terminal

I had totally written this one off, but your determination is impressive.

EDIT: BTW this would be a good time to grab your missed back-ups, for completeness.

---

### Post by ca-scribner on 2024-01-12
hah, I am rather stubborn sometimes ;)  as you can tell I don't know much about the topic, but there's something about this that feels *so close* that I can't drop it :D

Rebooted, redid the `zpool imports`, and still with `-f` they spit out the same info to the terminal.  Still have the same trouble with `zdb`, but I can do:

```

sudo su -

zdb
cannot open '/etc/zfs/zpool.cache': No such file or directory


zdb -e rpool | head -n 200

Configuration for import:
        vdev_children: 1
        version: 5000
        pool_guid: 6153821987050407745
        name: 'rpool'
        state: 0
        hostid: 104614418
        hostname: 'framework'
        vdev_tree:
            type: 'root'
            id: 0
            guid: 6153821987050407745
            children[0]:
                type: 'disk'
                id: 0
                guid: 14470870218067292293
                whole_disk: 0
                metaslab_array: 66
                metaslab_shift: 33
                ashift: 12
                asize: 995367059456
                is_log: 0
                DTL: 10141
                create_txg: 4
                degraded: 1
                aux_state: 'err_exceeded'
                path: '/dev/disk/by-partuuid/9ce2f3c6-a683-9941-9ae0-a469a45ea6d4'
        load-policy:
            load-request-txg: 18446744073709551615
            load-rewind-policy: 2

MOS Configuration:
        version: 5000
        name: 'rpool'
        state: 0
        txg: 36209561
        pool_guid: 6153821987050407745
        errata: 0
        hostid: 104614418
        hostname: 'framework'
        com.delphix:has_per_vdev_zaps
        vdev_children: 1
        vdev_tree:
            type: 'root'
            id: 0
            guid: 6153821987050407745
            create_txg: 4
            children[0]:
                type: 'disk'
                id: 0
                guid: 14470870218067292293
                path: '/dev/disk/by-partuuid/9ce2f3c6-a683-9941-9ae0-a469a45ea6d4'
                whole_disk: 0
                metaslab_array: 66
                metaslab_shift: 33
                ashift: 12
                asize: 995367059456
                is_log: 0
                DTL: 10141
                create_txg: 4
                com.delphix:vdev_zap_leaf: 129
                com.delphix:vdev_zap_top: 130
                degraded: 1
                aux_state: 'err_exceeded'
        features_for_read:
            com.delphix:hole_birth
            com.delphix:embedded_data

Uberblock:
    magic = 0000000000bab10c
    version = 5000
    txg = 36657508
    guid_sum = 2177948131408148422
    timestamp = 1704667778 UTC = Sun Jan  7 22:49:38 2024
    mmp_magic = 00000000a11cea11
    mmp_delay = 0
    mmp_valid = 0
    checkpoint_txg = 0

All DDTs are empty

Metaslabs:
    vdev          0      ms_unflushed_phys object 70
    metaslabs   115   offset                spacemap          free        
    ---------------   -------------------   ---------------   ------------
    metaslab      0   offset            0   spacemap     78   free     800M
    On-disk histogram:        fragmentation 54
             12:   7447 ****************************************
             13:   6163 **********************************
             14:   4194 ***********************
             15:   2064 ************
             16:   1086 ******
             17:    745 *****
             18:    451 ***
             19:    166 *
             20:     42 *
             21:      2 *
space map object 78:
  smp_length = 0x6e140
  smp_alloc = 0x1cdfc7000
    Flush data:
    unflushed txg=36657508

    metaslab      1   offset    200000000   spacemap     77   free    1.51G
    On-disk histogram:        fragmentation 57
             12:  12550 ****************************************
             13:  10107 *********************************
             14:   8691 ****************************
             15:   4848 ****************
             16:   3279 ***********
             17:   1664 ******
             18:    753 ***
             19:    215 *
             20:     38 *
             21:      3 *


zdb -e bpool

Configuration for import:
        vdev_children: 1
        version: 5000
        pool_guid: 493191063445844317
        name: 'bpool'
        state: 0
        hostid: 104614418
        hostname: 'framework'
        vdev_tree:
            type: 'root'
            id: 0
            guid: 493191063445844317
            children[0]:
                type: 'disk'
                id: 0
                guid: 934484222053174471
                whole_disk: 0
                metaslab_array: 131
                metaslab_shift: 27
                ashift: 12
                asize: 2142765056
                is_log: 0
                DTL: 263
                create_txg: 4
                path: '/dev/disk/by-partuuid/5b071324-e0aa-1847-a7a4-327192b4f1f9'
        load-policy:
            load-request-txg: 18446744073709551615
            load-rewind-policy: 2

MOS Configuration:
        version: 5000
        name: 'bpool'
        state: 0
        txg: 7329848
        pool_guid: 493191063445844317
        errata: 0
        hostid: 104614418
        hostname: 'framework'
        com.delphix:has_per_vdev_zaps
        vdev_children: 1
        vdev_tree:
            type: 'root'
            id: 0
            guid: 493191063445844317
            create_txg: 4
            children[0]:
                type: 'disk'
                id: 0
                guid: 934484222053174471
                path: '/dev/disk/by-partuuid/5b071324-e0aa-1847-a7a4-327192b4f1f9'
                whole_disk: 0
                metaslab_array: 131
                metaslab_shift: 27
                ashift: 12
                asize: 2142765056
                is_log: 0
                DTL: 263
                create_txg: 4
                com.delphix:vdev_zap_leaf: 129
                com.delphix:vdev_zap_top: 130
        features_for_read:
            com.delphix:embedded_data
            com.delphix:hole_birth

Uberblock:
    magic = 0000000000bab10c
    version = 5000
    txg = 7429653
    guid_sum = 1427675285499018788
    timestamp = 1704626259 UTC = Sun Jan  7 11:17:39 2024
    mmp_magic = 00000000a11cea11
    mmp_delay = 0
    mmp_valid = 0
    checkpoint_txg = 0

All DDTs are empty

Metaslabs:
    vdev          0   
    metaslabs    15   offset                spacemap          free        
    ---------------   -------------------   ---------------   ------------
    metaslab      0   offset            0   spacemap    141   free    3.12M
    On-disk histogram:        fragmentation 64
             12:     10 **********
             13:     36 ************************************
             14:      1 *
             15:      9 *********
             16:     20 ********************
             17:      3 ***
space map object 141:
  smp_length = 0x8910
  smp_alloc = 0x7ce2000
    metaslab      1   offset      8000000   spacemap    140   free    1.78M
    On-disk histogram:        fragmentation 65
             12:      4 ****
             13:      8 ********
             14:      6 ******
             15:     11 ***********
             16:     13 *************

...(truncated)

```

which I think is the what we're after?

---

### Post by #&amp;thj^% on 2024-01-12
This jumps out for me:
```
 metaslab      1   offset    200000000   spacemap     77   free    1.51G
    On-disk histogram:        fragmentation 57
             12:  12550 ****************************************
```
This as well:
```
space map object 141:
  smp_length = 0x8910
  smp_alloc = 0x7ce2000
    metaslab      1   offset      8000000   spacemap    140   free    1.78M
    On-disk histogram:        fragmentation 65
```
But to answer, yes this good info to act on.
I'm back and forth @work and forums today. 
This is really MAFoElffen specialty so I'm going to let him guide you now.

Good Luck, and if you can pull what you need for a complete back-up.
Just in case!

---

### Post by MAFoElffen on 2024-01-12
When you start out all over again, before you import, do
```

zpool export -a

```

---

### Post by #&amp;thj^% on 2024-01-13
> **MAFoElffen said:**
> When you start out all over again, before you import, do
```

zpool export -a

```

+1

---

### Post by MAFoElffen on 2024-01-13
Anything yet?

---

### Post by ca-scribner on 2024-01-14
I swear I've been able to do everything I need to, but never in the same session.

I tried redoing everything after first doing `zpool export -a`, but I get the same "cannot import 'rpool': one or more devices is currently unavailable'.  I did figure out why `zpool import -f -d /dev/disk/by-uuid/UUID` was giving me trouble at least - I was incorrectly doing "...by-uuid/UUID" when it should have been "...by-uuid UUID".  But fixing that, I still get the "one or more devices is currently unavailable" error.

To try things another way, I booted using zfsbootmenu and that dropped me into a recovery shell.  From that recovery shell, rpool and bpool actually show up in `zpool status` and `/dev/zvol/rpool/keystore` is actually discoverable.  Which is great, except in that recovery shell **I dont have cryptsetup** :( so I don't know how to actually open the keystore to then unlock everything else.  Not sure why zpool in the zfsbootmenu can open things, but zpool in the Ubuntu Live USB cannot.  *maybe* its a different version of zpool?  I'll try that out.  But afaict the data is still available so it feels like there's a way to do this.  

As a feeble attempt, I tried taking cryptsetup plus all the dynamic libraries (`ldd cryptsetup`) and putting them on a USB to access from the recovery shell but running that gave a segmentation fault (I assume its compiled for the wrong thing, and I'm not sure what I'd need to compile it to to get it to work...)

---

### Post by ca-scribner on 2024-01-14
gah so close... 

Running again from the zfsbootmenu's recovery shell (which uses void linux), I've copied in `cryptsetup` and the libs from `ldd cryptsetup` from a void linux live boot and gotten closer.  I can now do:

`cryptsetup -v open /dev/zvol/rpool/keystore keystore_rpool`

which asks for (and I think accepts my passphrase!), but then fails with:
device-mapper: reload ioctl on   failedL Invalid argument
Command failed with code -4 (wrong device or file specified)

and a message in dmesg of:
table: 254:0: crypt: unknown target type
ioctl: error adding target to table

which I think means I'm missing something (maybe dm-crypt?  still doing some googling...)

---

### Post by ca-scribner on 2024-01-15
I think I finally have it.  Here is what I've done:

```

sudo su -

# note the `-o readonly=on`.  Because there were data issues in the pools, they refused to import unless set to readonly
zpool import rpool -R /mnt -N -o readonly=on -f
zpool import bpool -R /mnt -N -o readonly=on -f

cryptsetup open -v /dev/zvol/rpool/keystore keystore-rpool
# enter passphrase

ls /dev/mapper
# control  keystore-rpool
ls /dev/zvol/rpool/keystore
# /dev/zvol/rpool/keystore

mount -o ro,noload /dev/mapper/keystore-rpool  /media

cat /media/system.key | zfs load-key -L prompt rpool

zfs mount $(zfs list | grep -m1 -e '^rpool\/ROOT\/ubuntu_' | awk '{print $1}' )
zfs mount $(zfs list | grep -m1 -e '^bpool\/BOOT\/ubuntu_' | awk '{print $1}' )
zfs mount -a

ls /mnt
# all my stuff!

```

I'm now in the process of pulling all the data I need out of the drive, then I'll probably just replace the drive and install ubuntu fresh on a new one just to be safe.  Not sure if the issues were software or hardware, but I am not a trustworthy person :D

ty MAFoElffen and 1fallen for all your help!  MAFoElfen, I wonder if the boot repair might be able to learn some things from this too.  The `-o readonly=on` came from the zfsbootmenu folks -- if their recovery shell couldn't import something, it would failover to using `-o readonly=on` (and also spoofing the hostid to the old drive's hostid, so they didn't need -f).  That's why in their boot drive I could get into rpool/bpool initially.  Might be useful as a fallback for boot repair, too

---

### Post by #&amp;thj^% on 2024-01-15
> **ca-scribner said:**
> I think I finally have it.  Here is what I've done:

```

sudo su -

# note the `-o readonly=on`.  Because there were data issues in the pools, they refused to import unless set to readonly
zpool import rpool -R /mnt -N -o readonly=on -f
zpool import bpool -R /mnt -N -o readonly=on -f

cryptsetup open -v /dev/zvol/rpool/keystore keystore-rpool
# enter passphrase

ls /dev/mapper
# control  keystore-rpool
ls /dev/zvol/rpool/keystore
# /dev/zvol/rpool/keystore

mount -o ro,noload /dev/mapper/keystore-rpool  /media

cat /media/system.key | zfs load-key -L prompt rpool

zfs mount $(zfs list | grep -m1 -e '^rpool\/ROOT\/ubuntu_' | awk '{print $1}' )
zfs mount $(zfs list | grep -m1 -e '^bpool\/BOOT\/ubuntu_' | awk '{print $1}' )
zfs mount -a

ls /mnt
# all my stuff!

```

I'm now in the process of pulling all the data I need out of the drive, then I'll probably just replace the drive and install ubuntu fresh on a new one just to be safe.  Not sure if the issues were software or hardware, but I am not a trustworthy person :D

ty MAFoElffen and 1fallen for all your help!  MAFoElfen, I wonder if the boot repair might be able to learn some things from this too.  The `-o readonly=on` came from the zfsbootmenu folks -- if their recovery shell couldn't import something, it would failover to using `-o readonly=on` (and also spoofing the hostid to the old drive's hostid, so they didn't need -f).  That's why in their boot drive I could get into rpool/bpool initially.  Might be useful as a fallback for boot repair, too
Once again impressive determination!! =d>
MAFoElffen  and I are both waiting for the boot-repair maintainer to get a hold of us.

---

### Post by MAFoElffen on 2024-01-15
Yes, Yann finally got a hold of me with a short message, I've passed on a few things... Then he disappeared again. Dang. LOL

Glad to hear you are in and recovering your data.

While you are in... Or after you have your new install up-and-running ... That's a good choice if you cannot mount it without it being r/w, becaseu you can't make a repair or do a scrub in r/o mode...

Document everything in an Admin Journal Note document. This is what I do form my systems. I include all my zpool and zfs stats... and add the output of 'zdb'. <-- That way I have a record of all my Zpool UUIS's & ID's.

Also keep a record of how to chroot into your system. That kind of thing is handy.

---

### Post by ca-scribner on 2024-01-15
100% agreed!  Good ideas for things to keep handy. That’s also why I keep coming back here and doing the “ok this is everything I did” posts, because at least then I’ve written it somewhere ;)

---

