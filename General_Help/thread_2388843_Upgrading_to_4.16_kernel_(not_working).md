---
title: "Upgrading to 4.16 kernel (not working)"
date: 2018-04-08
forum: General Help
---

### Post by Henry_Methorst on 2018-04-08
[COLOR=#111111][FONT=Ubuntu]Running Mate 16.04 LTS I tried to upgrade the kernel because I swapped my crappy wifi for an Intel AC 9260 and wanted the kernel support.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After running through the steps listed here (and rebooting of course) [/FONT]

 [http://news.softpedia.com/news/how-to-install-linux-kernel-4-16-on-ubuntu-17-10-and-ubuntu-16-04-lts-520514.shtml](http://news.softpedia.com/news/how-to-install-linux-kernel-4-16-on-ubuntu-17-10-and-ubuntu-16-04-lts-520514.shtml)

[FONT=Ubuntu] ```
 [/FONT][FONT=Consolas]$ uname -a [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][FONT=Consolas]Linux CQF-MSI 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux 
```[/FONT][/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

Still on 4.13 looks like to me :( 

Any help is much appreciated.[/FONT][/COLOR]

---

### Post by kerry_s on 2018-04-08
try running:
sudo update-grub

see what it says it finds.

---

### Post by Henry_Methorst on 2018-04-08
> sudo update-grub[sudo] password for henry: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.16.0-041600-generic
Found initrd image: /boot/initrd.img-4.16.0-041600-generic
Found linux image: /boot/vmlinuz-4.13.0-38-generic
Found initrd image: /boot/initrd.img-4.13.0-38-generic
Adding boot menu entry for EFI firmware configuration
done


 

Grub at reboot still shows 4.13

---

### Post by kerry_s on 2018-04-08
did you select the new kernel in grub?

to get into grub start tapping esc right after your bios is done.

---

### Post by Henry_Methorst on 2018-04-08
I can get a grub CLI, but thats about it, I don't know the command to invoke 4.16

---

### Post by jeremy31 on 2018-04-08
Post results for ```
lspci -nnk | grep -iA3 net
```
There is likely another way to support the wifi

---

### Post by monkeybrain20122 on 2018-04-08
> **Henry_Methorst said:**
> I can get a grub CLI, but thats about it, I don't know the command to invoke 4.16

From the grub menu choose advanced option, it should list all the kernels you have then if 4.16 is there, choose it and press enter.

---

### Post by Henry_Methorst on 2018-04-08
> **kerry_s said:**
> did you select the new kernel in grub?

to get into grub start tapping esc right after your bios is done.



BOOM it's done. I had to select the correct kernel in my rEFInd menu as it's a dual boot system. 

Thanks!!

---

