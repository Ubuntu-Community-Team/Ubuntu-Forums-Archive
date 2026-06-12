---
title: "When booting I get the following message: 'irq9 nobody cared (try booting with the &quot;i"
date: 2022-04-17
forum: General Help
---

### Post by notreallyeight on 2022-04-17
I have been trying to boot my Ubuntu installation, it used to work  fine before but when I restarted it prompted this error message and I  can only see a black screen with that text. After Googling around I saw  there were other people with my same CPU and laptop model with the same  issue. Thanks in advance!


 Full message: irq 9: nobody cared (try booting with the "irqpoll" option) [<0000000030056519>] acpi_irq Disabling IRQ #9

 
My system specs: 
Lenovo V15-IIL 
Ubuntu 21.10
Intel Core i5-1035G1

---

### Post by oldfred on 2022-04-17
Did you try the irqpoll boot parameter?

Have you updated UEFI & SSD to latest firmware?

Lenovo V15 G2 ALC Ryzen 5700U + Ubuntu 21.04
[https://ubuntuforums.org/showthread.php?t=2462880&page=2](https://ubuntuforums.org/showthread.php?t=2462880&page=2)

Some Lenovo also have this UEFI setting:
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.

---

### Post by notreallyeight on 2022-04-17
Yes, the error goes away but I still cannot boot and only get the following output:

[ATTACH=CONFIG]290300[/ATTACH]

Yes, I have updated UEFI & SSD to latest firmware, same issue.

I have also seen the other thread, but I can access all the disk files so I am pretty sure it recognizes the disk

---

### Post by oldfred on 2022-04-17
Clean is normal and that is good.

It looked like you had installed the nVidia driver.
But can you press escape to get grub menu and boot recovery mode. Or manually add nomodeset boot parameter.

We now normally do not have to use nomodeset with nVidia as you can use Safe Boot to boot live installer & choose to install the restricted extras to get the proprietary nVidia driver installed.

Also please do not post screen shots or photos in line. Attach with Forum's advanced editor and paperclip icon.

---

### Post by notreallyeight on 2022-04-18
Hmm, my laptop does not have any Nvidia GPU, why do I have any of its driver installed? &#55357;&#56837;

About recovery mode, after getting into recovery mode do I need to do anything else? I only get a screen with multiple options there

---

### Post by ActionParsnip on 2022-04-18
If you boot an older kernel is it OK?

---

### Post by notreallyeight on 2022-04-18
In an older kernel I still get the clean line, nothing else if I use the irqpoll option. If I don't put any option then I get the error

---

### Post by oldfred on 2022-04-18
Sorry about confusion on nVidia. That was another thread I was posting in.

Can you boot recovery mode, or second line in grub menu?
And then try all the options.

---

### Post by notreallyeight on 2022-04-18
I can boot into recovery mode, and most of the options give no errors.

fsck gives the following error:
[B]/lib/recovery-mode/recovery-menu: line 80: /etc/default/rcS: No such file or director
fsck from util-linux 2.36.1
/dev/nvme0n1p4 is mounted.
e2fsck: Cannot continue, aborting.


[/B]dpkg gives the following:
[B]Reading cache
Reading package lists... Done
Reading dependency tree... Done
Reading state information... Done
No candidate ver: ippusbxd
No candidate ver: python3.8-minimal

Calculating the changes
No candidate ver: ippusbxd
No candidate ver: python3.8-minimal

EFI System Partition (ESP) not usable

Your EFI System Partition (ESP) is not mounted at /boot/efi. Please ensure that it is properly configured and try again.
[/B]

---

### Post by oldfred on 2022-04-18
Are you booting in UEFI mode?
Post this:
sudo parted -l
cat /etc/fstab

You may need to boot recovery mode, and copy to a folder so you can upload from live installer, if you cannot continue to boot.
Or mount folders & use that path to /mount_from_live_installer/etc/fstab

I thought from recovery mode, you could run fsck before everything is mounted. But then ESP would not be mounted.

---

### Post by notreallyeight on 2022-04-18
I think I am booting in UEFI mode, but I cannot be sure as I don't know how to check

The output of the commands is as in the attachment:

---

### Post by oldfred on 2022-04-18
You have ESP - efi system partition on gpt drive.
Windows only boots in UEFI mode from gpt drives.
For Ubuntu you show the mount of the ESP in your fstab. So unless you also installed grub in BIOS/CSM/Legacy mode, you are in UEFI mode.

Your UEFI boot entry for Ubuntu should be similar to mine, except with your GUID/partUUID for ESP partition.
> 
[FONT=monospace][COLOR=#008080]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo efibootmgr -v[/COLOR]
[/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]Boot0018* ubuntu        HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\UB[/COLOR]UNTU\SHIMX64.EFI)
[/FONT][/FONT]

I might comment out your extra data partition to see if that is the issue. I also prefer to mount/label everything without spaces or special chars.
I use CamelCase, under_score or justalabel as styles for my entries.

---

### Post by notreallyeight on 2022-04-18
It used to boot fine for months though even though I had spaces in the partition name, how could that be an issue? (I'm asking as I am pretty much a newbie)

---

### Post by oldfred on 2022-04-18
Partitions do get corrupted. And then fsck if ext4 may be required.
If using NTFS, that would need chkdsk from Windows. But NTFS not recommended on Linux only systems.

---

### Post by notreallyeight on 2022-04-18
Ah, I actually use this partition on both Windows and Linux, so that could be the case I guess?

---

### Post by notreallyeight on 2022-04-18
> **notreallyeight said:**
> Ah, I actually use this partition on both Windows and Linux, so that could be the case I guess?

About this, I can still access the files in the partition when I am on Windows, so I think it is not corrupted because well I can access the files

---

### Post by oldfred on 2022-04-18
Did Windows turn fast start up back on, setting hibernation flag?
That prevents the Linux NTFS driver from loading the NTFS partition. It may still boot but has to time out and take several minutes to time out.

My old XP NTFS partition needed chkdsk. The XP chkdsk fixed some things. But I had to run a Windows 7 chkdsk to fix them all. But then it needed a XP chkdsk to revert to XP type NTFS. After chkdsk, my XP boot time dropped from 5 min, to only 3 min. Big part of why I changed to Ubuntu.

---

### Post by notreallyeight on 2022-04-19
Yes, Windows had turned on fast boot, but turning fast boot off still gives the error and still does not boot the system

---

