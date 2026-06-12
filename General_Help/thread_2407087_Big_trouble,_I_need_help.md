---
title: "Big trouble, I need help"
date: 2018-11-29
forum: General Help
---

### Post by Dave Martyn on 2018-11-29
Good evening, I recently borrowed my lads girlfriends laptop as mine had died. She more or less said I could do what I wanted with it. I was running windows 7 Ultimate on it and decided I wanted to give Linux a go. I installed Ubuntu on the drive but wasn't happy with it, but when I try to reload windows 7 onto it, it tells me windows cannot be loaded. I think its because I somehow managed to make the drive a Fat 32 instead of NTFS. How can I repair my hard drive to accept a windows 7 installation.
Many thanks in advance
Dave

---

### Post by QIII on 2018-11-29
Just a quick question before we go anywhere -- Did she indicate that you could wipe the drive (and thus all of her data, personal files, emails, pictures, etc)?

If not, you need to stop and recover data if possible.

---

### Post by Dave Martyn on 2018-11-29
Hello, yes she gave me carte blanche over everything, there was nothing on the laptop she required, it was always too slow for her.
Thanks for reply

---

### Post by QIII on 2018-11-29
Good.

Use the Live install media and go to "Try Ubuntu" rather than installing.  Open the terminal and type 

```
gparted
```

which will open the partitioning tool.

Delete all partitions on the laptop's storage device and create one large NTFS partition.  The creation of the NTFS partition should not really be necessary, but the Windows installer can be finicky. 

Exit out of the live session and install Windows 7.

If you have any difficulty, we'll be here!

---

### Post by Dave Martyn on 2018-11-30
Thank you very much. I shall report back and let you know how I get on.
Regards
Dave

I am determined to get away from Microsoft, just may take a little time. I have purchased a new Laptop and am thinking of trying Linux again, any suggestions for a newbie to try?

---

### Post by HermanAB on 2018-11-30
Well, you can either set up the machine to dual boot on the existing HDD, or you can install Linux on removable media: A USB disk drive, a SD card, or a USB flash memory stick.

---

### Post by dragonfly41 on 2018-11-30
If as likely you have Windows 10 on your new laptop you can get get a taste of Ubuntu by installing on Windows 10 the Windows Linux Subsystem.

[https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

But eventually you will move to one of the external solutions.

p.s. I forgot to mention the VirtualBox option on Windows 10 where you install Ubuntu as a VM.

---

### Post by RobGoss on 2018-11-30
Just curious to know what the **specs** are for this laptop, it might be that you need a **lighter version **of Ubuntu in order to have a better experience

---

### Post by CatKiller on 2018-11-30
> **Dave Martyn said:**
> I have purchased a new Laptop and am thinking of trying Linux again, any suggestions for a newbie to try?

Well, that depends on what you didn't like when you tried it before.

There are many different desktop environments, which each have their own feel. They can all be installed, independently of what the distro came with. It's likely that you'll find Ubuntu with your choice of desktop the easiest to manage.

Ubuntu used to use Unity by default, and recently switched to Gnome instead. I personally recently switched from Gnome to KDE. Cinnamon is popular. Xfce, LXDE and Mate are lightweight. There are also obscure and boutique combinations of different frameworks and window managers available if you become so inclined. 

For each desktop environment there's generally a live installer you can use to just test them out and play with them. It only costs you the download and reboot time; you don't need to install anything.

I'd recommend trying Gnome, KDE, and Cinnamon first.

---

### Post by RobGoss on 2018-11-30
**#1** Catkiller

---

### Post by Dave Martyn on 2018-11-30
Thanks :)

its a Samsung RV510 with 2gb Ram 500g hard drive running ubuntu

Thank you Killer

Thank you Dragonfly

Ok, am in the ubuntu live system and have opened terminal and typed in gparted, and a window comes up with "root privileges are required for running gparted"

thats me stumped :)
just found the sudo root explanation...…

ok am in gparted …… lets see what I can do :)

Thanks again, windows 7 now installed, going to run a few of the suggested live Linux, to get a proper feel for it.
Many thanks again

---

