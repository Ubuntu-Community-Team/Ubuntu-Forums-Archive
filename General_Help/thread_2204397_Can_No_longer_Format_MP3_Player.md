---
title: "Can No longer Format MP3 Player"
date: 2014-02-08
forum: General Help
---

### Post by daniell59 on 2014-02-08
I have formatted my MP3 players numerous times. I would right click on it, and that option would be available. For some reason, that option is no longer present. Presently, the only options available are eject and safely remove. Any suggestion on how I can recover that option would be appreciated.

Ubuntu 12.04 64

---

### Post by tgalati4 on 2014-02-08
There could be errors on it that the kernel detects.  Plug it in then open a terminal and look through:

```
dmesg | tail -50
```

Post any helpful messages.  It's possible that the flash memory has worn out.

---

### Post by daniell59 on 2014-02-08
> **tgalati4 said:**
> There could be errors on it that the kernel detects.  Plug it in then open a terminal and look through:

```
dmesg | tail -50
```

Post any helpful messages.  It's possible that the flash memory has worn out.

I have two identical MP3 players. It is the same with both.

Thanks for you input.

---

### Post by daniell59 on 2014-02-08
Updated post

---

### Post by daniell59 on 2014-02-08
daniel@daniel-P5Q-PRO:~$ daniel@daniel-P5Q-PRO:~$ dmesg | tail -50
daniel@daniel-P5Q-PRO:~$: command not found
daniel@daniel-P5Q-PRO:~$ [   58.375102] scsi7 : usb-storage 2-5:1.0
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.375016] scsi 7:0:0:0: Direct-Access     SanDisk  Sansa m250       v4.1 PQ: 0 ANSI: 0
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.375452] sd 7:0:0:0: Attached scsi generic sg7 type 0
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.379008] sd 7:0:0:0: [sdg] 3992576 512-byte logical blocks: (2.04 GB/1.90 GiB)
bash: syntax error near unexpected token `('
daniel@daniel-P5Q-PRO:~$ [   59.380012] sd 7:0:0:0: [sdg] Write Protect is off
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.380015] sd 7:0:0:0: [sdg] Mode Sense: 04 00 00 00
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.381005] sd 7:0:0:0: [sdg] No Caching mode page found
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.381009] sd 7:0:0:0: [sdg] Assuming drive cache: write through
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.389130] sd 7:0:0:0: [sdg] No Caching mode page found
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.389134] sd 7:0:0:0: [sdg] Assuming drive cache: write through
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.391767]  sdg:
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.399007] sd 7:0:0:0: [sdg] No Caching mode page found
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.399010] sd 7:0:0:0: [sdg] Assuming drive cache: write through
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   59.399013] sd 7:0:0:0: [sdg] Attached SCSI removable disk
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [   67.531904] WARNING! power/level is deprecated; use power/control instead
bash: [: missing `]'
No command 'use' found, did you mean:
 Command 'nse' from package 'ns2' (universe)
 Command 'muse' from package 'muse' (universe)
 Command 'uae' from package 'uae' (multiverse)
 Command 'fuse' from package 'fuse-emulator-sdl' (universe)
 Command 'fuse' from package 'fuse-emulator-gtk' (universe)
use: command not found
daniel@daniel-P5Q-PRO:~$ [   67.608040] usb 2-5: USB disconnect, device number 5bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  115.968026] hub 2-0:1.0: unable to enumerate USB device on port 5
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  116.280013] usb 2-5: new high-speed USB device number 7 using ehci_hcd
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  116.430989] scsi8 : usb-storage 2-5:1.0
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.430902] scsi 8:0:0:0: Direct-Access     SanDisk  Sansa m250       v4.1 PQ: 0 ANSI: 0
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.431454] sd 8:0:0:0: Attached scsi generic sg7 type 0
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.435520] sd 8:0:0:0: [sdg] 3992576 512-byte logical blocks: (2.04 GB/1.90 GiB)
bash: syntax error near unexpected token `('
daniel@daniel-P5Q-PRO:~$ [  117.436517] sd 8:0:0:0: [sdg] Write Protect is off
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.436521] sd 8:0:0:0: [sdg] Mode Sense: 04 00 00 00
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.437517] sd 8:0:0:0: [sdg] No Caching mode page found
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.437520] sd 8:0:0:0: [sdg] Assuming drive cache: write through
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.445017] sd 8:0:0:0: [sdg] No Caching mode page found
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.445021] sd 8:0:0:0: [sdg] Assuming drive cache: write through
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.447529]  sdg:
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.454269] sd 8:0:0:0: [sdg] No Caching mode page found
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.454273] sd 8:0:0:0: [sdg] Assuming drive cache: write through
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  117.454276] sd 8:0:0:0: [sdg] Attached SCSI removable disk
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [  123.272038] usb 2-5: USB disconnect, device number 7bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7991.840032] hub 2-0:1.0: unable to enumerate USB device on port 5
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7992.140017] usb 2-5: new high-speed USB device number 9 using ehci_hcd
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7992.291536] scsi9 : usb-storage 2-5:1.0
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.291463] scsi 9:0:0:0: Direct-Access     SanDisk  Sansa m250       v4.1 PQ: 0 ANSI: 0
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.292227] sd 9:0:0:0: Attached scsi generic sg7 type 0
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.295576] sd 9:0:0:0: [sdg] 3992576 512-byte logical blocks: (2.04 GB/1.90 GiB)
bash: syntax error near unexpected token `('
daniel@daniel-P5Q-PRO:~$ [ 7993.296572] sd 9:0:0:0: [sdg] Write Protect is off
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.296575] sd 9:0:0:0: [sdg] Mode Sense: 04 00 00 00
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.297572] sd 9:0:0:0: [sdg] No Caching mode page found
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.297575] sd 9:0:0:0: [sdg] Assuming drive cache: write through
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.305445] sd 9:0:0:0: [sdg] No Caching mode page found
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.305449] sd 9:0:0:0: [sdg] Assuming drive cache: write through
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.307958]  sdg:
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.315321] sd 9:0:0:0: [sdg] No Caching mode page found
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.315324] sd 9:0:0:0: [sdg] Assuming drive cache: write through
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 7993.315327] sd 9:0:0:0: [sdg] Attached SCSI removable disk
bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ [ 8413.380028] usb 2-5: USB disconnect, device number 9bash: [: missing `]'
daniel@daniel-P5Q-PRO:~$ daniel@daniel-P5Q-PRO:~$ 
daniel@daniel-P5Q-PRO:~$: command not found
daniel@daniel-P5Q-PRO:~$

---

### Post by tgalati4 on 2014-02-09
Are you right-clicking an icon on the desktop or inside a file manager?  What file manager are you using?  Dmesg is not showing any flash disk read errors.  You might perform an fsck on both drives--but only after you unmount them but leave them connected to USB.  Did you perform any updates lately?

---

### Post by daniell59 on 2014-02-09
> **tgalati4 said:**
> Are you right-clicking an icon on the desktop or inside a file manager?  What file manager are you using?  Dmesg is not showing any flash disk read errors.  You might perform an fsck on both drives--but only after you unmount them but leave them connected to USB.  Did you perform any updates lately?

I am right clicking on the icon in the launcher.
I have been performing updates on almost a daily basis. That is whenever they are available.

---

### Post by tgalati4 on 2014-02-09
File a bug with the Unity Desktop and do a search to see if others are having  a similar issue.

---

### Post by daniell59 on 2014-02-10
> **tgalati4 said:**
> File a bug with the Unity Desktop and do a search to see if others are having  a similar issue.

I filed a bug report. An automated response indicated that I did not mention the package source. I do not know what it is.

---

### Post by tgalati4 on 2014-02-10
What source code do you feel the bug is contained in?  Yes, I know, if you are not a developer, then it would be difficult to answer this.

I would suspect this:  libunity-core-6.0-5 - Core library for the Unity interface.

Then let the developers kick it around.  Since it is repeatable with 2 mp3 players, the devs may take a look at it.  Otherwise, others would have to observe the same behavior, and comment on the bug for it to get triaged to a higher level.

Include the word *regression* in your description, since it worked previously and now it is not working, presumably after some recent updates.

---

