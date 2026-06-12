---
title: "Hello there need help to recover the booting of Ubuntu on a multi-boot with Deepin."
date: 2024-10-24
forum: General Help
---

### Post by laodan2 on 2024-10-24
I upgraded my Ubuntu 22.04.3 OS to Ubuntu 24.04.1, in the first days of September, in a multi-boot with Mint on 2 different partitions of a SSD. When starting the system Ubuntu was booting successfully but Mint was no longer visible on the boot menu. Failing to recover my Mint booting I decided to install Deepin 23 on the Mint partition. When starting the system both Ubuntu and Deepin were booting flawlessly ... until yesterday October 23rd !

The boot menu gives the choice between Deepin as primary partition and Ubuntu as secondary. Deepin continues to boot flawlessly but when I click on Ubuntu, for booting, the menu disappears with no further action. I'm then forced to push the power button to restart the computer...  



COMPUTER SYSTEM

Lenovo Yoga 27. 32 Gb Ram. 
CPU : AMD Rysen 7 4800H with Radeon graphics
          Core 16

DISKS
Partitions of SSD nvmeOn1:
-- nvmeOn1p1 (230 Gb) : Ubuntu 24.04. 
-- nvmeOn1p2 (240 Gb) : Deepin 23. 
-- nvmeOn1p4 (1 Gb): efi boot partition
SDA1 : storage.

Deepin 23 Primary OS
Kernel 6.6.47-amd64-desktop-hwe

Ubuntu 24.04 secondary OS
Kernel 6.8.45-amd64-desktop-hwe



BOOT REPAIR

I launched my boot-repair stick and clicked the "advanced options" to order Deepin as my default OS and clicked "reinstall Grub", "use the standard EFI file", "uncomment GRUB_GFXMODE", and "Create a BOOTINFO summary". The MBR options were empty.

After reboot Deepin was still working flalessly but Ubuntu was still actionless.

The "INFO summary" is available at the following Pastebin address : [https://paste.ubuntu.com/p/HT3vssrrPX/](https://paste.ubuntu.com/p/HT3vssrrPX/)

Thanks for helping.

---

### Post by yancek on 2024-10-24
>  When starting the system both Ubuntu and Deepin were booting flawlessly ... until yesterday October 23rd !

Which begs the question, what happened yesterday.  Any changes made?  If so, what were they?

Beginning at line 24 of boot repair, you see the contents of the EFI partition which show the correct directory and contents for both ubuntu and deepin.  The only unusual thing about this is that the EFI partition is partition 4 when it is usually the first or second partition but that should not have any effect.  If you have Grub installed and booting Deepin correctly, reinstalling Grub again isn't going to help as it is already installed.

If you go into the BIOS boot options and select Boot0001* (the ubuntu option) as first boot, does ubuntu boot?  Boot repair no longer posts the contents of the /boot/grub/grub.cfg file so could you post the first Ubuntu menuentry from that file from the Deeping /boot/grub/grub.cfg file.

---

### Post by laodan2 on 2024-10-24
Thanks for the reply Yancek,

See Deepin files :
- boot/grub/grub.cfg at [https://drive.google.com/file/d/17vHoORfLFyPPMk0fBkgGnoYE068_ZjZT/view?usp=drive_link](https://drive.google.com/file/d/17vHoORfLFyPPMk0fBkgGnoYE068_ZjZT/view?usp=drive_link)
- etc/default/grub-d/10_deepin.cfg at [https://drive.google.com/file/d/1x2V6HYuNoNh6z1fWAx5ql1aiht-JFurT/view?usp=drive_link](https://drive.google.com/file/d/1x2V6HYuNoNh6z1fWAx5ql1aiht-JFurT/view?usp=drive_link)

I changed the BIOS boot options, booted but same as before.

---

### Post by yancek on 2024-10-24
I'm not going to google drive so either wait for someone else to respond or post it here.  Just the entry from the Deepin grub.cfg for Ubuntu, not the entire file.

If you selected to boot Ubuntu from the BIOS boot options and it failed, the problem is with the Ubuntu boot files and they need to be correct or you need to reinstall Grub from Ubuntu which will be problematic if you can't boot it.  You could use the chroot method from Deepin or a 'live' usb as described at the link below under Fixing a broken system.

[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing


[/URL]

---

### Post by dragonfly41 on 2024-10-24
What do you see when running:

```
efibootmgr
```

---

### Post by laodan2 on 2024-10-24
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 24.04.1 LTS (24.04) (on /dev/nvme0n1p1)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-58075cbb-fb13-4a20-a9db-4acf28a5404f' {
    insmod part_gpt
    insmod ext2
    search --no-floppy --fs-uuid --set=root 58075cbb-fb13-4a20-a9db-4acf28a5404f
    linux /boot/vmlinuz-6.8.0-47-generic root=UUID=58075cbb-fb13-4a20-a9db-4acf28a5404f ro quiet splash $vt_handoff
    initrd /boot/initrd.img-6.8.0-47-generic
}
submenu 'Advanced options for Ubuntu 24.04.1 LTS (24.04) (on /dev/nvme0n1p1)' $menuentry_id_option 'osprober-gnulinux-advanced-58075cbb-fb13-4a20-a9db-4acf28a5404f' {
    menuentry 'Ubuntu (on /dev/nvme0n1p1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-6.8.0-47-generic--58075cbb-fb13-4a20-a9db-4acf28a5404f' {
        insmod part_gpt
        insmod ext2
        search --no-floppy --fs-uuid --set=root 58075cbb-fb13-4a20-a9db-4acf28a5404f
        linux /boot/vmlinuz-6.8.0-47-generic root=UUID=58075cbb-fb13-4a20-a9db-4acf28a5404f ro quiet splash $vt_handoff
        initrd /boot/initrd.img-6.8.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 6.8.0-47-generic (on /dev/nvme0n1p1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-6.8.0-47-generic--58075cbb-fb13-4a20-a9db-4acf28a5404f' {
        insmod part_gpt
        insmod ext2
        search --no-floppy --fs-uuid --set=root 58075cbb-fb13-4a20-a9db-4acf28a5404f
        linux /boot/vmlinuz-6.8.0-47-generic root=UUID=58075cbb-fb13-4a20-a9db-4acf28a5404f ro quiet splash $vt_handoff
        initrd /boot/initrd.img-6.8.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 6.8.0-47-generic (recovery mode) (on /dev/nvme0n1p1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-6.8.0-47-generic-root=UUID=58075cbb-fb13-4a20-a9db-4acf28a5404f ro recovery nomodeset dis_ucode_ldr-58075cbb-fb13-4a20-a9db-4acf28a5404f' {
        insmod part_gpt
        insmod ext2
        search --no-floppy --fs-uuid --set=root 58075cbb-fb13-4a20-a9db-4acf28a5404f
        linux /boot/vmlinuz-6.8.0-47-generic root=UUID=58075cbb-fb13-4a20-a9db-4acf28a5404f ro recovery nomodeset dis_ucode_ldr
        initrd /boot/initrd.img-6.8.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 6.8.0-45-generic (on /dev/nvme0n1p1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-6.8.0-45-generic--58075cbb-fb13-4a20-a9db-4acf28a5404f' {
        insmod part_gpt
        insmod ext2
        search --no-floppy --fs-uuid --set=root 58075cbb-fb13-4a20-a9db-4acf28a5404f
        linux /boot/vmlinuz-6.8.0-45-generic root=UUID=58075cbb-fb13-4a20-a9db-4acf28a5404f ro quiet splash $vt_handoff
        initrd /boot/initrd.img-6.8.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 6.8.0-45-generic (recovery mode) (on /dev/nvme0n1p1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-6.8.0-45-generic-root=UUID=58075cbb-fb13-4a20-a9db-4acf28a5404f ro recovery nomodeset dis_ucode_ldr-58075cbb-fb13-4a20-a9db-4acf28a5404f' {
        insmod part_gpt
        insmod ext2
        search --no-floppy --fs-uuid --set=root 58075cbb-fb13-4a20-a9db-4acf28a5404f
        linux /boot/vmlinuz-6.8.0-45-generic root=UUID=58075cbb-fb13-4a20-a9db-4acf28a5404f ro recovery nomodeset dis_ucode_ldr
        initrd /boot/initrd.img-6.8.0-45-generic
    }
    menuentry 'Memory test (memtest86+x64.efi) (on /dev/nvme0n1p1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+x64.efi--58075cbb-fb13-4a20-a9db-4acf28a5404f' {
        insmod part_gpt
        insmod ext2
        search --no-floppy --fs-uuid --set=root 58075cbb-fb13-4a20-a9db-4acf28a5404f
        linux /boot/memtest86+x64.efi 
    }
    menuentry 'Memory test (memtest86+x64.efi, serial console) (on /dev/nvme0n1p1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+x64.efi--58075cbb-fb13-4a20-a9db-4acf28a5404f' {
        insmod part_gpt
        insmod ext2
        search --no-floppy --fs-uuid --set=root 58075cbb-fb13-4a20-a9db-4acf28a5404f
        linux /boot/memtest86+x64.efi console=ttyS0,115200
    }
}
```

---

### Post by laodan2 on 2024-10-24
$ efibootmgr
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0001,0019,0017,001A,0016,0018,001B
Boot0000* deepin
Boot0001* Ubuntu
Boot0010  Enter Setup
Boot0011  Boot Menu Primary
Boot0012  Startup Interrupt Menu
Boot0013  Lenovo Diagnostics
Boot0014  Rescue and Recovery
Boot0015  Rescue and Recovery
Boot0016* USB HDD:
Boot0017* M.2 Drive 1:
Boot0018* M.2 Drive 2:
Boot0019* SATA 1:
Boot001A* Network1:
Boot001B* USB CDROM:

---

### Post by laodan2 on 2024-10-24
etc/default/grub-d/10_deepin.cfg


GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT DEEPIN_GFXMODE=\$DEEPIN_GFXMODE"

---

### Post by dragonfly41 on 2024-10-25
Since efibootmgr works I would now try installing rEFInd as a parallel boot manager. Then in BIOS or using efibootmgr set rEFInd as default boot manager. It will show a GUI on bootup rather than usual grub list.  See if rEFInd can launch Deepin. It does not touch your normal grub. Just acts as a buddy.

---

