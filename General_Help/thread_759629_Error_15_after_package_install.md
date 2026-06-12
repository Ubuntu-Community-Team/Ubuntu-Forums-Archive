---
title: "Error 15 after package install"
date: 2008-04-19
forum: General Help
---

### Post by SyMpToM on 2008-04-19
I was running Kubuntu 8.04 installed by Wubi, on a dual-boot system with Windows Vista.

Everything worked perfectly until today, when i tried to install a package with Synaptic the system froze and remained in this situation. I didn't have a choice but to hard reset it.

The unpleasant surprise came the moment i chose Kubuntu from grub..

I saw the dreaded find /ubuntu/install/boot/grub/menu.lst Error 15: File not found...

I am quite a newbie in Linux, so any help much appreciated (I dread the thought of re-installation as I have a fully configured Application server in Kubuntu which by no chance I wanna miss..)

---

### Post by ago on 2008-04-19
Hard reboots can cause filesystem corruption, and some files might no longer be accessible.
That can usually be fixed running chkdsk /r from windows or a windows CD 

To avoid hard resets see [https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a](https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a)

---

### Post by tigersrock on 2008-04-19
Exact same problem here. I was running ubuntu on dual-boot with windows xp

---

### Post by SyMpToM on 2008-04-19
I checked the partition with chkdsk /r but nothing changed.

Also when i navigated at the /ubuntu directory using Vista, when i double-clicked the disk sub-folder i had a "refers to a location that is
unavailable. It could be on a disk drive on this computer, or on a network.
Check to make sure that the disk is properly inserted, or that you are
connected to the internet or your network, and then try again. If it still
cannot be located, the information might have been moved to a different
location."  error and then, it disappeared.

Shall i forget my neat n tidy kubuntu?

---

### Post by ago on 2008-04-19
see if there are some hidden .found.0000 files and/or use a file recovery tool

---

### Post by Rioku on 2008-04-19
I also have this same issue! can anyone help us out! I had a perfect installation and put allot of hard work and effort into setting it up

pllleassee someone help

---

### Post by ago on 2008-04-19
Unfortunately hard reboot can compromise the filesystem (this is true whatever the OS), but wubi si more vulnerable to that than a normal installation. To recover you can try with chkdsk /r and if that does not fix it, you may have to try windows recovery tools. Basically you have to restore c:\ubuntu\disks\root.disk

Sometimes that gets moved to hidden files called found.000 (ntfs)

---

### Post by Rioku on 2008-04-19
well I tried chkdsk and it didnt help :S Do you recomend any recover tool?

I am kinda desperate to get this fixed for monday

---

### Post by SyMpToM on 2008-04-20
@Rioku

If checkdisk managed to recover your files they will be in a hidden system folder named "found". To view this you have to change the option in "View-Tools- Hide protected system operating files" to false.

@ago

Well, hopefully I recovered my files (many thanks) , but unfortunately, when I placed them back in their appropriate locations I get another after I select an option from menu.lst

```
/boot/vmlinuz-2.6.24.16-generic root=UUID=01C85AABF49E948 loop=/ubuntu/disks/root.disk ro quiet splash
```

The root.disk is there...

---

### Post by ago on 2008-04-20
You may need some recovery tools to restore found.000* files not sure if renaming them is enough. I am not too familiar with windows recovery tools either (am a Linux guy after all...).

---

