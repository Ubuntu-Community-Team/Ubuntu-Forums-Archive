---
title: "Reinstalling Ubuntu as main OS after removing dual-boot (Black screen)"
date: 2021-04-17
forum: General Help
---

### Post by johtzenbach on 2021-04-17
Hello everyone, I have the following problem:

I installed Dual boot (Ubuntu and Windows), but then I decided to delete Ubuntu completely. I've been using Windows for a few months with no problems. Now I want to install only ubuntu, and use it as my main and only OS.

I have an USB with the ubuntu installation (I used rufus). Now I'm trying to boot from the USB to install Ubuntu but in the GRUB there's no option to "Install Ubuntu", It shows the option to start from Ubuntu directly as if it was never removed (which I actually did, I deleted the partitions and everything).

Obviously if I try to start from the Ubuntu option then a black screen appears.

1. I tried the first and second option ("Ubuntu" and "Ubuntu(safe graphics)"). Both of them get me into a black screen.
2. I downloaded Rufus and the Ubuntu iso again, nothing happened.
3. I changed the USB thinking that it could be the problem. Nothing.
4. I tried with Secure boot disabled and CSM enabled. Nope.
5. Also with CSM disabled and with rufus installer as UEFI/GPT and not BIOS.
6. I added 'nomodeset' at the end of the linux line before quiet splash, after quiet splash and also replaced quiet splash with it (obviously not all at the same time but in each restart). Nothing.

What is happening here? I'd appreciate some help.

---

### Post by oldfred on 2021-04-17
If UEFI system, do not use CSM.
With Rufus use the UEFI/gpt option which creates an installer that only works in UEFI mode. Other tools may make an installer that will work in both modes.
Setting in UEFI, is normally for installed system, once installed. How you select boot of USB installer is then how it installs. 

Often easier with UEFI Secure Boot off, especially if you need proprietary drivers for graphics or wireless. But boot in UEFI mode, always.

What brand/model system? What video card/chip? Some require special settings.
If nVidia, you may need nomodeset or Safe Boot mode.
See general instructions in link in my signature for more UEFI install info.

You may not be booting USB live installer. You want USB entry, not ubuntu entry.
UEFI often keeps the ubuntu boot entry in UEFI and /EFI/ubuntu files in ESP. But with rest of grub & boot in partition you deleted, it will not work.

---

### Post by johtzenbach on 2021-04-18
> **oldfred said:**
> If UEFI system, do not use CSM.
With Rufus use the UEFI/gpt option which creates an installer that only works in UEFI mode. Other tools may make an installer that will work in both modes.
Setting in UEFI, is normally for installed system, once installed. How you select boot of USB installer is then how it installs. 

Often easier with UEFI Secure Boot off, especially if you need proprietary drivers for graphics or wireless. But boot in UEFI mode, always.

What brand/model system? What video card/chip? Some require special settings.
If nVidia, you may need nomodeset or Safe Boot mode.
See general instructions in link in my signature for more UEFI install info.

You may not be booting USB live installer. You want USB entry, not ubuntu entry.
UEFI often keeps the ubuntu boot entry in UEFI and /EFI/ubuntu files in ESP. But with rest of grub & boot in partition you deleted, it will not work.

Thanks for your help, I managed to solve the problem. 

I will describe what I did in case anyone stumbles into this thread from google.

1-  I Disabled 'Launch CSM' 
2- Disabled Fast Boot 
3- Disabled Secure Boot  Control 
4- I saved all boot variables in a USB. 
5- I deleted the PK Key  
6- I inversed the boot option (first the USB with ubuntu, then windows) 
7  -Installed the ubuntu iso with rufus, but I used GPT in partition, and  UEFI in target. 
8 -I selected Ubuntu(safe graphics) in grub, and  replaced 'quiet splash' with nomodeset.

 Then it worked. I have an Asus  laptop with Nvidia.

---

### Post by CelticWarrior on 2021-04-18
> [COLOR=#000000]8 -I selected Ubuntu(safe graphics) in grub, and replaced 'quiet splash' with nomodeset.[/COLOR]


This should be temporary only. You need to install Nvidia drivers then remove nomodeset.

---

### Post by johtzenbach on 2021-04-19
> **CelticWarrior said:**
> This should be temporary only. You need to install Nvidia drivers then remove nomodeset.
Thanks I will look into it.

Another question if anyone is still here.

I did the installation, replacing Windows with Ubuntu.

Now I was curious about the partitions, so I checked in the terminal:

[URL="https://ibb.co/JCwy8VD"][IMG]https://i.ibb.co/Ptv9JKq/terminal-disks.png[/IMG]
[/URL]

My PC had 2 partitions, C: and D:
I installed Ubuntu in the D: partition (the biggest one, 931,5g), and I thought this would erase everything about windows.

Is it normal to still have the sdb3 ntfs (C: ) with Windows? I thought that selecting said installation option would erase all disks.

I'm wondering if this could case any problems in the future. Right now I'm booting to Ubuntu by selecting the first option in GRUB, and it's working fine.

---

### Post by oldfred on 2021-04-19
It looks like you have Windows installed on sdb.
The erase option only erases the drive you install into, not all drives. 
Note that Windows confuses drives with partitions. A drive should be sda, sdb, sdc, etc. And partitions are sda1, sda2, sdb1, sdb2 etc or number on a drive. Windows d: "drive" may be another partition on same drive like sda2 or another drive's partition like sdb1.

If you want to see all details of your system configuration. I run this report periodically and save into /home so part of my normal backup, just to document system.

If system is working, do not run any fixes, just the report.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

