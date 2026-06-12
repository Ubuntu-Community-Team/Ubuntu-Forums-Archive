---
title: "Ubuntu not booting all of a suden"
date: 2015-08-25
forum: General Help
---

### Post by buisteric on 2015-08-25
Two days ago, I was able to boot into my Ubuntu box. This morning, it freezes at the Ubuntu logo and nothing more. After more than 30 seconds, I tried CTRL-ALT-F1, CTRL-ALT-F7, and ended up in a rescue prompt. The /var/log/syslog contains nothing related to today's boot. The text is very small, making it hard to read for me. Clueless, I tried to reboot, and now I'm stuck with a black screen, nothing more. I just cannot believe I have YET ANOTHER dead drive (a SSD this time), because I just booted Windows 10 off that same SSD. How can I deal with such issues if the system provides me no information and just offers me a very hard to read terminal screen as a troubleshooting facility. Booting from a live DVD or USB key takes more than two minutes, probably because once again, I didn't choose my DVD drive and/or motherboard correctly (probably my USB controller is flaky because USB keys are awfully slow), but I just don't know what to choose and what to do, this is never correct and always causing me tons of issues.

---

### Post by buisteric on 2015-08-25
I tried to reboot after writing this post and it now works. On my previous attempt, no NTFS partitions were mounted. My boot shouldn't rely on NTFS since my Ubuntu is installed onto a Ext4 partition, so this is quite strange. Seems NTFS has been updated with Windows 8 so I have issues with NTFS-3G under Ubuntu since then. I tried to disable the FastBoot in Windows, but the setting keeps turning itself on from time to time, so I'm a bit stuck. I just cannot format that 1Tb drive in FAT32 for it to work correctly with both Windows 8/10 and Ubuntu, nor can I downgrade to Windows 7 because of Ubuntu. I will probably end up moving that Ubuntu setup to a VirtualBox VM; this is becoming too maintenance intensive. But I feel I'm going backward if I do this. Linux was a first-class operating system for years and now it becomes something that can only run into VMs. At least Ubuntu still works great on my Linux-only HTPC, so my new problems are probably partly caused by dual boot with Windows 8, now upgraded to Windows 10.

---

### Post by grahammechanical on 2015-08-25
This is what I was about to post. It is the kind of information that we need in order to help you. Otherwise all you are doing is complaining. And complaints are not support requests.

"Go back to the beginning.

"Does Windows 10 still load correctly?  Do you get a Linux boot menu (Grub)? Can you select Advanced options for  Ubuntu? Can to select recovery mode? What happens when you select  recovery mode? Describe what happens. Did the machine come with Windows  10 pre-installed or did you upgrade from Windows 8.1. What are the  hardware specifications of that machine?

"Booting a Ubuntu live  session does take a long time because the live session has to  investigate the hardware and choose the correct hardware driver modules.  This is true whether we are using a DVD disc or a USB memory stick.

"If you upgraded from windows 8 to Windows 10 when did you do it? Was Ubuntu working after any upgrade to Windows 10?"

Regards.

---

### Post by yancek on 2015-08-25
> Two days ago, I was able to boot into my Ubuntu box. 

Since then, have you made any changes to the hardware or software on Ubuntu or windows and if so, what?

>  because I just booted Windows 10 off that same SSD. 

I would take that to mean that you have Ubuntu installed on this same SSD on which you have windows 10 installed and that both were previously working, correct?

> My boot shouldn't rely on NTFS since my Ubuntu is installed onto a Ext4 partition, 

It doesn't and never has for Ubuntu or any Linux system and whether ntfs partitions are mounted after boot or not has nothing to do with the actual boot process.
Do you now have windows 8 and 10 installed or did you upgrade to 8 and then to 10?

---

### Post by buisteric on 2015-08-27
Here are some more details.

I upgraded from Windows 8 to Windows 10 last weekend. The upgrade replaced my Windows 8 installation; there is no way to clean install alongside because Windows 10 rejects Windows 8 serial numbers so I would have had no way to activate the new Windows 10. The Windows 10 upgrade completely broke GRUB. The bootloader was going into rescue mode and not accepting any command. I tried with "help" and "?" to get a list of supported commands and that failed as well. I thus had to reinstall GRUB by using a Ubuntu live DVD. After that, I was able to boot both Ubuntu and Windows.

Tuesday morning, GRUB was still booting and I picked Ubuntu in its menu. Screen went blank, Ubuntu logo showed up and then system hung up. After a couple of minutes, I tried presing CTRL-ALT-F1 and got a blank screen with a blinking cursor. Pressing CTRL-ALT-F7 gave me the rescue shell with too small font size and only old stuff in /var/log/syslog. Trying to reboot gave me a blank screen and nothing else.

Windows was still booting. After a reboot from Windows, Ubuntu was working again.

The problem didn't happen since Tuesday. If that happens again, I will try the Ubuntu recovery from GRUB.

I did no change to the hardware these last days.

Intel Core i7
Asus P8Z77-V LX
NVIDIA GeForce GTX 650 Ti
16Gb of RAM
240GB SSD
1Tb hard drive

---

