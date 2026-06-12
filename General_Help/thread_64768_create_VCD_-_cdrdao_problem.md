---
title: "create VCD - cdrdao problem"
date: 2005-09-12
forum: General Help
---

### Post by RikoW on 2005-09-12
Dear all,

I try to create a VCD from an mpeg file I have. I create the .bin and .cure files using tovid. I try to burn the image using cdrdao, however always fail with a write error:

```

> sudo cdrdao write --device /dev/hdc --driver generic-mmc Jans_VCD.xml.cue
Password:
Cdrdao version 1.1.9 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Using libscg version 'schily-0.8'

/dev/hdc: HL-DT-ST RW/DVD GCC-4241N     Rev: A100
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Burning entire 79 mins disc.
Starting write at speed 10...
Pausing 10 seconds - hit CTRL-C to abort.
Process can be aborted with QUIT signal (usually CTRL-\).
Turning BURN-Proof on
Executing power calibration...
Power calibration successful.
cdrdao: Success.  : scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 60736
cmd finished after 0.002s timeout 180s
ERROR: Write data failed.
ERROR: Writing failed.
>

```
 checked that the permissions are set on the /dev/hdc, even though I run cdrdao as root.

Burning in principle works, because k3b burns cds just fine. Any ideas, what I'm missing?

Thanks,
             Riko


Edit:

I just realized, that I can burn VCD also directly via k3b. However, also that doesn't work. I get an 'unknown error 254' from cdrecord. Data, audio CDs or iso images burn just fine, though.

Also, feeding k3b with the image file of the VCD directly causes the 254 error.

I'm completely confused. Is there something special about a VCD that cause the burning engines to fail? Do a need a specail CD type? I tried both CD-RW and CD-R ...

---

