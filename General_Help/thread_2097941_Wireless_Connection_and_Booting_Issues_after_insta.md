---
title: "Wireless Connection and Booting Issues after installing Ubuntu in Dell Inspiron 14"
date: 2012-12-25
forum: General Help
---

### Post by urielo on 2012-12-25
Hey guys, I've just got a new Dell Inspiron I14-2530p with native Windows 8, and decided to install Ubuntu for a dual boot.

I had to change the bios settings to Legacy instead of UEFI Secure Boot (I don't know very well what that means, but was the only way I found to boot from the CD-ROM). I've used an old live CD I had for Ubuntu 9.10.

The booting went fine, and so did the installation. At the end of it, I clicked the button to restart the computer, but it took too long, and I had to turn it off. After I turned it back on, no GRUB menu was displayed, but I've got that worked out already. Still, no Windows 8 option to boot appears. I wondered if i had the Windows partition formatted, but I can still access all of the Windows files, so the system is there, I just can't reach it.

Also, Ubuntu won't recognize my wireless chip. I try to turn it on via keyboard, but it doesn't work. No networks are available to connect either, even though I could connect to it via Windows.

Now I've managed to upgrade my Ubuntu to 10.04 LTS via wired network. But wireless still won't work, and Windows still won't show up on GRUB's menu.

I've searched around, but no topics seemed to solve the problem for my specific hardware and Windows version.

If anyone has any idea how to solve either issue, I'd be very grateful. I'm starting to freak out on how I screwed my xmas gift up ><

---

### Post by adityamagadi on 2012-12-25
go to your system settings , under the hardware tab u will find additional drivers, click on it and see it your wireless driver is listed and activated.

for solving your windows issue pls post the output of "sudo fdisk -l" by running it in your terminal. hit ctrl+alt+t to fire up  your terminal.

---

### Post by urielo on 2012-12-25
> **adityamagadi said:**
> go to your system settings , under the hardware tab u will find additional drivers, click on it and see it your wireless driver is listed and activated.

for solving your windows issue pls post the output of "sudo fdisk -l" by running it in your terminal. hit ctrl+alt+t to fire up  your terminal.

I went to System -> Administration -> Hardware Drivers (the closest thing I found to system settings o-o), and there were no drivers listed. Is that right?

Here's the output from terminal 

=== fdisk -l ===
WARNING: GPT (GUID Partition Table) detected on '/dev/sda' ! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976762583+  ee  GPT

=======


PS: I'm thinking about upgrading from 10.04 LTS to 12.04 LTS. Would that solve anything, or be good at all?

---

### Post by urielo on 2012-12-25
Hey, I updated from 10.04 LTS to 12.04 LTS and the wireless got back working. But Windows still won't show up on grub =/. I'm guessing by the output of the command above, that grub is not recognizing the partitions within sda.

---

### Post by adityamagadi on 2012-12-25
you are correct there is no other partition on your harddrive... what steps did follow to install ubuntu? did you use wubi installer? or you created the partions yourself?

---

### Post by urielo on 2012-12-25
I used wubi and followed the instructions from the live cd. It's weird because i can access the other partitions from Ubuntu after the startup. I have to find a way to make grub see them too before boot. Does this have anything to do with UEFI? or Windows 8?

---

### Post by adityamagadi on 2012-12-25
no the UEFI issue has been resolved with 12.04. 
as a last try,try this open your terminal and do this : "sudo update-grub".

---

### Post by adityamagadi on 2012-12-25
and did you change back your bios settings to UEFI after installing ubuntu?

---

### Post by urielo on 2012-12-26
> **adityamagadi said:**
> no the UEFI issue has been resolved with 12.04. 
as a last try,try this open your terminal and do this : "sudo update-grub".

I've tried it over and over. This the output of the last time (4s ago):
==========
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-2.6.32-45-generic
Found initrd image: /boot/initrd.img-2.6.32-45-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/50_windows: 1: /etc/grub.d/50_windows: menuentry: not found
insmod: can't read 'part_gpt': No such file or directory
insmod: can't read 'chain': No such file or directory
/etc/grub.d/50_windows: 5: /etc/grub.d/50_windows: chainloader: not found
/etc/grub.d/50_windows: 6: /etc/grub.d/50_windows: Syntax error: "}" unexpected
=====================

before you ask, I followed this tutorial here [http://www.timmeredith.com/tutorials/windows-8-grub.php](http://www.timmeredith.com/tutorials/windows-8-grub.php)
so now i have a file at /etc/grub.d/ named 50_windows with the following code:

```
menuentry "Windows 8" {
	insmod part_gpt
	insmod chain
	set root='(hd0,gpt1)'
	chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
```

it seems that such code is not really good, but if fixed it could insert the option in grub's list

---

### Post by urielo on 2012-12-26
> **adityamagadi said:**
> and did you change back your bios settings to UEFI after installing ubuntu?

no, it's still legacy. should i?

EDIT:
so, i've tried to set it back to UEFI Secured Boot, but i didn't recognize my hard drive, and didn't boot neither Ubuntu nor Windows. Then I changed it to UEFI Unsecured Boot (with Legacy ROM options, as it said) and it showed grub again. But still no Windows options

---

