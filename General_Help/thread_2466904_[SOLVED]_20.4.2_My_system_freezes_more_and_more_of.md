---
title: "[SOLVED] 20.4.2 My system freezes more and more often for no reason"
date: 2021-09-09
forum: General Help
---

### Post by thealpman on 2021-09-09
Hello,
My system freezes very often now :
- on the connection screen
- for no reason once the session is open (doesn't seem to depend on the software running)
- when I try to put the computer to sleep
Below are a couple information. Does somebody know where it might come from ?
Thank you 

```
jr@jr-ubuntu:~$ journalctl --no-pager --since yesterday -p err
-- Reboot --
sept. 09 16:11:06 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
sept. 09 16:11:06 jr-ubuntu systemd-udevd[667]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
sept. 09 16:11:06 jr-ubuntu systemd-udevd[667]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
sept. 09 16:11:08 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
sept. 09 16:11:16 jr-ubuntu gdm-password][1767]: gkr-pam: unable to locate daemon control file
sept. 09 16:11:22 jr-ubuntu gnome-session-binary[1328]: Unrecoverable failure in required component org.gnome.Shell.desktop
sept. 09 16:11:23 jr-ubuntu pulseaudio[1309]: Error opening PCM device front:0: Aucun fichier ou dossier de ce type
sept. 09 16:11:23 jr-ubuntu pulseaudio[1309]: Error opening PCM device front:0: Aucun fichier ou dossier de ce type
-- Reboot --
sept. 09 16:12:02 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
sept. 09 16:12:02 jr-ubuntu systemd-udevd[665]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
sept. 09 16:12:02 jr-ubuntu systemd-udevd[665]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
sept. 09 16:12:05 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
sept. 09 16:12:13 jr-ubuntu gdm-password][1771]: gkr-pam: unable to locate daemon control file
-- Reboot --
sept. 09 16:15:33 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
sept. 09 16:15:33 jr-ubuntu systemd-udevd[666]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
sept. 09 16:15:33 jr-ubuntu systemd-udevd[666]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
sept. 09 16:15:35 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
sept. 09 16:15:43 jr-ubuntu gdm-password][1790]: gkr-pam: unable to locate daemon control file
sept. 09 16:24:55 jr-ubuntu kernel: JS Helper: Corrupted page table at address 7f70183288f0
-- Reboot --
sept. 09 16:25:46 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
sept. 09 16:25:46 jr-ubuntu systemd-udevd[667]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
sept. 09 16:25:46 jr-ubuntu systemd-udevd[667]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
sept. 09 16:25:48 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
sept. 09 16:25:55 jr-ubuntu gdm-password][1758]: gkr-pam: unable to locate daemon control file
-- Reboot --
sept. 09 16:28:27 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
sept. 09 16:28:27 jr-ubuntu kernel: [drm:intel_dp_aux_xfer [i915]] *ERROR* dp aux hw did not signal timeout!
sept. 09 16:28:27 jr-ubuntu kernel: [drm:intel_dp_aux_xfer [i915]] *ERROR* dp aux hw did not signal timeout!
sept. 09 16:28:27 jr-ubuntu systemd-udevd[668]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
sept. 09 16:28:27 jr-ubuntu systemd-udevd[668]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
sept. 09 16:28:30 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
sept. 09 16:28:38 jr-ubuntu gdm-password][1793]: gkr-pam: unable to locate daemon control file
jr@jr-ubuntu:~$ 
```

```
jr@jr-ubuntu:~$ uname -a
Linux jr-ubuntu 5.4.0-81-generic #91-Ubuntu SMP Thu Jul 15 19:09:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
jr@jr-ubuntu:~$ 

```

```
jr@jr-ubuntu:~$ lspci -nnk | egrep -iA3 "VGA"
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:8a56] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:40d1]
    Kernel driver in use: i915
    Kernel modules: i915
jr@jr-ubuntu:~$ 
```

```
jr@jr-ubuntu:~$ jr@jr-ubuntu:~$ echo; dpkg -l | awk '!/^rc/ && /  linux-(c|g|h|i|lo|m|si|t)/{print $1,$2,$3,$4 | "sort -k3V | column  -t"}' ; echo -e "\nNoyau courant : $(uname -mr)"
jr@jr-ubuntu:~$ : commande introuvable
ii  linux-headers-5.4.0-70                5.4.0-70.78  all
ii  linux-headers-5.4.0-70-generic        5.4.0-70.78  amd64
ii  linux-image-5.4.0-70-generic          5.4.0-70.78  amd64
ii  linux-modules-5.4.0-70-generic        5.4.0-70.78  amd64
ii  linux-modules-extra-5.4.0-70-generic  5.4.0-70.78  amd64
ii  linux-headers-5.4.0-81                5.4.0-81.91  all
ii  linux-headers-5.4.0-81-generic        5.4.0-81.91  amd64
ii  linux-image-5.4.0-81-generic          5.4.0-81.91  amd64
ii  linux-modules-5.4.0-81-generic        5.4.0-81.91  amd64
ii  linux-modules-extra-5.4.0-81-generic  5.4.0-81.91  amd64
ii  linux-generic                         5.4.0.81.85  amd64
ii  linux-headers-generic                 5.4.0.81.85  amd64
ii  linux-image-generic                   5.4.0.81.85  amd64

Noyau courant : 5.4.0-81-generic x86_64
jr@jr-ubuntu:~$
```

---

### Post by Timothy Taylor on 2021-09-27
I also see more system lock-ups (again) now.

I first noticed this weeks ago after a system update: my PC would freeze when I hit the suspend key.  
I hit ESC on restart for splash-free boot: I noticed lots of "recovering inode.." messages and I suspected my HDD.  I fitted a new HDD, installed 20.04.2 and restored my data.  The system freezes persisted on suspend, so it wasn't the HDD.  
This problem seemed to coincide with the replacement of the NVIDIA drivers with Nouveau in the same update, but learned opinion here suggested a kernel bug.  I avoided using suspend and awaited a fix.

Despite several updates (now on 20.04.3), the problem remains: suspend still locks my PC and I still avoid using it.  

Now though, I find my PC locks up at random and the only way out is to restart my PC with reset button or Alt-PrtSct-B.
Again, if I hit ESC at restart, there are lots of "recovering inode.." messages.  I'm not sure if this means the filesystem is damaged by the forced restart?  That might explain why freezes are happening more often?

Luckily, I still have my old HDD holding the previous 18.04 system, so I tried that.  System suspend works on that with no problem, so there's something either with the kernel or the graphics driver updates on 20.04 which is causing this.  

The only reason I upgraded to 20.04 was because of messages saying that 18.04 was no longer supported.  I am now considering switching back to 18.04: I don't need support for a working system!

---

### Post by thealpman on 2021-10-19
Hello Timothy,

Thank you for your answer !
What is strange is that the computer was working just fine in the first couple months...
And now it freezes even when I boot on my USB drive with 20.04.3 and 21.10
So I'll also try to start on a USB drive with 18.04.6 after 20.04.3, 21.10 and we'll see !

What is very strange also is that the computer does not freeze when I keep a video playing with VLC in a loop (but it doesn't help for the sleep mode).
Someone suggested me to try to install windows to see if it's a hardware problem.

It's a shame, my previous computer worked just fine with the 20.04 version.

---

### Post by vmpx on 2021-10-19
Replace in GRUB menu for 20.04 ”quiet splash” with ”quiet splash  nomodeset” (On the grub screen click select ‘*Ubuntu’ and press ‘e’)
After that freeze should be gone.

---

### Post by ActionParsnip on 2021-10-19
If you disconnect your Brother device, does it run as normal? No lockups?

---

### Post by thealpman on 2021-10-20
Thanks for you answers.
I uninstalled my brother printer and the problem is still there (even 500 km from my printer :)).
I added the "nomodeset", it cures the freeze but the display is very slow, I can't properly use the computer anymore...
I tried to boot on an USB drive with 18.04.6, 20.04.2, 20.04.3, 21.04 and 21.10, it freezed every time.
I'm running out of ideas ! If you have more, they are very welcome.
How can I check if it's a hardware problem ?

---

### Post by thealpman on 2021-12-23
Hello,

The problem is finally solved by a change of RAM!
Apparently Corsair RAM (I had 2x 8GB DDR4) sometimes causes problems with Linux (when everything works fine with Windows).
It was changed by a company specialized in Linux which uses Crucial or Kingston.

As a reminder, I had found a workaround to launch a video in loop in VLC, strangely, it avoided the freezing.

Thanks to all for your help.

---

