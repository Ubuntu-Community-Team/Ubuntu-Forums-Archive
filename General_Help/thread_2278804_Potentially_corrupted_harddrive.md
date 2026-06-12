---
title: "Potentially corrupted harddrive"
date: 2015-05-19
forum: General Help
---

### Post by Cythrax on 2015-05-19
Hi

I just tried to install Lubuntu to my wife's Laptop as a dualboot with Windows 7. Since I don't use Windows at all, I didn't know that it was not the best idea to resize the harddisk using gparted. So I resized the disk, then installed Lubuntu. The installation proceeded without any errors and I was able to boot the new Lubuntu. 

Next I checked if Windows was still okay, and it did some kind of diskcheck and reinitialized the harddisk. Windows booted and worked well after that, but Lubuntu doesn't work at all now. I can still boot it, but it gives me loads of permission errors, even if the permissions are fine when I check them. Programs don't run anymore because it tells me that the program is already running, but it is not.

I couldn't solve that, but since it was a fresh install I decided on just install Lubuntu again. But now the harddisk isn't recognized at all. Fdisk -l just lists my usb drive and gparted and the disk utility on the live system don't detect the harddrive. The installer wants to install to /dev/sdb, but shows just empty space there and gives me a fsyncing error. 

I suspect some kind of corrupted file system, but I don't know what to do about it. Is there anything I can do to install Lubuntu without killing the Windows partition? All help would be appreciated very much.

---

### Post by dino99 on 2015-05-19
you did not tell us what kind of installation you made and which settings has been chosen, so the answer cant be precise. Here is one (of the numerous howtos) step by step guide. First  boot from a livedc/usb to know about the partitions & windows (hope you did not let the installer overwriting them), otherwise do nothing but try to undelete with testdisk

[http://www.linuxbsdos.com/2014/05/30/dual-boot-ubuntu-14-04-and-windows-7-on-a-pc-with-uefi-firmware/](http://www.linuxbsdos.com/2014/05/30/dual-boot-ubuntu-14-04-and-windows-7-on-a-pc-with-uefi-firmware/)

---

### Post by Cythrax on 2015-05-19
I tried to install Lubuntu 15.04 on a Sony Vario pcg 61611m, it is a few years old and has a normal Bios, no UEFI. I installed from the live image 15.04-desktop-amd64.iso, which i wrote to usb using unetbootin. During installation I chose 'something else' at partitioning and used the free space to create / with 30 gb, swap with 8 gb and /home with the rest of available space. 

The resized Windows 7 partition was on /sda3 and it had a recovery partition at /sda2. 

I booted from the liveusb and still can't read the harddrive. The Disk utility lists the harddrive not under Disk Drives but as /dev/sdb under other devices. All partitions seem to be there, but they are all listed as partition type and contents 'unknown'. Windows still boots, so at least this partition should be okay. 

The liveusb is now /dev/sda and the hdd is /sdb. I checked with gparted, but there it just says 'error fsyncing/closing /dev/sdb: input/output error'.

---

### Post by ajgreeny on 2015-05-19
See Boot-Repair in my signature and follow the instructions to run that and get the report; do not accept the default repair at this stage but simply post back here the pastebin URL you are shown.

---

### Post by Cythrax on 2015-05-19
I ran the boot repair and it gave me this result: [http://paste.ubuntu.com/11222894/](http://paste.ubuntu.com/11222894/)

---

