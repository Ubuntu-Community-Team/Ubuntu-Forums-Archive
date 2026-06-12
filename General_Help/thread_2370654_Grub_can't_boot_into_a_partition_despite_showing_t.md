---
title: "Grub can't boot into a partition despite showing the option in the boot menu"
date: 2017-09-06
forum: General Help
---

### Post by warrengbrn on 2017-09-06
I'm trying to boot into the Windows Boot Manager from GRUB but when I do so it now randomly fails even though it used to work in the past and shows the messages:

error: no such device: AA86-3CF5
error: disk 'hd1,gpt2' not found.

I found a command "sudo blkid" that shows the UUID of all of my partitions on my solid state drives and the device and partition listed above definitely seem to exist since it shows up in the terminal, GRUB detects it, and I'm able to boot to it from my motherboard's BIOS. I've already updated GRUB and reinstalled it completely. Does anyone know if there's anything else I could try? I dual boot both Ubuntu and Windows 10 but I just cannot boot into Windows 10 from GRUB despite the option appearing.

---

### Post by deadflowr on 2017-09-06
Run Boot-info and post the paste link that it gives you.
Boot-info: [https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")

---

### Post by warrengbrn on 2017-09-06
I wasn't able to generate a paste link showing any information for some reason but I was able to generate a text file locally and submit a link myself.

Here it is: [https://paste2.org/BC2jsOWH](https://paste2.org/BC2jsOWH)

Thanks for the quick reply yesterday.

---

### Post by oldfred on 2017-09-06
UUIDs seem to match, and GUIDs which UEFI uses seems to match.

But grub only boots working Windows? That means Windows fast start up or always on hibernation must be off. Windows on updates will turn that back on and those updates may be in the back ground so you do not even know.

Check that fast start up is off.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by LostFarmer on 2017-09-06
> it now randomly fails when it fails do  you have an usb external hdd/stick plugged in , and when it works the usb hdd is removed ?

---

### Post by warrengbrn on 2017-09-06
I can boot into Ubuntu but not windows 10(aka windows boot manager) if I'm booting from GRUB. I also tried turning off fast startup as well earlier and it made no difference. Funny how its on because I do recall turning that feature off months ago.

---

### Post by warrengbrn on 2017-09-06
> **LostFarmer said:**
> when it fails do  you have an usb external hdd/stick plugged in , and when it works the usb hdd is removed ?

EDIT: Nevermind the issue came back and now its stating:

error: no such device: AA86-3CF5
error: file `/efi/Microsoft/Boot/bootmgfw.efi' not found.

The only thing I changed was generating a text file report of my system. Didn't even use Boot Repair to try and fix any issues, only generated the report. I'll try using Boot Repair.
Removing my usb stick with a live cd install of ubuntu doesn't seem to make any difference. I have no external storage devices plugged in except for the usb stick I used to install ubuntu.

---

### Post by oldfred on 2017-09-07
You can try this or chkdsk from Windows.
 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted run on both sda1 & sdc2, as sdc2 is the one it is complaining about.
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[URL="https://bbs.archlinux.org/viewtopic.php?id=164185"]https://bbs.archlinux.org/viewtopic.php?id=164185
[/URL] See also
man dosfsck

Can you directly boot Windows from UEFI boot menu, often f10 or f12 check manual?

---

