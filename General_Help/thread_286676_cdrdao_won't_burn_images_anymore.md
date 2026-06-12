---
title: "cdrdao won't burn images anymore"
date: 2006-10-28
forum: General Help
---

### Post by GhettoPuNKkiD on 2006-10-28
After wasting about 4 CD-Rs to burn a BIN image (with cue sheet) with cdrdao (via the shell) I'm writing to the forums.

Here's what I'm getting:

```

erik@gumby:~/data$ sudo cdrdao write image.cue
Cdrdao version 1.2.1 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

/dev/cdrw: TSSTcorp CD/DVDW TS-L532U    Rev: GA03
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Starting write at speed 4...
Pausing 10 seconds - hit CTRL-C to abort.
Process can be aborted with QUIT signal (usually CTRL-\).
Turning BURN-Proof on
Executing power calibration...
Power calibration successful.
Writing track 01 (mode MODE2_RAW/MODE2_RAW )...
Writing track 02 (mode MODE2_RAW/MODE2_RAW )...
ERROR: Read error while reading data from file "/home/erik/data/image.bin": Input/output error
ERROR: Reading of track data failed.
ERROR: Reader process terminated abnormally.
ERROR: Writing failed.
erik@gumby:~/data$

```

It's worked before and I'm not sure what happened to make it stop working. :-| :evil: 

OH my fellow forum users. Pleaaase help. Using Dapper 6.06LTS. Thank you!

-Erik

---

### Post by cvmostert on 2006-11-11
i also had problems to write commandline... so i installed gnomebaker...

yes probably a little lame. but I dont want to look for the problem.

ciao

---

