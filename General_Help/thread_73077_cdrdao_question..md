---
title: "cdrdao question."
date: 2005-10-08
forum: General Help
---

### Post by xmastree on 2005-10-08
I have a mpg file from which I'd like to make a vcd. So far I've used **mkvcdfs** to create the vcd.toc and vcd_image.bin files, that seemed to work without any problem.
However, when I try to burn the disc, It fails:

```
chris@ubuntu:/mnt/shared/video$ sudo cdrdao write --device /dev/hdd vcd.toc
Cdrdao version 1.1.9 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'schily-0.8'

/dev/hdd: LITE-ON DVDRW SOHW-1653S      Rev: CS09
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Burning entire 79 mins disc.
Starting write at speed 48...
Pausing 10 seconds - hit CTRL-C to abort.
Process can be aborted with QUIT signal (usually CTRL-\).
Turning BURN-Proof on
Enabling JustSpeed.
Executing power calibration...
Power calibration successful.
ERROR: Drive does not accept any cue sheet variant - please report.
ERROR: Writing failed.
```
I've managed to erase a CDRW using it, so it partially works.

I sudid it because I got an error```
WARNING: No super user permission to setup real time scheduling.
```otherwise.

Any ideas?

---

### Post by xmastree on 2005-10-08
So, looking around I discovered **vcdimager** which apparently can make an ISO file, and I can just burn that from nautilus.
Except whatever switches I try, **-l** should be the right one I think, I end up with a .CUE and .BIN which need to be burned with cdrdao.

---

