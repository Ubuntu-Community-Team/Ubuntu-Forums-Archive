---
title: "Bash like gnu grub menu"
date: 2024-03-19
forum: General Help
---

### Post by linuxisthebest2 on 2024-03-19
Hello, sorry to bother you, but I have a problem with my computer and maybe you can help me. I am running dual boot Windows and Ubuntu. When I turn on my computer it stays in the minimal bash-like cli gnu grub menu. When I type "exit" it gets me to Windows but only setup screen (set up wifi, username,...). Command "normal" does not help. I used very helpful tool (boot-repair) to get some info and quick repair. But there is no quick repair and I am quite stuck. I will be very glad if you can help me with that. I can send a report from boot-repair program if you want. Thank you very much.

Link to pastebin: [https://paste.ubuntu.com/p/BzkzK5yw2B/](https://paste.ubuntu.com/p/BzkzK5yw2B/)


[B]EDIT:
[/B]&#8203;I think some partitions are missing. I am sendings pictures. Bigger is Windows and smaller is Ubuntu.

Sincerely,
* * * * * * *Damián

---

### Post by ajgreeny on 2024-03-19
Run Boot-repair again from a live USB if necessary,  but choose to run just the **boot-info** script, not any repair.
The output you see will offer to upload the info to **pastebin** which you should accept and then copy/paste that pastebin link into your reply to this post.
There are many users here who are able to decipher that info and hopefully solve your problem.

There is a link to boot-repair in my signature below.

---

### Post by yancek on 2024-03-19
Running boot repair and posting the output would be the best way to start getting help.  Did your dual boot ever work, were you able to boot both windows and Ubuntu?  You indicate you get to a 'setup screen' when you try to boot windows.  That seems a bit odd.  Did you actually have an installed, functioning windows OS?  If both Ubuntu and Windows previously booted, were any changes made prior to this problem?  Most of the other questions should be answered with boot repair.

---

### Post by linuxisthebest2 on 2024-03-19
Thanks a lot.

Here is the link: [https://paste.ubuntu.com/p/BzkzK5yw2B/](https://paste.ubuntu.com/p/BzkzK5yw2B/)

---

### Post by linuxisthebest2 on 2024-03-19
[COLOR=#000000]Hello, here are some answers that maybe can help: 

[/COLOR][COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]**Didyour dual boot ever work, were you able to boot both windows andUbuntu?**[/FONT][/COLOR]


Yes,it works well to this date. I forgot about it, and laptop was turnedon whole night and the night after that night it stops working.


[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]**Didyou actually have an installed, functioning windows OS?**[/FONT][/COLOR]


Yes,I was running Windows just fine, all accounts, files etc. But nowwhen I type „exit“ to this cli gnu grub menu it will take me toWindows and it wants password to wifi, username and all of thisstuff.


**[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]Ifboth Ubuntu and Windows previously booted, were any changes madeprior to this problem?[/FONT][/COLOR] **


No,except it was turned on whole night.

---

### Post by tea for one on 2024-03-19
[COLOR="#0000FF"]Line 55[/COLOR] - 1 OS detected 
[COLOR="#0000FF"]Line 57[/COLOR] - OS#1:   Windows 10 or 11 on mmcblk0p3

Your internal disk (mmcblk0) does not contain any Linux partitions
Can you power off the PC and then try to boot Windows via the PC one time boot menu (i.e using the dedicated key)

---

### Post by oldfred on 2024-03-19
You only have the live installer.
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

And with a small MMC drive, you really do not have room for Both Windows & Ubuntu on it.
If you want a full install, you have to install from one USB flash drive to another USB flash drive.
But if you want fast system use a SSD as external drive.

---

### Post by linuxisthebest2 on 2024-03-19
When I press F7 during startup and I get to the boot menu, there is only ubuntu. And when I select Ubuntu, it will go back to the cli gnu grub menu.

---

### Post by tea for one on 2024-03-19
Select "Enter Setup"
Do you see Windows Boot Manager within the settings?

---

### Post by linuxisthebest2 on 2024-03-19
No, I can't see it.

---

### Post by tea for one on 2024-03-19
> **linuxisthebest2 said:**
> No, I can't see it.
That's a pity.

As boot-repair has reported that you only have Windows on your internal disk, then you'll need to use Windows tools to try and locate (or re-install) the Windows Boot Manager.
Do you have a USB device with a Windows Installer or a Windows recovery drive?
The Ubuntu boot-repair software cannot repair Windows boot difficulties.

I cannot offer more pertinent advice because I've never had to use Windows repair utilities.

---

### Post by linuxisthebest2 on 2024-03-19
Ok, thanks a lot.

---

### Post by oldfred on 2024-03-19
Since UEFI, you should be able to go into UEFI settings (not UEFI one time boot menu) and change boot order so Windows is first.

Or from Ubuntu you can use efibootmgr, unless an HP system as those can only be changed in UEFI settings.

---

### Post by linuxisthebest2 on 2024-03-21
Does someone know how to backup partition when I cant mount it?

---

### Post by ajgreeny on 2024-03-21
Have a look at gparted from the USB you used to install the system which can be used to move or copy/backup partitions.

I have never done this myself so can't offer any more detail but gparted always needs partitions unmounted in order to act on them so may be a good place to start.

---

### Post by linuxisthebest2 on 2024-03-21
I have tried it, but as it is not mounted I cant do that. But I am thinking if installing ubuntu again but with option to not format disk, so files (documents, etc.) will be kept. It can maybe be a solution. What do you think?

---

### Post by linuxisthebest2 on 2024-03-21
No, it wont work, because ubuntu installer does not even see the other disk (partition).

---

### Post by yancek on 2024-03-22
>   ubuntu installer does not even see the other disk (partition). 		

What other disk or partition?  What are you trying to back up?  All of the information you posted shows only windows filesystems on the various partitions on your small drive so are you trying to back up your windows files?  Best to use windows tools for that.  Was this an actual install of Ubuntu on a separate partition or was it a windows subsystem for Linux.  Reinstalling the same version of Ubuntu (or other Linux systems) without formatting should work to repair.  The problem is that nothing you have shown indicates there is anything related to Linux installed.

---

### Post by linuxisthebest2 on 2024-03-22
Ok, thanks

---

