---
title: "New to Ubuntu would like to dual boot windows"
date: 2012-12-12
forum: General Help
---

### Post by meph1les on 2012-12-12
Hello

I just popped in ubuntu via a flash drive and I realized that for some reason I cannot install it because I have...from what my details is tellling me 7.8 GiB of memory and 4.2GB of disk...is this right? Another question is how do I dual boot ubuntu and windows 7? I would like to make windows 7 my main OS though unbuntu leaves me curious however I cannot install any information to get my N-300 netgear wireless adapter working on it. How do I go on about this procedure?

---

### Post by Rebelli0us on 2012-12-12
If you're just "curious" you can install Linux on a USB flash drive. A USB 3.0 card reader with a $17 UHS flash drive will read at ~70 MB/sec and OS runs just like from hard disk. And it's portable, you can stick it in any machine and boot.

---

### Post by meph1les on 2012-12-12
> **Rebelli0us said:**
> If you're just "curious" you can install Linux on a USB flash drive. A USB 3.0 card reader with a $17 UHS flash drive will read at ~70 MB/sec and OS runs just like from hard disk. And it's portable, you can stick it in any machine and boot.

Actually thats how I evne got ubuntu running but its telling me I have 4.3 gig worth of diskspace..which perplexes me this is a hard drive that is suppose to have 1TB. I was contemplating on zerioing the drive to see if that'll fix that problem but I ha eto relocate and reburn it it to a flashdrive which I'm doing as I speak

---

### Post by Mopar1973Man on 2012-12-12
I took my brand new Toshiba laptop and shrunk the NTFS partition down to about half the disk space and then install Ubuntu 12.04 to the empty partition. During install Grub is setup for you so it will dual boot automatically. 

Suggest to you. Take you time with Ubuntu. Try to give yourself ample time to do daily tasks with your computer on the Linux side. If you can figure it out do some researching. If you pressed for time then flip to windows and knock it out. But return back to Linux and continue to learn on how to do you daily tasks.

Now thatI've been using Ubuntu 12.04 and Lubuntu 12.04 I found myself needing less and less of windows as day went on. 

So welcome to the Ubuntu Family. ;)

---

### Post by meph1les on 2012-12-12
> **Mopar1973Man said:**
> I took my brand new Toshiba laptop and shrunk the NTFS partition down to about half the disk space and then install Ubuntu 12.04 to the empty partition. During install Grub is setup for you so it will dual boot automatically. 

Suggest to you. Take you time with Ubuntu. Try to give yourself ample time to do daily tasks with your computer on the Linux side. If you can figure it out do some researching. If you pressed for time then flip to windows and knock it out. But return back to Linux and continue to learn on how to do you daily tasks.

Now thatI've been using Ubuntu 12.04 and Lubuntu 12.04 I found myself needing less and less of windows as day went on. 

So welcome to the Ubuntu Family. ;)

Oh I'll take my time with it....once I get around to figure out how to use my clearewire mobile hotspot / Negear wirless N-300 to get stuff working and also some gaming. I do exactly what I do on my win7 laptop and winxp desktop but I dont think I've ever had such a difficult time just trying to get wireless internet working. I have no access to creating a hard wire connection and wireless is my only choice:-({|=

---

### Post by Rebelli0us on 2012-12-12
> **meph1les said:**
> Actually thats how I evne got ubuntu running but its telling me I have 4.3 gig worth of diskspace..which perplexes me this is a hard drive that is suppose to have 1TB. I was contemplating on zerioing the drive to see if that'll fix that problem but I ha eto relocate and reburn it it to a flashdrive which I'm doing as I speak

It could be that your Windows partition is using the entire disk leaving no room for another.

---

### Post by meph1les on 2012-12-12
> **Rebelli0us said:**
> It could be that your Windows partition is using the entire disk leaving no room for another.

Strange I've been unable to install it eversince I lacked the proper drivers to complete windows 7 on this msi 760GM-P23 (FX)motherboard.... whats a good program that I can stuff into a bootable usb to clean up my haddrive so that I can begin anew

---

### Post by Rebelli0us on 2012-12-12
> **meph1les said:**
> Strange I've been unable to install it eversince I lacked the proper drivers to complete windows 7 on this msi 760GM-P23 (FX)motherboard.... whats a good program that I can stuff into a bootable usb to clean up my haddrive so that I can begin anew

If as you said you're booting form USB flash drive, you can use "gparted" to format partitions. But if you choose to install from there, the Linux installer will give you the option to delete WIndows during the installation.

---

### Post by meph1les on 2012-12-12
> **Rebelli0us said:**
> If as you said you're booting form USB flash drive, you can use "gparted" to format partitions. But if you choose to install from there, the Linux installer will give you the option to delete WIndows during the installation.

I see I'll try that next....I tried using DBAN and kill@disk. DBAN ended abruptly saying that I have bad sectors, Kill@disk [active boot disk] Cant even find anything to delete

---

### Post by Corelogik on 2012-12-13
> **meph1les said:**
> I see I'll try that next....I tried using DBAN and kill@disk. DBAN ended abruptly saying that I have bad sectors, Kill@disk [active boot disk] Cant even find anything to delete

How big is the flash drive? If your running Ubuntu form the USB Flash drive, it may possibly be reporting that the flash drive has ~4GB left,... rather than reporting your HD, since it's not running from there.

---

### Post by meph1les on 2012-12-13
> **Corelogik said:**
> How big is the flash drive? If your running Ubuntu form the USB Flash drive, it may possibly be reporting that the flash drive has ~4GB left,... rather than reporting your HD, since it's not running from there.

ACTUALLY...afer exhausting most software methods I finally opened up and discovered....that a SATA cable was disconnected from my harddrive and after plugging that in everything started working again. I am now transferring my goods from laptop to my new desktop and working on a dual boot of ubuntu and win7

---

