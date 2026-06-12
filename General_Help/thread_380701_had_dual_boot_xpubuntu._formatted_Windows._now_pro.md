---
title: "had dual boot xp/ubuntu. formatted Windows. now problem"
date: 2007-03-10
forum: General Help
---

### Post by element0 on 2007-03-10
Hi all.
I had dual boot with Ubuntu 6.10 and Windows XP previously. I had to format my XP Drive (C) because of a hardware issue (long story). I reinstalled XP on the same patition and everything is okay with my Windows (had to replace my videocard though). 
Since i formated windows, i dont get the option to boot into ubuntu. Also i desperately needed to get some data off of the ubuntu partition, so i booted using the live cd and mounted the ubuntu partition (sda7) onto my External Drive and copied that stuff onto my usb stick. 
My question is that if it is possible to restore my existing ubuntu partition and get the GRUB loader to come up during bootup and if so, how would i go about doing that.
Thanks in advance

---

### Post by rsambuca on 2007-03-10
Just open a terminal from the live CD and enter ```
sudo grub-install
```

---

### Post by element0 on 2007-03-11
Thanks for the very quick reply, I tired that and im getting:
```
ubuntu@ubuntu:~$ sudo grub-install
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

```
and i cant seem to understand which option to use and which device filename (sda1 i think). I tried it without the option (and sda1 as the device_filename)and it didnt do anything, gave me
```
Format of install_device not recognized.
```
followed by that same long message. What do you guys suggest I do?

---

