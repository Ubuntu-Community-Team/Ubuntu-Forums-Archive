---
title: "Ruined grub on Samsung NP300U1A, is it possible to brick using UEFI on a live usb?"
date: 2013-08-24
forum: General Help
---

### Post by Norvii on 2013-08-24
[FONT=arial]First of all, I am not using Wubi and I obviously have installed Ubuntu on my system before. For those who may not know, there has been a problem with some Samsung laptop models hardbricking, resulting in an unusable motherboard after an attempt to install a new OS or run a live cd/usb through the BIOS using UEFI. My model is from July 2011, and runs (or did) Windows 7, not Windows 8. I did find one person who claimed to have had it happen to his new laptop which did run Windows 7, however. So essentially, I am asking, can this still happen to my system even though I've already installed Ubuntu using a bootable USB flash drive? It's caused by Samsung's drivers, but I have not been able to find anything relevant for my model on their site.

I cannot boot into anything after making changes in my Windows partition on my harddrive, as it appears grub has been ruined. I boot into the error: unknown filesystem with grub rescue. I can ls and thus find some info on my paritions. Doing so renders the result as this: (hd0)  (hd0,msdos7)  (hd0,msdos6)  (hd0,msdos5)  (hd0,msdos3)  (hd0,msdos2)  (hd0,msdos1)

I have tried a few things such as

ls
ls (hd0,msdos6)/
set root=(hd0,msdos6)
ls /
set prefix=(hd0,msdos6)/boot/grub
insmod /boot/grub/linux.[mod]("http://askubuntu.com/questions/119597/grub-rescue-error-unknown-filesystem#")
normal

but this has been without luck, as I only receive errors regardless what I attempt. I am afraid booting a live usb may ruin my motherboard, but I am not sure if there are any other options at this point... I really hope someone can help me a bit with this.[/FONT]

---

### Post by VMC on 2013-08-24
If you can boot from a livecd, I doubt you have bricked your computer.
So you get the grub "grub>" prompt.
Will you download and run bootinfoscript(see my blue link), then output the results back here between [code] tags. thanks.

---

### Post by oldfred on 2013-08-24
+1 on Boot-Repair. It may also fix your issues, but post link to Bootinfo report.

The bricking related to UEFI booting and not ever being able to get back into UEFI/BIOS to choose what to boot or boot a repair flash drive or DVD.
It turned out to also be an issue with Windows, so it does not matter what operating system. Fixes were released fot some of the worst cases to work around errors in the UEFI design.

---

### Post by Norvii on 2013-08-25
Since yesterday I have pulled the hdd from the laptop computer and transferred it temporarily to a stationary computer. I have made a live usb of Ubuntu and am running this at the moment. I am attempting to reinstall grub through the terminal, and this is what happens when I attempt to mount hdd with the partition containing Ubuntu,

sudo mount -t ext3 /dev/sda2 /mnt

But I am met with this error...

bash: /dev/sdb6: Permission denied

As I am running live Ubuntu on usb ( I am borrowing the computer I am using for this) I am not quite certain at this point what action should be taken. How do I use sudo on live usb then? What else can I do?

---

### Post by oldfred on 2013-08-25
I would still suggest Boot-Repair but not to run an auto repair. Uncheck auto repair, check fix MBR and in advance choose which install to put into which MBR. You want to be sure to install grub2's boot loader to MBR of same drive as Ubuntu install.

Post this:
sudo fdisk -lu

---

