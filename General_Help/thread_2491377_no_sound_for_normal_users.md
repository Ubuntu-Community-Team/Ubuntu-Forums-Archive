---
title: "no sound for normal users"
date: 2023-10-06
forum: General Help
---

### Post by uwe3 on 2023-10-06
[COLOR=#000000][FONT=&amp]# pbl: no sound for normal users [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]# my findings so far:[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# check OS version[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ lsb_release -a[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]No LSB modules are available.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Distributor ID:[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Description:[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Ubuntu 22.04.3 LTS[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Release:[/FONT][/COLOR][COLOR=#000000][FONT=&amp]22.04[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Codename:[/FONT][/COLOR][COLOR=#000000][FONT=&amp]jammy[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]### select the right sound output[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]There is only one. The internal sound ...[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# check for audio device[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ lspci -v [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]00:1f.3 Audio device: Intel Corporation Alder Lake PCH-P High Definition Audio Controller (rev 01) (prog-if 80)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]DeviceName: Onboard - Sound[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Subsystem: Tongfang Hongkong Limited Device 1173[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Flags: bus master, fast devsel, latency 32, IRQ 191, IOMMU group 14[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Memory at 612d188000 (64-bit, non-prefetchable) [size=16K][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Memory at 612d000000 (64-bit, non-prefetchable) [size=1M][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Capabilities: <access denied>[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Kernel driver in use: snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# find a sound file for the tests[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:/usr/share$ find /usr/share/sounds/alsa -name "*.wav"[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/usr/share/sounds/alsa/Front_Left.wav[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/usr/share/sounds/alsa/Side_Left.wav[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/usr/share/sounds/alsa/Front_Right.wav[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/usr/share/sounds/alsa/Noise.wav[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/usr/share/sounds/alsa/Side_Right.wav[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/usr/share/sounds/alsa/Rear_Center.wav[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/usr/share/sounds/alsa/Rear_Right.wav[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/usr/share/sounds/alsa/Front_Center.wav[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/usr/share/sounds/alsa/Rear_Left.wav[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# :-( no sound with [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ aplay /usr/share/sounds/alsa/Front_Center.wav[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# :-) sound ok with[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ sudo aplay /usr/share/sounds/alsa/Front_Center.wav[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# uwe is in group audio![/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ groups uwe[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe : uwe adm cdrom sudo audio dip plugdev lpadmin sambashare lxd[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# check access rights for /dev/snd[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ ls /dev -la | grep snd[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]drwxr-xr-x   3 root root             280 Okt  5 17:52 snd[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# change ownership [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ sudo chown root:audio /dev/snd[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# :D successful test with [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ aplay /usr/share/sounds/alsa/Front_Center.wav[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# a restart will change the ownership back to  ### ??? ###[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ ls -ls /dev | grep snd[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]0 drwxr-xr-x   3 root root             280 Okt  6 09:47 snd[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# again a manually change of ownership [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ sudo chown root:audio /dev/snd[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# but now NO success with [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]uwe@tux2:~$ aplay /usr/share/sounds/alsa/Front_Center.wav[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]# ???[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@tux2:/dev/snd# ls -la[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]insgesamt 0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]drwxr-xr-x   3 root audio     280 Okt  6 09:47 .[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]drwxr-xr-x  23 root root     5480 Okt  6 09:47 ..[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]drwxr-xr-x   2 root root       60 Okt  6 09:47 by-path[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116, 10 Okt  6 09:47 controlC0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116,  8 Okt  6 09:47 hwC0D0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116,  9 Okt  6 09:47 hwC0D2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116,  3 Okt  6 09:47 pcmC0D0c[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116,  2 Okt  6 09:56 pcmC0D0p[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116,  4 Okt  6 09:47 pcmC0D3p[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116,  5 Okt  6 09:47 pcmC0D7p[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116,  6 Okt  6 09:47 pcmC0D8p[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116,  7 Okt  6 09:47 pcmC0D9p[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116,  1 Okt  6 09:47 seq[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]crw-rw----+  1 root audio 116, 33 Okt  6 09:47 timer[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
# if I chage the ownership of by-pass to root:audio, aplay works again. But no sound via the sound test via settings.[/FONT][/COLOR]

---

