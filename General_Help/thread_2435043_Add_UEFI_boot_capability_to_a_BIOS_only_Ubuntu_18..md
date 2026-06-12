---
title: "Add UEFI boot capability to a BIOS only Ubuntu 18.04 based custom iso"
date: 2020-01-15
forum: General Help
---

### Post by lhh29936 on 2020-01-15
I am trying to add UEFI boot capability to a BIOS only Ubuntu 18.04 based custom iso. All the methods I've found so far require an efi.img file which isn't present in the custom iso so I pulled it from the base 18.04 iso. Can I use the file out of a full install Ubuntu 18.04? If yes, do I need to edit it?

The custom iso is designed to run from a USB, not installed. It is also intended for distribution to new Linux users. Adding UEFI capabilities to the USB rather than the iso isn't the solution we're looking.

This is the script that I used to build the fat partition. It is run in the folder containing the extracted iso:
```
 #!/bin/bash
    BOOT_IMG_DATA="$PWD"
    BOOT_IMG=efi.img
    
    #Ensure needed folders exist
    
    if [ ! -d "$PWD"/efi/boot ]; then
      mkdir -p "$PWD"/efi/boot
      chown larry:larry "$PWD"/efi -R
    fi
    
    if [ ! -d "$PWD"/boot/grub ]; then
      mkdir -p "$PWD"/boot/grub
      chown larry:larry "$PWD"/boot -R
    fi
 
    chmod -R +rw "$PWD"/boot/grub
    chmod -R +rw "$PWD"/efi/boot
    
    # Create the 64-bit EFI GRUB binary (bootx64.efi) and the El-Torito boot
    # image (efiboot.img) that goes in the /isolinux directory for booting on
    # UEFI systems.
    
    # First, build bootx64.efi, which will be installed here in /EFI/BOOT:
    
    grub-mkimage --format=x86_64-efi --output=bootx64.efi --config=grub.cfg --compression=xz --prefix=/EFI/BOOT part_gpt part_msdos fat ext2 hfs hfsplus iso9660 udf ufs1 ufs2 zfs chain linux boot appleldr ahci configfile normal regexp minicmd reboot halt search search_fs_file search_fs_uuid search_label gfxterm gfxmenu efi_gop efi_uga all_video loadbios gzio echo true probe loadenv bitmap_scale font cat help ls png jpeg tga test at_keyboard usb_keyboard
    
    # Then, create a FAT formatted image that contains bootx64.efi in the
    # /EFI/BOOT directory.  This is used to bootstrap GRUB from the ISO image.
    dd if=/dev/zero of=efiboot.img bs=1K count=1440
    
    # Format the image as FAT12:
    mkdosfs -F 12 efiboot.img
    
    # Create a temporary mount point:
    MOUNTPOINT=$(mktemp -d)
    
    # Mount the image there:
    mount -o loop efiboot.img $MOUNTPOINT
    
    # Copy the GRUB binary to /EFI/BOOT:
    mkdir -p $MOUNTPOINT/EFI/BOOT
    cp -a bootx64.efi -s $MOUNTPOINT/EFI/BOOT
    
    
    # Unmount and clean up:
    umount $MOUNTPOINT
    rmdir $MOUNTPOINT
    
    # Move the efiboot.img to isolinux:
    mv efiboot.img isolinux
    mv bootx64.efi efi/boot



```
This is the script I use to build the iso:


```
    #!/bin/bash
    
    # The example names get mapped to their roles here
    orig_iso="$HOME"/foxclone/foxclone025-01.iso
    new_iso="$HOME"/foxclone/foxclone025-02.iso
    new_files="$PWD"
    mbr_template=/usr/lib/ISOLINUX/isohdpfx.bin
    
    
    # Extract MBR template file to disk
    dd if="$orig_iso" bs=1 count=432 of="$mbr_template"
    
    
    # Create the new ISO image
    xorriso -as mkisofs \
       -U  \
       -allow-lowercase  \
       -r -V 'foxclone025-02' \
       -o "$new_iso" \
       -J -J -joliet-long \
       -isohybrid-mbr "$mbr_template" \
       -c isolinux/boot.cat \
       -b isolinux/isolinux.bin \
        -no-emul-boot -boot-load-size 4 -boot-info-table \
       -eltorito-alt-boot \
       -e isolinux/efiboot.img \
        -no-emul-boot \
        -isohybrid-gpt-basdat \
       "$new_files"

```



Contents of boot/grub and EFI/BOOT follows


```
    larry@larry-Satellite-C55-A:~/foxclone/iso3$ ls -l boot/grub
    total 2492
    -rw------- 1 larry larry 2523136 Jul 31 01:33 efi.img
    -rw------- 1 larry larry    5004 Mar 18  2019 font.pf2
    -rw------- 1 larry larry     941 Aug  5 15:28 grub.cfg
    -rw------- 1 larry larry     604 Aug  5 15:28 loopback.cfg
    drwxr-xr-x 2 larry larry   12288 Jan 13 09:20 x86_64-efi
    
    larry@larry-Satellite-C55-A:~/foxclone/iso3$ ls -l EFI/BOOT
    total 2424
    -rw------- 1 larry larry 1334816 Aug  5 15:28 BOOTx64.EFI
    -rw------- 1 larry larry 1146744 Aug  5 15:28 grubx64.efi

```

Contents of grub.cfg


```
    if loadfont /boot/grub/font.pf2 ; then
        set gfxmode=auto
        insmod efi_gop
        insmod efi_uga
        insmod gfxterm
        terminal_output gfxterm
    fi
    
    set menu_color_normal=white/black
    set menu_color_highlight=black/light-gray
    
    set timeout=5
    menuentry "Foxclone" {
        set gfxpayload=keep
        linux    /casper/vmlinuz  boot=casper quiet splash ---
        initrd    /casper/initrd
    }


```

When I mount the EFI partition of the iso, the folders are created but they are empty. 

Does anyone see a problem in the code? I really appreciate a different set of eyes looking at this as I think I've gotten "too close to the forest to see the trees".

Sorry if I posted in the wrong area.
TIA, Larry

---

### Post by oldfred on 2020-01-15
When you install grub, it also needs a grub.cfg
Ubuntu's shimx64.efi or grubx64.efi from a full install, seem to be hard coded to only find /EFI/ubuntu/grub.cfg.
But installer or just any install of grub to a drive just needs a grub.cfg.

I have installed grub to flash drives & then created grub entries to loopmount my ISO on the flash drive. This was to make my own repalr flash drive with multiple ISO. It used to be that grub install did not create /EFI/Boot and you needed the --removable parameter. Not sure with grub updates exactly how it now works.

Two versions that worked for me.
sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/media/test --removable
mounted the USB EFI partition at /media/test and I installed grub with
sudo grub-install --target=x86_64-efi --efi-directory=/media/test --bootloader-id=grub --removable --recheck --debug


sudo mount -t vfat /dev/sdb1 /mnt -o uid=1000,gid=1000,umask=022
sudo grub-install --removable --boot-directory=/mnt/boot --efi-directory=/mnt/EFI/BOOT /dev/sdb

grub.cfg in efi partition where a602..... is UUID of my main grub.cfg. 
search.fs_uuid a60289d6-c308-44f1-9ce6-85db3482ff32 root hd0,gpt1  
set prefix=($root)/boot/grub
configfile $prefix/grub.cfg

---

### Post by dragonfly41 on 2020-01-15
This UEFI world is still all a mystery to me. But intuitively, from what I have read in searching around, [CUBIC]("https://www.techrepublic.com/article/how-to-create-a-custom-ubuntu-iso-with-cubic/") can be used to create a custom UEFI Live USB.

---

### Post by lhh29936 on 2020-01-15
oldfred, thanks for the reply. I've got it booting from the USB now but it's dumping me to a GNU GRUB 2.02 grub> prompt. I assume that the problem is with my [COLOR=#000000]/EFI/ubuntu/grub.cfg. The iso name is Foxclone025-02.iso but was built on a minimal version of Ubuntu 18.04 desktop. Here's my grub.cfg

[/COLOR]

```
if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


set timeout=5
menuentry "ubuntu" {
        set root=(hd0)
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}

```

Thanks again for your help

EDIT: I've double checked, the files in /casper are correct.

---

### Post by oldfred on 2020-01-15
The default file names have changed with various version. Some have .efi others do not, etc.

This from 20.04 ISO. But this grub is in /boot/grub/grub.cfg. But most of the other files & folders with grub support files are also needed.

> menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed quiet splash ---
    initrd    /casper/initrd
}



I almost always have to look at the ISO to know exact details of grub.cfg. Path, file names & other details.

---

### Post by lhh29936 on 2020-01-15
@oldfred - Still ending up at a grub> prompt, even after copying the grub.cfg file and preseed folder from the original Ubuntu 18.04, Removed "quiet splash" from grub,cfg. but getting no output. Any ideas?

---

### Post by oldfred on 2020-01-15
At grub can you do ls, the ls (0,1)/ and then ls (0,1)/boot/ etc  to find kernel and rest of system?

---

### Post by lhh29936 on 2020-01-15
I think I found the problem. My /isolinux/efiboot.img has efi and efi/boot folders but they are empty. Now to figure out why.

---

### Post by wildmanne39 on 2020-03-16
*Thread moved to **General Help a more appropriate sub-forum*** since it is not a tutorial.

---

### Post by C.S.Cameron on 2020-03-17
Creating a Full Install of Ubuntu 20.04 to USB
--------------------------------------------------

I have been working on a step by step guide for creating a BIOS/UEFI compatible Ubuntu 20.04 Full install USB drive.
Perhaps there might be something here that is of value to you. See **bold** text
Following is based on a 16GB Target drive, adjust for larger drive.

- Create a Live USB or DVD using SDC, UNetbootin, mkusb, dd, etc. (See Note 1 at bottom)
- Turn off and unplug the computer.
- Unplug the power cable from the hard drive or unplug the hard drive from the laptop. (See Note 2 at bottom)
- Plug the computer back in.
- Insert and boot the Live USB or Live DVD.
- Select Language and Try Ubuntu.
- Insert the target flash drive.

[B]- Start GParted.
- Unmount any mounted partitions.
- Select Device tab and create a GPT partition table on the Target drive.
- Create a 3GB NTFS or FAT32 partition on the right side, (optional Linux / Windows data partition, See Note 3 at bottom).
- Create a 1MB partition on the left side, format as unformatted.
- Create a 300MB FAT32 partition next to the 1MB partition.
- Create a 7GB ext partition next to the 300MB partition.
- In the remaining space create an ext4 partition, (optional for /home partition).
- Apply All Operations.
- Flag the 1MB partition as bios_grub.
- Flag the 300MB partition as boot,esp.[/B]


- Start Install Ubuntu.
- Select Language, click "Continue".
- Select Keyboard layout, click "Continue".
- Select Wireless network, click "Continue". (optional)
- Select installation preference and select "Download updates while installing Ubuntu", (optional), and Select "Install third-party software ...", (optional).Click "Continue".
- 
- If asked about mounted partitions, select Yes, click "Continue".
- Do not use Advanced feature disk encryption for this install method. (See Note 3 at bottom)
- At "Installation type" select "Something else", click "Continue"
- Under Device for boot loader installation select the target drive.
- Select partition sdx4 and click change, select use as Ext4, select format this partition, and Mount point = "/" then OK.
- If asked to Write previous changes... select Continue.
- Select partition sdx5 and click change, select use as Ext4, select format this partition, and Mount point = "/home" then OK. (optional).
- Click Install now.


- Confirm partitions to be formatted.
- Select your location. click	 "Continue"
- Insert your name, computer name, username, password and select if you want to log in automatically or require a password.
- Wait until install is complete.


[B]- Copy the boot and the EFI folders from the Live USB cdrom folder to the boot,esp partition sdx3
- Copy grub.cfg from partition sdx4 /boot/grub/ to partition sdx3 /boot/grub/.

- Re-Install grub

    ```
sudo mount /dev/sdx3 /mnt
```
    ```
sudo grub-install --boot-directory=/mnt/boot /dev/sdx
```[/B]

- Turn off computer and plug in the HDD.
- Replace the computer's cover.

Note 1, Booting ISO Files

If you want the USB to have the ability to boot ISO files using grub create the boot drive using mkusb with the usb-pack-efi option. (this replaces grub 2.04 with 2.02). 


Note 2: Hard drive removal.

You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the USB drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR as default location for boot loader is sda, any items in the internal drive's grub will be added to the USB's grub. You may do an update-grub later.


Note 3: If you own an Apple computer make this partition FAT32.


Note 4: Encryption (optional).

- For method of creating Full Encryption BIOS/UEFI USB drive see: [https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption)

---

