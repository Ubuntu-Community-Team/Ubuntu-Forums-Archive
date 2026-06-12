---
title: "How to get rid of ubuntu?"
date: 2015-02-15
forum: General Help
---

### Post by Brandon210395 on 2015-02-15
I can't Install windows back due to the changed boot system called Grub, I don't know how to operate it and I can't make anything work correctly using Wine, can anyone guide me through to go back to Windows? thank you.

---

### Post by Bucky Ball on 2015-02-15
Boot from the Ubuntu Live install media (disk or USB), open Gparted and delete all Ubuntu EXT* partitions. Then have a look through [here]("https://duckduckgo.com/?q=uninstall+grub&ia=qa") to uninstall grub.

---

### Post by carl4926 on 2015-02-15
Use your windows install dvd to fix the mbr boot
Then check you can boot windows
Now use windows disk management to delete the linux partitions

---

### Post by Brandon210395 on 2015-02-15
> **carl4926 said:**
> Use your windows install dvd to fix the mbr boot
Then check you can boot windows
Now use windows disk management to delete the linux partitions
i only have bootable windows USB, is that okay?
Cause when I try to install windows after formatting UBUNTU partitions 
I get the message:

> error: no such device: 58ABF29C...  
grub rescue>

> **Bucky Ball said:**
> Boot from the Ubuntu Live install media (disk or USB), open Gparted and delete all Ubuntu EXT* partitions. Then have a look through [here]("https://duckduckgo.com/?q=uninstall+grub&ia=qa") to uninstall grub.
Well im stuck on:
> error: no such device: 58ABF29C...  
grub rescue>
Can you help me? I cant get rid of Ubuntu

---

### Post by sgage on 2015-02-15
> **Brandon210395 said:**
> i only have bootable windows USB, is that okay?
Cause when I try to install windows after formatting UBUNTU partitions 
I get the message:

> error: no such device: 58ABF29C...  
grub rescue>


Well im stuck on:
> error: no such device: 58ABF29C...  
grub rescue>
Can you help me? I cant get rid of Ubuntu

What do you mean 'when I try to install Windows'? If you boot from your Windows media, you will see no mention of grub. Boot from your Windows media and go into 'system repair' mode. You will see the option to 'repair Windows startup' or some such (I am just recalling this from memory). You may have to run it a couple of times. If it tells you it can't fix the problem, you'll need to go to the command line option under, I believe, 'advanced options'.

From there, try 'diskpart /fixmbr' followed by 'diskpart /fixboot'. That usually takes care of it. If not, you will have to use fdisk, but that is not for beginners...

---

### Post by Brandon210395 on 2015-02-15
> **sgage said:**
> What do you mean 'when I try to install Windows'? If you boot from your Windows media, you will see no mention of grub. Boot from your Windows media and go into 'system repair' mode. You will see the option to 'repair Windows startup' or some such (I am just recalling this from memory). You may have to run it a couple of times. If it tells you it can't fix the problem, you'll need to go to the command line option under, I believe, 'advanced options'.

From there, try 'diskpart /fixmbr' followed by 'diskpart /fixboot'. That usually takes care of it. If not, you will have to use fdisk, but that is not for beginners...
But I can't boot from windows media at all. How am I suppose to create a working bootable windows usb using windows? Cause Winsub does not work anymore. Please help, thank you

---

### Post by Brandon210395 on 2015-02-15
when I try using my bootable UBUNTU usb now it shows: 
```
Missing parameter in configuration file. keyword: path
gfxboot.c32:not a com32R image
```

---

### Post by buzzingrobot on 2015-02-15
The Grub bootloader installed on the hard drive won't come into play -- not executed -- when you boot successfully from a Windows installation DVD/USB.  

If you cannot boot from your Windows installation DVD/USB, then something else is going on.  Be sure you have the BIOS set to boot from that DVD/USB drive.

---

### Post by sgage on 2015-02-15
> **Brandon210395 said:**
> But I can't boot from windows media at all. How am I suppose to create a working bootable windows usb using windows? Cause Winsub does not work anymore. Please help, thank you

I thought you said you had a Windows USB... You are going to need bootable Windows media, either the installation CD or a Repair CD. I believe you can download an iso image from DigitalRiver and burn it to a CD/USB stick. You don't need to reinstall Windows, just restore the Windows MBR and bootloader, and your former Windows installation should be fine. Unless you formatted its partition by mistake while you were trying to get rid of Ubuntu.

The other alternative is to reinstall Ubuntu on one of the now-empty partitions, and grub will offer you Windows in its boot menu. Once you're in Windows, then you can download the free EasyBCD program, which among its many features is the ability to give the MBR back to Windows.

Then you can use Windows' Disk Partitioner to delete the Linux partition and give the space back to Windows.

---

### Post by Brandon210395 on 2015-02-15
> **buzzingrobot said:**
> The Grub bootloader installed on the hard drive won't come into play -- not executed -- when you boot successfully from a Windows installation DVD/USB.  

If you cannot boot from your Windows installation DVD/USB, then something else is going on.  Be sure you have the BIOS set to boot from that DVD/USB drive.

> **sgage said:**
> I thought you said you had a Windows USB... You are going to need bootable Windows media, either the installation CD or a Repair CD. I believe you can download an iso image from DigitalRiver and burn it to a CD/USB stick. You don't need to reinstall Windows, just restore the Windows MBR and bootloader, and your former Windows installation should be fine. Unless you formatted its partition by mistake while you were trying to get rid of Ubuntu.

The other alternative is to reinstall Ubuntu on one of the now-empty partitions, and grub will offer you Windows in its boot menu. Once you're in Windows, then you can download the free EasyBCD program, which among its many features is the ability to give the MBR back to Windows.

Then you can use Windows' Disk Partitioner to delete the Linux partition and give the space back to Windows.

thank you guys, I am using Unetbootin now, I will update here if it will work or if it won't, thanks for trying to help me

---

