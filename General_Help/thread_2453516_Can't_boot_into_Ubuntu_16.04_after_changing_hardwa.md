---
title: "Can't boot into Ubuntu 16.04 after changing hardware (motherboard/cpu)"
date: 2020-11-12
forum: General Help
---

### Post by colin162 on 2020-11-12
Dear All
Hope somebody can help.
Yesterday my keyboard hung and when I tried to reboot it kept saying I need to Update BIOS.
After a few hours of trying I could not get it to boot again and assumed it must be a problem with the motherboard and so bought a second hand HP. I was hoping I could just transfer my old Samsung SSD (with Ubuntu 16.04LTS) to the newly purchased comp and start up normally.
I was under the impression that the hardware is detected while installing.

Anyway, it wouldn't boot. Fiddled about with UEFI and LEGACY settings in BIOS but still would not boot.
I then used a USB to boot into 16.04LTS and managed. So from there I copied the system to another SSD (Goodram), that came with the HP, and tried booting from that, which worked.

I tried comparing the /boot folder and copied the /boot of the (Goodram) SSD (that booted ok) to my old Samsung SSD, but it still did not boot. All I'm getting is a black screen with the cursor flashing in the top left corner.

I'm attaching what the partitions look like on both SSDs. plus fdisk -l

colin@colin-HP-Compaq-Elite-8300-SFF:~$ sudo fdisk -l

Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 7E457AA2-06ED-4528-9EBC-5411B43A0377

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 471881727 470831104 224.5G Linux filesystem
/dev/sda3  471881728 488396799  16515072   7.9G Linux swap


Disk /dev/sdb: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x72ee7fbe

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *           63 498095324 498095262 237.5G 83 Linux
/dev/sdb2       498095325 500103449   2008125 980.5M  5 Extended
/dev/sdb5       498095388 500103449   2008062 980.5M 82 Linux swap / Solaris

Any help much appreciated.
Thanks

---

### Post by Impavidus on 2020-11-12
One of the SSDs (the Samsung) uses GPT partitioning and has an EFI partition, suggesting it was partitioned for an UEFI install. The other uses MBR partitioning and has no EFI partition, which means it must be used for a legacy install. Those are not compatible. Make sure the new computer is set to the same mode as the old and it may work. But maybe not, if there are proprietary drivers involved.

16.04 only has 5 months of life left, so don't invest too much time in it.

---

### Post by colin162 on 2020-11-12
I tried messing about with the Bios settings and UEFI but still no luck.

I also tried to repair grub using this method [https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)
and got this error
[URL="http://paste.ubuntu.com/p/PRCwk45Fwk/"]

[http://paste.ubuntu.com/p/34xcVKG3Fx/](http://paste.ubuntu.com/p/34xcVKG3Fx/)


[/URL]

---

### Post by colin162 on 2020-11-12
I installed Ubuntu along side my current Ubuntu and can chose which one to log into, and although I'm getting an error:
[I]
error: file '/boot/vmlinuz-4.15.0.45-generic' not found
alloc magic is broken at 0xc59723cO: c58b57eo
Aborted. Press any key to exit
[/I]
I'm managing to log in now but my keyboard only works till I have entered the password then nothing. The mouse keeps working normally.

---

### Post by ActionParsnip on 2020-11-12
If you boot a live USB / CD of Focal (Ubuntu 20.04), is it OK? You have to remember that 16.04 is 4.5 years old. The newer version of Ubuntu with much much newer packages will help a lot

---

### Post by colin162 on 2020-11-12
Managed to solve the keyboard issue too after following this link
[https://techwiser.com/fix-keyboard-not-working-in-ubuntu-18-04/](https://techwiser.com/fix-keyboard-not-working-in-ubuntu-18-04/)

So all good now :)
Thanks

---

