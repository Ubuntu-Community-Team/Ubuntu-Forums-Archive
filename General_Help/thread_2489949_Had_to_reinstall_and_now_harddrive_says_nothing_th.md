---
title: "Had to reinstall and now harddrive says nothing there ??"
date: 2023-08-15
forum: General Help
---

### Post by creature1963 on 2023-08-15
I had to reinstall ubuntu 22.04 LTS yesterday 

and now my 2nd ssd hard drive it says the drive is empty!.

As this is my backup device of important files n stuff I know this not to be true.

How can I get this issue sorted ??

Many thanks in advance

Mr C

---

### Post by Rubi1200 on 2023-08-16
You posted in the System 76 sub-forum. Not something I am familiar with at all.

However, please run the boot info script in my signature from a liveUSB. Do not attempt any repairs, just post the script results here so we can see what is going on.

Hopefully, we can help you get this sorted out.

---

### Post by creature1963 on 2023-08-16
Sorry new to these forums and struggled to find a folder suited to my question.

Can you please elaberate on what you want and more importantly how to do it.

Sorry altho I have been a user for many years I have never dealt in issues like this so at this part of Ubuntu I am a complete novis.

Many thanks in advance

Mr C

---

### Post by creature1963 on 2023-08-16
Is this what you are looking for ?

```
boot-repair-4ppa2056                                              [COLOR=#666666][[/COLOR]20230816_1348[COLOR=#666666]][/COLOR]

[COLOR=#666666]==============================[/COLOR] Boot Info [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu [COLOR=#666666]22[/COLOR].04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

nvme1n1: _______________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


[COLOR=#666666]================================[/COLOR] [COLOR=#666666]1[/COLOR] OS [COLOR=#B8860B]detected[/COLOR] [COLOR=#666666]=================================[/COLOR]

OS#1:   Ubuntu [COLOR=#666666]22[/COLOR].04.3 LTS on [COLOR=#B8860B]nvme0n1p2[/COLOR]

[COLOR=#666666]================================[/COLOR] Host/Hardware [COLOR=#666666]=================================[/COLOR]

CPU architecture: [COLOR=#666666]64[/COLOR]-bit
Video: GP106 [COLOR=#666666][[/COLOR]GeForce GTX [COLOR=#666666]1060[/COLOR] 6GB[COLOR=#666666]][/COLOR] EFI VGA from NVIDIA Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.2.0-26-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]28c03a52-daf8-4a78-af3d-bd0fd1ae6081 ro quiet splash vt.handoff[COLOR=#666666]=[/COLOR][COLOR=#666666]7[/COLOR]
df -Th / : /dev/nvme0n1p2 ext4  916G   17G  853G   [COLOR=#666666]2[/COLOR]% /

[COLOR=#666666]=====================================[/COLOR] [COLOR=#B8860B]UEFI[/COLOR] [COLOR=#666666]=====================================[/COLOR]

BIOS/UEFI firmware: [COLOR=#666666]1301[/COLOR][COLOR=#666666]([/COLOR][COLOR=#666666]5[/COLOR].12[COLOR=#666666])[/COLOR] from American Megatrends Inc.
The firmware is EFI-compatible, and is [COLOR=#AA22FF]set[/COLOR] in EFI-mode [COLOR=#AA22FF]**for**[/COLOR] this installed-session.
SecureBoot disabled [COLOR=#666666]([/COLOR]confirmed by mokutil[COLOR=#666666])[/COLOR].
BootCurrent: [COLOR=#666666]0003[/COLOR]
Timeout: [COLOR=#666666]1[/COLOR] seconds
BootOrder: [COLOR=#666666]0003[/COLOR]
Boot0003* ubuntu    HD[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR],GPT,1d9a5aa8-f8a0-427e-bd6d-0923856ee58e,0x800,0x100000[COLOR=#666666])[/COLOR]/File[COLOR=#666666]([/COLOR][COLOR=#BB6622]**\E**[/COLOR]FI[COLOR=#BB6622]**\U**[/COLOR]BUNTU[COLOR=#BB6622]**\S**[/COLOR]HIMX64.EFI[COLOR=#666666])[/COLOR]


[COLOR=#666666]=============================[/COLOR] Drive/Partition [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]=============================[/COLOR]

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes
nvme1n1    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1p2    : is-os,    [COLOR=#666666]64[/COLOR], apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
nvme0n1p1    : no-os,    [COLOR=#666666]64[/COLOR], nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1p2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]3[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1p2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ___________________________________________________________

Disk nvme0n1: [COLOR=#666666]931[/COLOR].51 GiB, [COLOR=#666666]1000204886016[/COLOR] bytes, [COLOR=#666666]1953525168[/COLOR] sectors
Disk identifier: F36DB6CE-D279-4D96-A558-0A6C02220FA6
            Start        End    Sectors  Size Type
nvme0n1p1    [COLOR=#666666]2048[/COLOR]    [COLOR=#666666]1050623[/COLOR]    [COLOR=#666666]1048576[/COLOR]  512M EFI System
nvme0n1p2 [COLOR=#666666]1050624[/COLOR] [COLOR=#666666]1953523711[/COLOR] [COLOR=#666666]1952473088[/COLOR]  931G Linux filesystem
Disk nvme1n1: [COLOR=#666666]1[/COLOR].82 TiB, [COLOR=#666666]2000398934016[/COLOR] bytes, [COLOR=#666666]3907029168[/COLOR] sectors

parted -lm [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1:1000GB:nvme:512:512:gpt:Seagate FireCuda [COLOR=#666666]530[/COLOR] ZP1000GM30013:;
[COLOR=#666666]1[/COLOR]:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
[COLOR=#666666]2[/COLOR]:538MB:1000GB:1000GB:ext4::;
nvme1n1:2000GB:nvme:512:512:loop:Seagate FireCuda [COLOR=#666666]530[/COLOR] ZP2000GM30013:;
[COLOR=#666666]1[/COLOR]:0.00B:2000GB:2000GB:ext4::;

blkid [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL        PARTLABEL
sda                                                                                                         
nvme0n1                                                                                                     
&#9500;&#9472;nvme0n1p1 vfat     16FE-363F                            1d9a5aa8-f8a0-427e-bd6d-0923856ee58e              EFI System Partition
&#9492;&#9472;nvme0n1p2 ext4     28c03a52-daf8-4a78-af3d-bd0fd1ae6081 1194832f-77ac-4a67-a93d-a1f3b6e2e449              
nvme1n1     ext4     f1285141-d59b-495a-8437-5b6981c59f88                                      FireCuda 2tb 

Mount points [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _______________________________________________________

                                     Avail Use% Mounted on
/dev/nvme0n1p2                      [COLOR=#666666]852[/COLOR].7G   [COLOR=#666666]2[/COLOR]% /
/dev/nvme1n1                          [COLOR=#666666]1[/COLOR].7T   [COLOR=#666666]0[/COLOR]% /mnt/FireCuda 2tb

Mount options [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: [COLOR=#B8860B]______________________________________________________[/COLOR]


[COLOR=#666666]===================[/COLOR] nvme0n1p1/efi/ubuntu/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]===================[/COLOR]

search.fs_uuid 28c03a52-daf8-4a78-af3d-bd0fd1ae6081 root 
[COLOR=#AA22FF]set[/COLOR] [COLOR=#B8860B]prefix[/COLOR][COLOR=#666666]=([/COLOR][COLOR=#B8860B]$root[/COLOR][COLOR=#666666])[/COLOR][COLOR=#BB4444]'/boot/grub'[/COLOR]
configfile [COLOR=#B8860B]$prefix[/COLOR]/grub.cfg

[COLOR=#666666]===================[/COLOR] nvme0n1p2/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]====================[/COLOR]

Ubuntu   28c03a52-daf8-4a78-af3d-bd0fd1ae6081
Ubuntu, with Linux [COLOR=#666666]6[/COLOR].2.0-26-generic   28c03a52-daf8-4a78-af3d-bd0fd1ae6081
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].15.0-43-generic   28c03a52-daf8-4a78-af3d-bd0fd1ae6081
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]
UEFI Firmware Settings   uefi-firmware
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#666666]========================[/COLOR] nvme0n1p2/etc/fstab [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]========================[/COLOR]

[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/nvme0n1p2 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]28c03a52-daf8-4a78-af3d-bd0fd1ae6081 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro [COLOR=#666666]0[/COLOR]       [COLOR=#666666]1[/COLOR]
[COLOR=#008800]*# /boot/efi was on /dev/nvme0n1p1 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]16FE-363F  /boot/efi       vfat    [COLOR=#B8860B]umask[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]0077[/COLOR]      [COLOR=#666666]0[/COLOR]       [COLOR=#666666]1[/COLOR]
/swapfile                                 none            swap    sw              [COLOR=#666666]0[/COLOR]       [COLOR=#666666]0[/COLOR]
[COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR]FireCuda0402tb /mnt/FireCuda0402tb auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name[COLOR=#666666]=[/COLOR]FireCuda%202TB [COLOR=#666666]0[/COLOR] [COLOR=#B8860B]0[/COLOR]

[COLOR=#666666]====================[/COLOR] nvme0n1p2/etc/default/grub [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]=====================[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT_STYLE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"hidden"[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"`lsb_release -i -s 2> /dev/null || echo Debian`"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]
[COLOR=#AA22FF]export[/COLOR] [COLOR=#B8860B]GRUB_COLOR_NORMAL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"cyan/magenta"[/COLOR]
[COLOR=#AA22FF]export[/COLOR] [COLOR=#B8860B]GRUB_COLOR_HIGHLIGHT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"green/yellow"[/COLOR]
[COLOR=#B8860B]GRUB_SAVEDEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"false"[/COLOR]
[COLOR=#666666]=================[/COLOR] nvme0n1p2: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
 [COLOR=#666666]352[/COLOR].397457123 [COLOR=#666666]=[/COLOR] [COLOR=#666666]378[/COLOR].383888384  boot/grub/grub.cfg                             [COLOR=#666666]1[/COLOR]
 [COLOR=#666666]562[/COLOR].662235260 [COLOR=#666666]=[/COLOR] [COLOR=#666666]604[/COLOR].153974784  boot/vmlinuz                                   [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]812[/COLOR].711910248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]872[/COLOR].642768896  boot/vmlinuz-5.15.0-43-generic                 [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]562[/COLOR].662235260 [COLOR=#666666]=[/COLOR] [COLOR=#666666]604[/COLOR].153974784  boot/vmlinuz-6.2.0-26-generic                  [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]812[/COLOR].711910248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]872[/COLOR].642768896  boot/vmlinuz.old                               [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]550[/COLOR].955223083 [COLOR=#666666]=[/COLOR] [COLOR=#666666]591[/COLOR].583666176  boot/initrd.img                                [COLOR=#666666]1[/COLOR]
 [COLOR=#666666]548[/COLOR].672847748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]589[/COLOR].132984320  boot/initrd.img-5.15.0-43-generic              [COLOR=#666666]3[/COLOR]
 [COLOR=#666666]550[/COLOR].955223083 [COLOR=#666666]=[/COLOR] [COLOR=#666666]591[/COLOR].583666176  boot/initrd.img-6.2.0-26-generic               [COLOR=#666666]1[/COLOR]
 [COLOR=#666666]548[/COLOR].672847748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]589[/COLOR].132984320  boot/initrd.img.old                            [COLOR=#B8860B]3[/COLOR]

[COLOR=#666666]===================[/COLOR] nvme0n1p2: ls -l /etc/grub.d/ [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]===================[/COLOR]

-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]18683[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 10_linux
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]43031[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 10_linux_zfs
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]14387[/COLOR] Dec [COLOR=#666666]18[/COLOR]  [COLOR=#666666]2022[/COLOR] 20_linux_xen
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]13369[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 30_os-prober
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root  [COLOR=#666666]1372[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 30_uefi-firmware
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]700[/COLOR] Feb [COLOR=#666666]19[/COLOR]  [COLOR=#666666]2022[/COLOR] 35_fwupd
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]214[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 40_custom
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]215[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 41_custom
drwxr-xr-x [COLOR=#666666]4[/COLOR] root root  [COLOR=#666666]4096[/COLOR] Aug [COLOR=#666666]15[/COLOR] [COLOR=#666666]01[/COLOR]:45 backup



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p2,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in [COLOR=#AA22FF]**case**[/COLOR] of suggested repair: ______________________________________

Please [COLOR=#AA22FF]**do**[/COLOR] not forget to make your UEFI firmware boot on the Ubuntu [COLOR=#666666]22[/COLOR].04.3 LTS entry [COLOR=#666666]([/COLOR]nvme0n1p1/efi/****/grub****.efi [COLOR=#666666]([/COLOR]**** will be updated in the final message[COLOR=#666666])[/COLOR] file[COLOR=#666666])[/COLOR] !
```

---

### Post by oldfred on 2023-08-16
Please use Code Tags for text or terminal output.
Easy to add with Forum's Advanced editor and # icon.
But with Boot-Repair better to just post link as it suggests.

I do not recommend using spaces in any names or labels with Linux.
I converted to using under_score, CamelCase or justalabel.
You have to escape or quote all uses of a space.

It shows you have a second NVMe drive, but not sure if correctly mounted or not.

---

### Post by tea for one on 2023-08-16
```
                                     Avail Use% Mounted on
/dev/nvme0n1p2                      852.7G   2% /
/dev/nvme1n1                          1.7T   0% /mnt/FireCuda 2tb
```
I assume that /dev/nvme1n1 is your backup disk?
Did you create it without a partition?

---

### Post by MAFoElffen on 2023-08-16
Do this booted from a LiveUSB
```

sudo fdisk -l
sudo blkid
sudo sgdisk -p /dev/nvme0n1
sudo sgdisk -p /dev/nvme1n1
lsblk -e7 -o name,label,size,fstype,fsused,UUID,PARTUUID,model

```
I find it curious that /dev/nvme1n1 has no partition identified on it, but is identified as having an ext4 filesystem on it... I don't know that it is mountable, that is why I am asking for more information, that may help with that. I'm thinking if the ext4 filesystem at least has an UUID, that it might possibly be mountable from that(?)

TheFu and I have preached for years never to give an unbound raw disk to something without a partition table as an outer container... I fear that this is what is going on there.

If this was some kind of backup drive, as someone else mentioned, how where you writing to it? Backing up with what?

---

### Post by creature1963 on 2023-08-16
> **tea for one said:**
> ```
                                     Avail Use% Mounted on
/dev/nvme0n1p2                      852.7G   2% /
/dev/nvme1n1                          1.7T   0% /mnt/FireCuda 2tb
```
I assume that /dev/nvme1n1 is your backup disk?
Did you create it without a partition?


Yes it is.

I cannot remember as it was added 2 years ago

---

### Post by creature1963 on 2023-08-16
> **MAFoElffen said:**
> Do this booted from a LiveUSB
```

sudo fdisk -l
sudo blkid
sudo sgdisk -p /dev/nvme0n1
sudo sgdisk -p /dev/nvme1n1
lsblk -e7 -o name,label,size,fstype,fsused,UUID,PARTUUID,model

```
I find it curious that /dev/nvme1n1 has no partition identified on it, but is identified as having an ext4 filesystem on it... I don't know that it is mountable, that is why I am asking for more information, that may help with that. I'm thinking if the ext4 filesystem at least has an UUID, that it might possibly be mountable from that(?)

TheFu and I have preached for years never to give an unbound raw disk to something without a partition table as an outer container... I fear that this is what is going on there.

If this was some kind of backup drive, as someone else mentioned, how where you writing to it? Backing up with what?

Yes it is mounted

See screenshot below using disks, you can see it is mounted

---

### Post by creature1963 on 2023-08-16
that went straight over my head, could you break it done and in simpler wording.

I know I am a pain in the butt, but as this is new to me I want to make sure I do it right.

Many Thanks in Advance

Mr C

---

### Post by oldfred on 2023-08-16
Moving thread to General Help and not System 76 specific.

Issue seems to be a combination of no partition table & space in mount/label.
Each makes it more complicated than it should be and the combination, makes it even more difficult.

---

### Post by Rubi1200 on 2023-08-16
You have a screenshot attached with something from eBay. You may want to edit and remove.

But, a question: when you reinstalled was the backup drive attached at the time?

---

### Post by MAFoElffen on 2023-08-16
> **MAFoElffen said:**
> Do this booted from a LiveUSB
```

sudo fdisk -l [COLOR=#ff0000]## This will show all storage devices, partition tables, the type of those, and partitions[/COLOR]
sudo blkid  [COLOR=#ff0000]## This will try to display the same as baove in a different format or perspective of[/COLOR]
sudo sgdisk -p /dev/nvme0n1 [COLOR=#ff0000]## This will show detailed information as seen through GDisk of your first NVMe[/COLOR]
sudo sgdisk -p /dev/nvme1n1 [COLOR=#ff0000]## This will show detailed information as seen through GDisk of your first NVMe[/COLOR]
lsblk -e7 -o name,label,size,fstype,fsused,UUID,PARTUUID,model [COLOR=#ff0000]## This will show different information, includinh information of how the filesystem may have to be mounted "differently".[/COLOR]

```
<EDITED above with detailed comments on each>

If this was some kind of backup drive, as someone else mentioned, how where you writing to it? Backing up with what?
Your title says: "Had to reinstall and now harddrive says nothing there ??"

I don't care that gnome-disks says it is somehow mounted currently. By that current mount, you say that you can not see anything on that disk, right? I'm asking for detailed information to see if it is possible to mount the filesystem itself, not the whole disk. That is not going to work with your translation of what you see. I need to see the hard data. The output of those commands. If it was given a filesystem with the unbound container given as a whole raw disk, then there is a very slight chance that the filesystem itself can be mounted without referring to a partition, which is not seen there...

This is the only way I know of accessing the data there directly, without having to read the disk bit-by-bit with a disk editor. If you have read the disk bit-by-bit to do that, that would take a whole lot of time and effort...

Is that more of an explanation, or do I need to get even more basic with the explanation?

---

### Post by creature1963 on 2023-08-16
> **oldfred said:**
> Moving thread to General Help and not System 76 specific.

Issue seems to be a combination of no partition table & space in mount/label.
Each makes it more complicated than it should be and the combination, makes it even more difficult.


Many thanks for moving this post into the correct forum room.

I have faith in Ubuntu users/developers and those who just like to fiddle arpound with coding etc....

---

### Post by creature1963 on 2023-08-19
not forgotten just waiting on a 16gb usb stick to aarive as all mine are below 4gb and will not allow to create a usb boot disk

---

### Post by MAFoElffen on 2023-08-19
Thank you for the update. I was wondering what your progress was, and was worried for you.

---

### Post by creature1963 on 2023-08-19
Many thanks for your thoughts

Also been stuck in bed with mysena gravis and depression.

This computer is the only thing I get enjoyment from and makes me happy so sit in front of it weather is building/restoring files from old drives updating my website etc.

Not a game player these days

---

