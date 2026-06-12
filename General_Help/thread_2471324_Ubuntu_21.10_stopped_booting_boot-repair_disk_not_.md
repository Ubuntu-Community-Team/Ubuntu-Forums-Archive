---
title: "Ubuntu 21.10 stopped booting /boot-repair disk not fixing"
date: 2022-01-26
forum: General Help
---

### Post by cigtoxdoc on 2022-01-26
This concerns my DELL Vostro 3500, which is dual-boot Ubuntu 21.10 and Win XP Pro SP3.  I was over on the Windows side this afternoon to back up some files that I wanted to back up on a commercial service that does not work with Linux.

When I rebooted, the PC when right into Windows.  This has happened before.  I tried boot-repair disk several times and it did not work.  Boot-repair would not let me repair GRUB (several lines dealing with chroot that I need to execute in a terminal), which is often the cure.  SSD (less than a year old) shows superblock checksum errors that I repaired with gparted, but they come back.  All my data files are backed up and I have several other PC's to use.  The last boot-repair details are at:

[http://paste.ubuntu.com/p/shJm2WXMMk/](http://paste.ubuntu.com/p/shJm2WXMMk/)

Even though the report shows boot successfully repaired, it isn't, and PC boots right into Win without putting up the GRUB menu.

How do I fix this problem?

Thank you,

John

---

### Post by oldfred on 2022-01-26
If going on the Internet, you should not be using XP, it is not supported and I have seen reports where it can be hacked within minutes of going on line.

It looks like newer UEFI system, with XP in BIOS/MBR mode but Ubuntu in UEFI mode on MBR drive.
Normally UEFI uses gpt as Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012.

You may just need to change from BIOS boot to UEFI boot in UEFI settings.
And XP does not install in UEFI mode. Most Windows 7 installs were BIOS/MBR, but Windows 7 could be UEFI as long as UEFI Secure Boot is off.

---

### Post by cigtoxdoc on 2022-01-26
Thank you for your reply.  My DELL Vostro is over ten years old and is working very well.  There is NO UEFI.  I have been running dual boot with Win since I started using Ubuntu in 2014.  All I need help on is getting GRUB back in.  This is where I need help.

John

---

### Post by tea for one on 2022-01-27
Please take note of [COLOR="#0000FF"]oldfred's[/COLOR] advice - using end-of-life Windows XP to connect to the internet is imprudent.
Can you not use a supported version of Windows?

You will see the following lines in the report and Grub is undoubtedly affected by the file system damage.

[COLOR="#0000FF"]Line 116[/COLOR] - Mounting failed:   mount: /mnt/BootInfo/sda9: cannot mount; probably corrupted filesystem on /dev/sda9
[COLOR="#0000FF"]Line 123[/COLOR] - Mounting failed:   mount: /mnt/BootInfo/sda10: cannot mount; probably corrupted filesystem on /dev/sda10
[COLOR="#0000FF"]Line 129[/COLOR] - OS#2:   Ubuntu 21.10 on sda9

Have you tried to repair the partitions in a live session using **fsck**?

---

### Post by cigtoxdoc on 2022-01-27
Thank you for your message.  In my office I have five PCs running Win 10, including the one I am using to reply to your message.  Over at AskUbuntu, [https://askubuntu.com/questions/849872/how-can-i-prevent-windows-10-from-corrupting-the-ext4-superblock-every-time/858159#858159](https://askubuntu.com/questions/849872/how-can-i-prevent-windows-10-from-corrupting-the-ext4-superblock-every-time/858159#858159), there is a discussion of the same problem, and it occurs on dual boots between newer versions of Ubuntu and Win 10.  One of the problems was that there were errors on the Win partition and running the full ckhdsk fixed those.  Running gparted fixed the errors on the Ubuntu partitions.  Boot-repair then did what it should, it reinstalled Grub.  That fixed the problem.  I am back up and running on my favorite PC.

John

---

