---
title: "Clean up Grub2 menu"
date: 2023-11-16
forum: General Help
---

### Post by rooman62 on 2023-11-16
This is a fork from [https://ubuntuforums.org/showthread.php?t=2492442&p=14165683#post14165683](https://ubuntuforums.org/showthread.php?t=2492442&p=14165683#post14165683) which must be considered closed please.

If I correctly understand, the files in the etc/grub.d folder are used by grub to dynamically create the boot menu. I would like to clean the menu but how can I work out which files I can delete?
I only need 3 entries; Ubuntu (normal and recovery mode) and one Windows entry. Dual boot on separate ssd.
For example I think 3 lines produce 3 Windows entries, is it safe to rename or move files from this folder to experiment?
For example lines 12 and 20 for Windows duplicate menu or 4 to 7? or the memtest entries?

etc/grub.d
```
1 /etc/grub.d/00_header
2 /etc/grub.d/05_debian_theme
3 /etc/grub.d/10_linux
4 /etc/grub.d/10_linux_proxy
5 /etc/grub.d/10_linux_zfs
6 /etc/grub.d/11_linux_zfs
7 /etc/grub.d/20_linux_xen
8 /etc/grub.d/20_memtest86+
9 /etc/grub.d/21_memtest86+_proxy
10 /etc/grub.d/22_os-prober_proxy
11 /etc/grub.d/25_bli
12 /etc/grub.d/30_os-prober
13 /etc/grub.d/30_uefi-firmware
14 /etc/grub.d/31_linux_proxy
15 /etc/grub.d/35_fwupd
16 /etc/grub.d/40_custom
17 /etc/grub.d/41_custom
18 /etc/grub.d/LS_linux
19 /etc/grub.d/LS_memtest86+
20 /etc/grub.d/LS_os-prober
```

---

### Post by yancek on 2023-11-16
My understanding is that the files ending in 'proxy' are used by Grub Customizer so if you use it, you probably need them.  If you don't, remove them.  I don't know why you have 2 linux_zfs files.  I don't have an files beginning with 'LS', maybe also part of Grub Customizer??  Line 12 is os_prober which will search for other OS's to add to the menu and is not just for windows.  I would suggest that you make a copy of the directory with the current contents and move it elsewhere, to your /home directory for example then you can experiment all you want. Or you could create another directory there and name it something else like grub.d2, then copy the files there.

---

### Post by tea for one on 2023-11-16
As I was a contributor to your previous thread, I'm very interested to see if this task can be fulfilled.

Assuming that both Windows and Ubuntu are installed in UEFI mode, I recommend that you prepare a backup boot USB device with rEFInd.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File
A USB with rEFInd for emergency use may help to find and boot an OS (if Grub is damaged/not responding)
i.e. It will find Windows Boot Manager and can also boot Ubuntu via the kernel (avoiding Grub).

Here are my files in /etc/grub.d
```
/etc/grub.d/00_header
/etc/grub.d/05_debian_theme
/etc/grub.d/10_linux
/etc/grub.d/10_linux_zfs
/etc/grub.d/20_linux_xen
/etc/grub.d/20_memtest86+
/etc/grub.d/30_os-prober
/etc/grub.d/30_uefi-firmware
/etc/grub.d/35_fwupd
/etc/grub.d/40_custom
/etc/grub.d/40_custom.save
/etc/grub.d/41_custom
/etc/grub.d/README
```

Possibly, you can remove all the files other than those above.
Then, boot into your Ubuntu installation via rEFInd USB and re-install/update-grub.

Fingers crossed

---

### Post by oldfred on 2023-11-16
Do not use grub customizer.

Totally reinstall grub, so proxy files removed.

Back up current grub stanza.
Turn off os-prober.
Then copy Windows boot stanza from grub backup & put into 40_custom.

---

### Post by rooman62 on 2023-11-16
Thanks for your suggestions, I'll attack asap.

And thanks for Thread tools info, didn't see it before.

---

### Post by MAFoElffen on 2023-11-17
At the end of the last thread, you said you were going to remove Grub Customizer, right? To correct that you reinstalled Grub2, right?

+1 with oldfred in Post #4. Migrate Windows to 40_custom.

To do what you what to do, what you do for testing is to turn off the execution bits of the concerned scripts in that directory. you then do 'update-grub' to test to make sure if it built it like you expected... That way you don't have to restore the file if it didn't.

First, make a backup of grub.cfg
```

sudo cp /boot/grub.cfg /boot/grub.cfg.old

```
Edit /etc/default/grub 
```

sudoedit /etc/default/grub

```
Ensure the line "GRUB_DISASLE_RECOVERY=true" is commented. If you wanted that entry to bremoved, then you would uncoment that. Ensure "GRUB_DISABLE_OSPROBER=true" is uncommented. Copy the menu entry for Windows from /boot/grub/grub.cfg.old into /etc/grub.d/40_custom

Remove the execution bit form all scripts except for 
```

/etc/grub.d/00_header
/etc/grub.d/05_debian_theme
/etc/grub.d/10_linux
/etc/grub.d/40_custom

```
If you want to leave the UEFI Settings menu item, leave the exectution bit for it, but you said you only with 3 lines in the Grub2 menu (without that).

You can remove the execution bit for all those by doing this
```

for Name in {10_linux_zfs 20_linux_xen 20_memtest86+ 30_os-prober 30_uefi-firmware 35_fwupd 40_custom.save 41_custom}; do sudo chomod -x /etc/grub.d/$Name; done

```
Rebuild your menu 
```

sudo update-grub

```
Reboot and test...

You can remove those files, or just leave them there turned off. The room they are taking up is less that 1MiB...

You said it was a closed system, so that should stay static. If it is not and receives update, then leave them their with the execution bit turned off. Create a script to turn off the execution bits of the concerned files if they are replaced over an update. 40_custom does not get replaced over an update.

---

