---
title: "Grub repair on encrypted disk"
date: 2016-01-29
forum: General Help
---

### Post by iclestu on 2016-01-29
[COLOR=#111111][FONT=Ubuntu]Hi,

I wonder if anyone can help...

I previously had Kubutu (14.04 i think) installed with an cryptoLuks encrypted hard disk. I have been trying to install 15.04 on the same drive. The install went ok with no errors but I wasn't able to boot afterwards - instead I reached the (initramfs) prompt with this message:
[/FONT][/COLOR]
[FONT=courier new]ALERT! /dev/mapper/kubuntu--vg-root does not exist. Dropping to a shell![/FONT]
[COLOR=#111111][FONT=Ubuntu]
indeed it does not exist. ls /dev/mapper lists only one file named 'control'
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So, after a bit of Googling, I found myself using the live cd to try to repair grub but to no avail. I tried first with the default settings and then using the advanced options to point it at my boot partition but I am back at (initramfs) prompt and no further forward.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I feel like there are options in the grub-repair tool to cover this scenario but my lack of knowledge is preventing me finding them?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I don't need any dual-boot. This is the only OS on that machine.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Boot repair paste-bin is here: [http://paste.ubuntu.com/14694855/](http://paste.ubuntu.com/14694855/)

Is anyone able to help? I'd be very grateful.

(Disclosure - I also posted this [here]("http://askubuntu.com/questions/727105/grub-repair-for-encrypted-disk") on ask ubuntu - I hope such cross posting is acceptable.. )

[/FONT][/COLOR]

---

### Post by Nuno_Abreu on 2016-01-29
To boot to encrypted OS, you need to have the /boot directory in a different partition because the BIOS can't decrypt LUKS encryption natively (exception: Libreboot BIOS).

Please get into a live CD. To my understanding, you have the /boot directory in /dev/sda1. Please consider mounting and keep in mind its mountpoint in <dir1>. Also, decrypt the OS and mount it - type its mountpoint in <dir2> in the code below. So, go to a Terminal:

```
sudo grub-install --boot-directory=<dir1> --root-directory=<dir2> /dev/sda
```

Try to boot now. If this does not work, remove the root directory option in the grub-install command:
```
sudo grub-install --boot-directory=<dir1> /dev/sda
```
Tell me the results, please.

---

### Post by oldfred on 2016-01-29
If you reinstalled, it probably would be better to remove the LVM.
I consider LVM to be advanced partitioning. It requires its own tools to manage the LVM partitions.

If you want to keep the LVM, this thread on resizing goes thru the process of mounting the LVM partitions. Just run repairs after mounting, not the resize steps afterwards.
       How to: Mount & Resize an Encrypted Partition (LUKS) also mount
[URL="http://ubuntuforums.org/showthread.php?p=4530641"]http://ubuntuforums.org/showthread.php?p=4530641
      [/URL]
 [URL="http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i"]http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i
[/URL]
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)[URL="http://ubuntuforums.org/showthread.php?p=4530641"]
[/URL]

---

### Post by iclestu on 2016-01-29
Hi,

Thank you for taking the time to respond - I appreciate your help

Trying Nunu_Abreu's suggestion first I did ```
lsblk
``` and got this:

```
NAME       MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda          8:0    0 931.5G  0 disk  
&#9500;&#9472;sda1       8:1    0   243M  0 part  /media/kubuntu/d9e47709-9e1a-4795-8b61-d50ef9edf06
&#9500;&#9472;sda2       8:2    0     1K  0 part  
&#9492;&#9472;sda5       8:5    0 931.3G  0 part  
  &#9492;&#9472;cr_lvm 252:0    0 931.3G  0 crypt 
    &#9500;&#9472;kubuntu--vg-root
    &#9474;      252:1    0 929.5G  0 lvm   /media/kubuntu/ea558532-9b70-48cd-bf13-2616d876b8f
    &#9492;&#9472;kubuntu--vg-swap_1
           252:2    0   1.8G  0 lvm   
sr0         11:0    1   1.3G  0 rom   /cdrom
loop0        7:0    0   1.2G  1 loop  /rofs
```

so I tried:

```
sudo grub-install --boot-directory=/media/kubuntu/d9e47709-9e1a-4795-8b61-d50ef9edf06a/ --root-directory=/media/kubuntu/ea558532-9b70-48cd-bf13-2616d876b8f5/ /dev/sda
```

but on rebooting I got the same error as before, so I booted back into the live CD and tried the second suggestion:

```

sudo grub-install --boot-directory=/media/kubuntu/d9e47709-9e1a-4795-8b61-d50ef9edf06a/ /dev/sda
```

but it gave the error: 
```

grub-install: error: cannot find a GRUB drive for /dev/sda/. Check your device.map

```

So I am not sure where to go next with it?

For oldfred's solution - I don't think I understand you properly, I am afraid - my lack of knowledge on the subject is preventing me understanding the context to those links you provided. 

I don't know why i would want to resize the partition? Everything I use is on a single partition (except the swap partition) so I don't understand why it needs resized? What am i missing? More than happy to lose the lvm if that's your advice but I don't really understand how to do it then how to boot thereafter (if, I am honest I am only vaguely aware of what the lvm does!).... I'll do some reading up ;-)

---

### Post by Nuno_Abreu on 2016-01-29
Oh, now I see what's wrong - you're using the LVM! My apologies... I thought you were using a normal partition.
OK, try this. From the Live CD (you must have lvm2 package installed, though), do the following:

```
sudo vgscan
sudo mkdir temporary && mount /dev/[COLOR=#000000][FONT=Ubuntu Mono]kubuntu--vg-root[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] ./temporary/ && [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]mount /dev/sda1[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] ./temporary/boot[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Now, let's bind some files:
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]mount -o bind /dev/ ./temporary/dev/ && mount -o bind /proc/ ./temporary/proc/[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Finally, let's chroot and install grub:
```
sudo chroot ./temporary && sudo grub-install /dev/sda && sudo update-grub
```

What about now?
[/FONT][/COLOR]

---

### Post by iclestu on 2016-01-29
Thanks for sticking with me.

When trying to do the command:

 ```
mount [COLOR=#000000][FONT=Ubuntu Mono]/media/kubuntu/ea558532-9b70-48cd-bf13-2616d876b8f5/ ./temporary[/FONT][/COLOR]
```

I get the following error:

```

mount:   [COLOR=#000000][FONT=Ubuntu Mono]/media/kubuntu/ea558532-9b70-48cd-bf13-2616d876b8f5/ is not a block device[/FONT][/COLOR]

```

---

### Post by Nuno_Abreu on 2016-01-29
> **iclestu said:**
> Thanks for sticking with me.

When trying to do the command:

 ```
mount [COLOR=#000000][FONT=Ubuntu Mono]/media/kubuntu/ea558532-9b70-48cd-bf13-2616d876b8f5/ ./temporary[/FONT][/COLOR]
```

I get the following error:

```

mount:   [COLOR=#000000][FONT=Ubuntu Mono]/media/kubuntu/ea558532-9b70-48cd-bf13-2616d876b8f5/ is not a block device[/FONT][/COLOR]

```

Oops, am I drunk? No, my head is just not responding correctly today. Check my edited post above yours, it should be fine now!

---

### Post by iclestu on 2016-01-29
Ah - unfortunately that hasn't changed anything.

I changed "mount /dev/kubunutu--vg-root" to "mount /dev/**mapper**/kubuntu--vg-root" in order to persuede it to run and also bound /sys/ to /temporary/sys after an initial warning message when updating grub.

After that the commands executed fine but on reboot I am back to the (initramfs) command line with the error message:

```

ALERT! /dev/mapper/kubuntu--vg-root does not exist.

```

Does the lvm need to set up this map during boot?

---

### Post by Nuno_Abreu on 2016-01-29
Yes, it should. Wasn't that set already on the Live CD? Well, then I do not know how to solve this - I'm searching for some answers, though. I came across this:
[https://stephentanner.com/restoring-grub-for-an-encrypted-lvm.html](https://stephentanner.com/restoring-grub-for-an-encrypted-lvm.html)

It might help The process is quite similar and you might have success!
Good luck!

---

### Post by iclestu on 2016-01-29
Its only set on the live cd after I mount the hard drive.

No worries - I really appreciate your efforts. Thank you

---

### Post by oldfred on 2016-01-29
If you go back to the thread on resizing it shows all the commands you need to mount your encrypted partitions and understand more about it. 
You just stop at this line:

You can now manage your encrypted partitions, mount them, copy them, or perform maintenance (fsck, backup, resize).

And part of the maintenance you can then do it reinstall grub.
To reinstall grub you mount / and /boot if you have one (almost all LVM installs do) and reinstall grub.

But still easier to use Boot-Repair's advanced options. You still have to make sure encrypted partition is mounted and tick the separate /boot before using Boot-Repair to fix your system.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by iclestu on 2016-01-30
Thanks oldfred - appreciate your guidance.

I've ran the repair tool with the /boot partition selected and still get to the same error:

```
ALERT! /dev/mapper/kubuntu--vg-root does not exist
```

I am never prompted for the passphrase for the encrypted disk when attempting to boot after boot-repair. Is there some option I am missing for encrypted disks on the boot-repair tool?

In case its of any use the latest paste-bin from the repair tool is here: [http://paste.ubuntu.com/14731106/](http://paste.ubuntu.com/14731106/)

---

### Post by oldfred on 2016-01-30
You do not install grub to the PBR of the /boot partition, but to sda or the MBR of the drive.

And you have to make sure you have mounted the root partition. If Boot-Repair is not asking for passphrase it is then not mounted and grub will not install correctly. You need to manually mount the root partition, then run the Boot-Repair fix. 

But it looks like somewhere you mounted it as it shows files inside it:
/mapper/kubuntu--vg-root/etc/default/grub

---

### Post by Nuno_Abreu on 2016-01-30
I think Boot-Repair does not manage LVM volumes by default, the lvm2 packages has to be installed. Then, it is time to decrypt the volume - that's what I tried to do with the commands I've posted... With the device mappers of the encrypted volumes I wanted to install grub to the MBR, based on the boot and root directories given (the /boot partition was obviously out of the encrypted volume because the BIOS can't decrypt LUKS).

I'd suggest the OP to do the same he did before, but add a final command:
```
sudo chroot ./temporary && sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

