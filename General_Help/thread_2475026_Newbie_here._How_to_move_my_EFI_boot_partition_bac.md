---
title: "Newbie here. How to move my EFI boot partition back to my Linux nvme drive?"
date: 2022-05-14
forum: General Help
---

### Post by Advait on 2022-05-14
[COLOR=#000000][FONT=Arial]I’m running Ubuntu 21.10 on my main internal nvme. On my 2nd internal nvme I have Windows 10. I spend 99.8% of my time in Ubuntu. About 3 weeks ago I was rebooting and out of the blue my system rebooted into Windows and started doing updates. I don’t know why this happened and I was not happy about this. After the Windows update finished I discovered that the Windows update had removed Ubuntu from my grub menu. I went on to Upwork and hired a Linux admin who fixed it.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Note: Windows FastBoot is turned OFF.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]See image here [/FONT][/COLOR][[COLOR=#1155cc][FONT=Arial]_[https://imgur.com/Qjzbaxd.png](https://imgur.com/Qjzbaxd.png)_[/FONT][/COLOR]]("https://imgur.com/Qjzbaxd.png")[COLOR=#000000][FONT=Arial] Now my EFI boot partition is on my Windows nvme and not my Linux nvme. How can I safely move the EFI partition back to my Linux nvme? I’m a Linux newbie. Do I need to hire a Linux admin to do this for me? I know zero about shell/bash.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Also, what are the consequences of having the EFI partition on my Windows nvme? [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Also, why would a Windows update screw up my grub menu? How can I prevent that from happening again?[/FONT][/COLOR]

---

### Post by TheFu on 2022-05-14
Windows has always been hostile towards other OSes.  Complain to MSFT.

Inside any computer, there is supposed to be only 1 EFI partition which is supposed to be shared by all OSes.

If you don't need to dual boot for GPU reasons, I'd really push you do stop it and start using virtual machines.  Put either Windows or Linux as a guest OS running under the other.  Whichever needs the best GPU performance is the one I'd run native.  VirtualBox runs on both systems and is pretty easy to figure out.  Your Ryzen will easily handle running multiple VMs. Easily.

There is nothing in Linux that you cannot perform yourself, but you need to have the desire and ability to learn. If you don't want this, you can pay someone else to handle it, but I wouldn't bother.  Does it really matter where the EFI partition sits?  I don't think it does.  I wouldn't worry about this at all.  I suppose you could use gparted to copy the EFI partition over, but you'll need to modify the /etc/fstab with the new UUID or Linux won't boot. You'll probably want to remove the old EFI partition to prevent confusion.  I have no idea what this will do to Windows. It may not boot. Most people would probably end up doing a reinstall of Windows, which would put the EFI back where it is.  I'm guessing. I haven't installed Windows on a physical computer in over a decade. My installs have only been into virtual machines.  

Maybe I shouldn't be posting at all.  There is a standard order to having a working dual-boot system.
a) install Windows - always must be first
b) install Linux and other OSes

BTW, in about 6 weeks, support for 21.10 will end, so you should be planning to move to 22.04 now.  And if you aren't technical, I'd stay on 22.04 for the next 2-4 yrs.  22.04 is an LTS with 5 yrs of support for the core packages. If you happen to run a different GUI/DE than the Gnome3 or Gnome4 (22.04) standard DE, then only 3 yrs of support is provided.  I don't keep up with non-LTS releases.  Just remember that "new" isn't always better.

---

### Post by Advait on 2022-05-14
> **TheFu said:**
> Windows has always been hostile towards other OSes.

Yes! I've now discovered that.

> If you don't need to dual boot for GPU reasons, I'd really push you do stop it and start using virtual machines.

Yes, I'm thinking of doing just that soon. I already have Windows working in a VBox VM and if I can get the EFI moved to my Linux nvme, then I'll likely remove the Windows nvme and store it in a safe place.

> Your Ryzen will easily handle running multiple VMs. Easily.

Yes, I got the extra RAM so I could play around with VMs.

> There is nothing in Linux that you cannot perform yourself, but you need to have the desire and ability to learn.

True. And I simply don't have the free time to study and practice Linux admin skills. I wish I did; it would be fun to build a little home lab and play around with Linux, distros, etc.

I found this site [https://askubuntu.com/questions/1250199/move-bootloader-or-remove-efi-partition-in-second-drive](https://askubuntu.com/questions/1250199/move-bootloader-or-remove-efi-partition-in-second-drive). Looks like it will give the Linux admin I hire a lot of what they need to do the EFI move.

> BTW, in about 6 weeks, support for 21.10 will end, so you should be planning to move to 22.04 now.

Yep, I'll upgrade to 22.04 and stick with that for the long term. And I'm very happy with the standard Ubuntu Gnome DE. Works great for me.

---

### Post by TheFu on 2022-05-14
We all trade money for time and expertise. Nothing wrong with that.  

Often, things that seem simple for 1 person aren't so simple or they just don't want to be bothered.  Sure, I can change the oil in my cars, but after doing that about 10 yrs, I choose to pay someone else to handle it, clean up any spills, and dispose of the old oil and filter.  Even though it is less than 5 minutes of my time in total, I'll spend $30 and sit in a waiting room for 30 minutes doing something else while "they" handle the hassles.  

What I do miss by not changing the oil myself is actually looking at the engine, seeing other issues like little fluid leaks from the transmission or wiper fluid or radiator and getting those corrected before being stranded somewhere inconvenient.  The same applies with computer maintenance or paying an accountant to handle personal finance.  The paid person likely doesn't care about the result as much as you or I might. Even if they perform what we ask expertly, that doesn't mean that we'd make the same choices to that result, if we had the same expertise.

BTW, 22.04 moves to Gnome4. It is a change. How much, I don't know, but there have been complaints in these forums about some things. I don't use a DE, prefer running just a window manager which I've used off and on since the mid-1990s. I just got tired of having the interface change every few years and realized that really wasn't necessary.

---

### Post by Advait on 2022-05-14
> **TheFu said:**
> BTW, 22.04 moves to Gnome4. It is a change. How much, I don't know, but there have been complaints in these forums about some things.

My brain is wired to be flexible when it comes to things like DEs and UIs. I actually like the process of getting my brain wrapped around a new UI. And I'm sure the UI changes in Gnome 42 will seem trivial to me.

When I switched from Windows to Gnome I found it trivial to learn Gnome. They both use the same basic UI elements and design conepts.

---

### Post by yancek on 2022-05-14
If you have both systems as UEFI and were using Grub to boot them both with Ubuntu set to boot first, there would be no reason for it to suddenly boot windows without changes having been made.

I doubt windows modified your Grub menu as a default windows sysem can't read a Linux filesystem much less write to it.  Are you actually referring to the BIOS menu.

Some windows updates will turn on hibernation (this will not effect booting) as well as change windows to boot first and sometimes turn on Secure Boot.

Windows can be installed on a UEFI system using the Custom install option and will not overwrite Linux UEFI boot files as they are in a separate directory on the UEFI partition.  In all likelihoood, it will set itself to boot first in the BIOS firmware.

Having your Ubuntu and windows EFI files on the windows drive should not be a problem as long as you have that drive set to boot first.

If you do not have an EFI partition on the Ubuntu drive you would first have to create it and format it FAT32.  Then simply (using sudo) copy the files from the windows EFI partition to the Ubuntu EFI partition.  There will be a Microsoft directory there which you will not need to copy as you can select the windows drive to boot from the BIOS firmware as you use it so infrequently.

---

### Post by tea for one on 2022-05-14
> **Advait said:**
> I’m running Ubuntu 21.10 on my main internal nvme. On my 2nd internal nvme I have Windows 10. 

You have two drives, each with a separate operating system i.e. Windows and Ubuntu.
This is an ideal position, but you have to consider the details of each OS.

An OS on different computers = perfection
An OS on different drives on the same PC = ideal
Two OS on the same drive = be careful with updates and intermittent boot problems

I have two drives in my PC.
Each drive is GPT with UEFI mode installed systems.
Each drive also has an EFI partition, which allows me to _always_ boot from the UEFI one-time boot menu.

In effect, updates on one OS do not affect the boot of the second OS.

When I install a system to a second drive, I always isolate, de-activate via UEFI settings or physically remove the first drive.
Only the target drive is visible during installation (whether Windows or Linux)
I always install in UEFI mode with GPT and so far, touch wood, boot difficulties never appear.

As to moving your EFI partition, I wouldn't bother.
Isolate your Windows drive.
Back up your data, install Ubuntu 22.04 LTS on your non-Windows drive and allow the installer to create an EFI partition.

Boot either OS from your UEFI boot menu.

---

### Post by grahammechanical on 2022-05-14
Can you still boot into Ubuntu? In Ubuntu there is the Disks utility. May be there is something similar in Windows. Find out if your second nmve drive has an EFI system boot partition still. If it does you might be able to use the UEFI setting utility to boot from the second nmve drive. That might load Ubuntu, If it does then run this command

```
sudo grub-update
```

Check the listing. It should show both Ubuntu and Windows as detected. Now set the UEFI settings utility to boot from the second nvme drive as default (priority) and a Grub menu should appear with options to boot either Ubuntu of Windows.

Regards

---

### Post by Advait on 2022-05-15
@yancek, @grahammechanical, @tea for one, Thanks for the replies. I'm doing a little research on what you shared so I can understand it better. A few items you shared I don't quite get so I'm now googling.

PS: What is way to @ or # someone on this forum?

---

