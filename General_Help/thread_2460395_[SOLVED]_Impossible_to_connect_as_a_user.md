---
title: "[SOLVED] Impossible to connect as a user"
date: 2021-04-09
forum: General Help
---

### Post by thealpman on 2021-04-09
Hello everyone,

I had a big problem, my screen was freezing all the time (a quick black glitch on the screen and then freezing) and I had to turn it off with the power button. Si I reinstalled the system from scratch :

[[IMG]https://i.ibb.co/fX3zdwS/IMG-20210408-132640.jpg[/IMG]]("https://ibb.co/fX3zdwS") [[IMG]https://i.ibb.co/QNCbz28/IMG-20210408-132655.jpg[/IMG]]("https://ibb.co/QNCbz28") [[IMG]https://i.ibb.co/HnYTydV/IMG-20210408-132813.jpg[/IMG]]("https://ibb.co/HnYTydV")

I had even freezing problems during the live session ! And the restart after the brand new installation froze also.

Here are the errors messages I got :

[[IMG]https://i.ibb.co/HHqsjCL/2021-04-09-09-44.png[/IMG]]("https://ibb.co/HHqsjCL") [[IMG]https://i.ibb.co/L1DgDCt/2021-04-09-09-45.png[/IMG]]("https://ibb.co/L1DgDCt") [[IMG]https://i.ibb.co/mSN1j2d/2021-04-09-09-45-1.png[/IMG]]("https://ibb.co/mSN1j2d")

The logs from my last start (freezing on the purple log in screen) :
```

jr@jr-ubuntu:~$ journalctl --no-pager --since yesterday -p err
-- Reboot --
avril 09 10:06:09 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 09 10:06:09 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 09 10:06:09 jr-ubuntu kernel: i915 0000:00:02.0: [drm] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 09 10:06:09 jr-ubuntu systemd-udevd[577]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 09 10:06:09 jr-ubuntu systemd-udevd[577]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
-- Reboot --
```

I see my graphics card i915 mentioned here and there.

Any idea ?
Thank you !

---

### Post by ActionParsnip on 2021-04-09
I suggest you test your RAM health as a good first step. Also check settings in BIOS and make sure that is up to date too

---

### Post by thealpman on 2021-04-12
Hello,

Thank you for your reply, ActionParsnip. I fully tested the RAM with a bootable memtest86 key, no error.

The problem was (almost completely)  solved by installing linux-generic (French forum thread : [https://forum.ubuntu-fr.org/viewtopic.php?pid=22413714#p22413714](https://forum.ubuntu-fr.org/viewtopic.php?pid=22413714#p22413714)) :
```
sudo apt install --install-recommends linux-generic
```

I now start on kernel 5.4 and deleted kernel 5.8

```
jr@jr-ubuntu:~$ uname -a 
Linux jr-ubuntu 5.4.0-70-generic #78-Ubuntu SMP Fri Mar 19 13:29:52 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
jr@jr-ubuntu:~$ 
```

I still have problems with the sleep mode though, whatever the way : systemctl suspend, power button, Fn+F12, or the menu in the upper right corner. It rarely works, usually the computer freezes and sometimes it restarts !

Any idea ?

Thank you !

My error log :
```
jr@jr-ubuntu:~$ journalctl --no-pager --since yesterday -p err
avril 12 12:10:39 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 12 12:10:39 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 12 12:10:39 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 12 12:10:39 jr-ubuntu systemd-udevd[652]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 12 12:10:39 jr-ubuntu systemd-udevd[652]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 12 12:10:41 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 12 12:10:41 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
-- Reboot --
avril 12 12:17:55 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 12 12:17:55 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 12 12:17:55 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 12 12:17:55 jr-ubuntu kernel: [drm:intel_dp_aux_xfer [i915]] *ERROR* dp aux hw did not signal timeout!
avril 12 12:17:55 jr-ubuntu kernel: [drm:intel_dp_aux_xfer [i915]] *ERROR* dp aux hw did not signal timeout!
avril 12 12:17:55 jr-ubuntu systemd-udevd[655]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 12 12:17:55 jr-ubuntu systemd-udevd[655]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 12 12:17:56 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 12 12:17:57 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 12 12:19:01 jr-ubuntu gdm-password][1941]: gkr-pam: unable to locate daemon control file
avril 12 12:19:25 jr-ubuntu nm-openvpn[2586]: write UDP: Network is unreachable (code=101)
avril 12 12:19:37 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 12 12:20:54 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 12 12:21:21 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
-- Reboot --
avril 12 12:23:09 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 12 12:23:09 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 12 12:23:09 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 12 12:23:09 jr-ubuntu kernel: [drm:intel_dp_aux_xfer [i915]] *ERROR* dp aux hw did not signal timeout!
avril 12 12:23:09 jr-ubuntu kernel: [drm:intel_dp_aux_xfer [i915]] *ERROR* dp aux hw did not signal timeout!
avril 12 12:23:09 jr-ubuntu systemd-udevd[653]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 12 12:23:09 jr-ubuntu systemd-udevd[653]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 12 12:23:10 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 12 12:23:11 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 12 12:23:23 jr-ubuntu gdm-password][1877]: gkr-pam: unable to locate daemon control file
-- Reboot --
avril 12 12:26:40 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 12 12:26:40 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 12 12:26:40 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 12 12:26:40 jr-ubuntu systemd-udevd[655]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 12 12:26:40 jr-ubuntu systemd-udevd[655]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 12 12:26:41 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 12 12:26:42 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 12 12:26:48 jr-ubuntu gdm-password][1798]: gkr-pam: unable to locate daemon control file
-- Reboot --
avril 12 12:41:47 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 12 12:41:47 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 12 12:41:47 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
-- Reboot --
avril 12 12:44:18 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 12 12:44:18 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 12 12:44:18 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 12 12:44:18 jr-ubuntu kernel: [drm:intel_dp_aux_xfer [i915]] *ERROR* dp aux hw did not signal timeout!
avril 12 12:44:18 jr-ubuntu systemd-udevd[657]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 12 12:44:18 jr-ubuntu systemd-udevd[657]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 12 12:44:20 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 12 12:44:20 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 12 12:44:45 jr-ubuntu gdm-password][1905]: gkr-pam: unable to locate daemon control file
avril 12 12:46:20 jr-ubuntu gdm3[1236]: Failed to contact accountsservice: Erreur lors de l&#8217;appel de StartServiceByName pour org.freedesktop.Accounts : Refusing activation, D-Bus is shutting down.
avril 12 12:46:21 jr-ubuntu pulseaudio[4361]: GetManagedObjects() failed: org.freedesktop.systemd1.ShuttingDown: Refusing activation, D-Bus is shutting down.
avril 12 12:46:21 jr-ubuntu nm-openvpn[2556]: event_wait : Interrupted system call (code=4)
avril 12 12:46:21 jr-ubuntu nm-openvpn[2556]: write UDP: Network is unreachable (code=101)
avril 12 12:46:22 jr-ubuntu systemd-cryptsetup[4389]: Device sda3_crypt is still in use.
avril 12 12:46:22 jr-ubuntu systemd-cryptsetup[4389]: Failed to deactivate: Device or resource busy
avril 12 12:46:23 jr-ubuntu kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.LPCB.EC._Q61.P80H], AE_NOT_FOUND (20190816/psargs-330)
avril 12 12:46:23 jr-ubuntu kernel: ACPI Error: Aborting method \_SB.PCI0.LPCB.EC._Q61 due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
-- Reboot --
avril 12 12:48:48 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 12 12:48:48 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 12 12:48:48 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 12 12:48:48 jr-ubuntu systemd-udevd[653]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 12 12:48:48 jr-ubuntu systemd-udevd[653]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 12 12:48:50 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 12 12:48:50 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 12 12:48:57 jr-ubuntu gdm-password][1760]: gkr-pam: unable to locate daemon control file
avril 12 12:49:04 jr-ubuntu gnome-session-binary[1312]: CRITICAL: We failed, but the fail whale is dead. Sorry....
avril 12 12:49:39 jr-ubuntu nm-openvpn[2542]: write UDP: Network is unreachable (code=101)
avril 12 12:49:52 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
-- Reboot --
avril 12 12:51:20 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 12 12:51:20 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 12 12:51:20 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 12 12:51:20 jr-ubuntu systemd-udevd[655]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 12 12:51:20 jr-ubuntu systemd-udevd[655]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 12 12:51:22 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 12 12:51:22 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
-- Reboot --
avril 12 12:54:09 jr-ubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
avril 12 12:54:09 jr-ubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
avril 12 12:54:09 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 12 12:54:09 jr-ubuntu systemd-udevd[653]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 12 12:54:09 jr-ubuntu systemd-udevd[653]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 12 12:54:10 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 12 12:54:11 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 12 12:54:20 jr-ubuntu gdm-password][1779]: gkr-pam: unable to locate daemon control file
-- Reboot --
```

---

### Post by CelticWarrior on 2021-04-12
If you don't need TPM (eventually for Windows in dual-boot) then please disable it in UEFI.
Also disable Secure Boot as it prevents the unsigned Virtualbox drivers from loading.

And, of course, update UEFI as suggested above.

---

### Post by thealpman on 2021-04-12
Thank you for your answer CelticWarrior.
I don't really know it I need TPM. I only have Ubuntu on this computer (which is a couple months old.), with 1 encrypted partition (LUKS) for system and data. Can I disable it ?
Do you have a link to a procedure to update my UEFI ?
Thanks again

---

### Post by CelticWarrior on 2021-04-12
Yes, with only Ubuntu you can and should disable it. It's a known source of several problems. More info at [https://askubuntu.com/a/414755](https://askubuntu.com/a/414755)

Regarding the UEFI ("BIOS") update pleased check with the manufacturer.

---

### Post by thealpman on 2021-04-15
Hello,

Thank you CelticWarrior.

I don't find any update of the UEFI for my computer (Clevo NL4x_NL5xLU).

During an update, the system installed version 5.4.0.71 and problems came again !
Si I desinstalled it to only leave 5.4.0.70. I still have problems, especially with my HDMI projector, sometimes the screen freezes again.
Sometimes also the system won't restart and give a "No response from codec" message (VLC was working or had been working shortly before)

I don't understand, the machine was working fine a couple week and is fairly recent (~3 months).

Thank you in advance for your help


```

jr@jr-ubuntu:~$ journalctl --no-pager -p err
-- Reboot --
avril 14 18:14:53 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 14 18:14:53 jr-ubuntu systemd-udevd[671]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 14 18:14:53 jr-ubuntu systemd-udevd[671]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 14 18:14:55 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 14 18:14:56 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 14 18:15:01 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x202f8100
avril 14 18:15:02 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x202f8100
avril 14 18:15:03 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20170500
avril 14 18:15:04 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20370500
avril 14 18:15:04 jr-ubuntu gdm-password][1808]: gkr-pam: unable to locate daemon control file
avril 14 18:15:05 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20470500
avril 14 18:15:06 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20570500
avril 14 18:15:07 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20670500
avril 14 18:15:08 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20770500
avril 14 18:15:09 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20870500
avril 14 18:15:10 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20970500
avril 14 18:15:11 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20a70500
avril 14 18:15:12 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20b70500
avril 14 18:15:13 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x201f0500
avril 14 18:15:14 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x202f8100
avril 14 18:15:15 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x202f8100
avril 14 18:15:16 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20170500
avril 14 18:15:17 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20370500
avril 14 18:15:18 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20470500
avril 14 18:15:19 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20570500
avril 14 18:15:20 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20670500
avril 14 18:15:21 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20770500
avril 14 18:15:22 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20870500
avril 14 18:15:23 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20970500
avril 14 18:15:24 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20a70500
avril 14 18:15:25 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20b70500
avril 14 18:15:26 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x201f0500
avril 14 18:15:27 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x202f8100
avril 14 18:15:28 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x202f8100
avril 14 18:15:29 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20170500
avril 14 18:15:30 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20370500
avril 14 18:15:31 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20470500
avril 14 18:15:33 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20570500
avril 14 18:15:34 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20670500
avril 14 18:15:35 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20770500
avril 14 18:15:36 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20870500
avril 14 18:15:37 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20970500
avril 14 18:15:38 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20a70500
avril 14 18:15:39 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20b70500
avril 14 18:15:40 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x201f0500
avril 14 18:15:41 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x202f8100
avril 14 18:15:42 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x202f8100
avril 14 18:15:43 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20170500
avril 14 18:15:44 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20370500
avril 14 18:15:45 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20470500
avril 14 18:15:46 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20570500
avril 14 18:15:47 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20670500
avril 14 18:15:47 jr-ubuntu gdm3[1263]: Failed to contact accountsservice: Erreur lors de l’appel de StartServiceByName pour org.freedesktop.Accounts : Refusing activation, D-Bus is shutting down.
avril 14 18:15:48 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20770500
avril 14 18:15:49 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20870500
avril 14 18:15:49 jr-ubuntu kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.LPCB.EC._Q61.P80H], AE_NOT_FOUND (20190816/psargs-330)
avril 14 18:15:49 jr-ubuntu kernel: ACPI Error: Aborting method \_SB.PCI0.LPCB.EC._Q61 due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
avril 14 18:15:50 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20970500
avril 14 18:15:51 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20a70500
avril 14 18:15:52 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x20b70500
avril 14 18:15:53 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x201f0500
avril 14 18:15:53 jr-ubuntu nm-openvpn[2641]: event_wait : Interrupted system call (code=4)
avril 14 18:15:53 jr-ubuntu nm-openvpn[2641]: write UDP: Network is unreachable (code=101)
avril 14 18:15:53 jr-ubuntu systemd-cryptsetup[2969]: Device sda3_crypt is still in use.
avril 14 18:15:53 jr-ubuntu systemd-cryptsetup[2969]: Failed to deactivate: Device or resource busy
avril 14 18:15:54 jr-ubuntu kernel: snd_hda_intel 0000:00:1f.3: No response from codec, resetting bus: last cmd=0x202f8100
-- Reboot --
avril 14 18:17:05 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 14 18:17:05 jr-ubuntu systemd-udevd[669]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 14 18:17:05 jr-ubuntu systemd-udevd[669]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 14 18:17:07 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 14 18:17:08 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 14 18:17:17 jr-ubuntu gdm-password][1813]: gkr-pam: unable to locate daemon control file
avril 14 18:17:24 jr-ubuntu gnome-session-binary[1337]: GLib-GIO-CRITICAL: g_dbus_connection_emit_signal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed
avril 14 18:17:24 jr-ubuntu gnome-session-binary[1337]: CRITICAL: gsm_client_peek_id: assertion 'GSM_IS_CLIENT (client)' failed
avril 14 18:17:24 jr-ubuntu gnome-session-binary[1337]: GLib-CRITICAL: g_hash_table_find: assertion 'version == hash_table->version' failed
avril 14 18:17:24 jr-ubuntu gnome-session-binary[1337]: CRITICAL: We failed, but the fail whale is dead. Sorry....
avril 14 18:18:58 jr-ubuntu gdm3[1267]: Failed to contact accountsservice: Erreur lors de l’appel de StartServiceByName pour org.freedesktop.Accounts : Refusing activation, D-Bus is shutting down.
avril 14 18:19:00 jr-ubuntu systemd-cryptsetup[4449]: Device sda3_crypt is still in use.
avril 14 18:19:00 jr-ubuntu systemd-cryptsetup[4449]: Failed to deactivate: Device or resource busy
-- Reboot --
avril 14 18:20:17 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 14 18:20:17 jr-ubuntu systemd-udevd[670]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 14 18:20:17 jr-ubuntu systemd-udevd[670]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 14 18:20:20 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 14 18:20:20 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 14 18:20:27 jr-ubuntu gdm-password][1809]: gkr-pam: unable to locate daemon control file
avril 14 20:46:59 jr-ubuntu nm-openvpn[2561]: event_wait : Interrupted system call (code=4)
avril 14 20:49:51 jr-ubuntu kernel: iwlwifi 0000:02:00.0: Unhandled alg: 0x707
avril 14 21:17:31 jr-ubuntu bluetoothd[1131]: Start: Connection timed out (110)
avril 14 21:17:31 jr-ubuntu pulseaudio[1929]: Transport Acquire() failed for transport /org/bluez/hci0/dev_B8_69_C2_78_8D_71/sep1/fd0 (Input/output error)
avril 14 21:17:33 jr-ubuntu bluetoothd[1131]: Abort: Connection timed out (110)
avril 14 21:17:43 jr-ubuntu bluetoothd[1131]: Unable to get io data for Headset Voice gateway: getpeername: Transport endpoint is not connected (107)
-- Reboot --
avril 14 22:03:29 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 14 22:03:29 jr-ubuntu systemd-udevd[655]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 14 22:03:29 jr-ubuntu systemd-udevd[655]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 14 22:03:31 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 14 22:03:32 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 14 22:03:40 jr-ubuntu gdm-password][1805]: gkr-pam: unable to locate daemon control file
avril 14 22:28:03 jr-ubuntu gdm3[1250]: Failed to contact accountsservice: Erreur lors de l’appel de StartServiceByName pour org.freedesktop.Accounts : Refusing activation, D-Bus is shutting down.
avril 14 22:28:03 jr-ubuntu pulseaudio[4487]: GetManagedObjects() failed: org.freedesktop.systemd1.ShuttingDown: Refusing activation, D-Bus is shutting down.
avril 14 22:28:04 jr-ubuntu nm-openvpn[2536]: event_wait : Interrupted system call (code=4)
avril 14 22:28:05 jr-ubuntu kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.LPCB.EC._Q61.P80H], AE_NOT_FOUND (20190816/psargs-330)
avril 14 22:28:05 jr-ubuntu kernel: ACPI Error: Aborting method \_SB.PCI0.LPCB.EC._Q61 due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
avril 14 22:28:05 jr-ubuntu systemd-cryptsetup[4566]: Device sda3_crypt is still in use.
avril 14 22:28:05 jr-ubuntu systemd-cryptsetup[4566]: Failed to deactivate: Device or resource busy
-- Reboot --
avril 15 07:51:09 jr-ubuntu kernel: [drm:tc_port_live_status_mask [i915]] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
avril 15 07:51:09 jr-ubuntu systemd-udevd[654]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
avril 15 07:51:09 jr-ubuntu systemd-udevd[654]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
avril 15 07:51:11 jr-ubuntu systemd[1]: Failed to start VirtualBox Web Service.
avril 15 07:51:11 jr-ubuntu kernel: iwlwifi 0000:02:00.0: BIOS contains WGDS but no WRDS
avril 15 07:51:37 jr-ubuntu gdm-password][1926]: gkr-pam: unable to locate daemon control file
avril 15 10:24:01 jr-ubuntu kernel: pcieport 0000:00:1d.0: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)
avril 15 10:24:01 jr-ubuntu kernel: pcieport 0000:00:1d.0: AER:   device [8086:34b0] error status/mask=00001000/00002000
avril 15 10:24:01 jr-ubuntu kernel: pcieport 0000:00:1d.0: AER:    [12] Timeout               
avril 15 10:28:43 jr-ubuntu kernel: pcieport 0000:00:1d.0: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)
avril 15 10:28:43 jr-ubuntu kernel: pcieport 0000:00:1d.0: AER:   device [8086:34b0] error status/mask=00001000/00002000
avril 15 10:28:43 jr-ubuntu kernel: pcieport 0000:00:1d.0: AER:    [12] Timeout               
jr@jr-ubuntu:~$ 

```

---

### Post by thealpman on 2021-04-19
In this post ([https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1894881](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1894881)), they suggest to revert to 5.8.0-48-generic.
I didn't quite find it and it's a sensitive matter, can someone give me the command to do it ?

Does someone have another idea ?

Thank you

---

### Post by thealpman on 2021-12-23
Hello,

The problem is finally solved by a change of RAM!
Apparently Corsair RAM (I had 2x 8GB DDR4) sometimes causes problems with Linux (when everything works fine with Windows).
It was changed by a company specialized in Linux which uses Crucial or Kingston.

As a reminder, I had found a workaround to launch a video in loop in VLC, strangely, it avoided the freezing.

Thanks to all for your help.

---

