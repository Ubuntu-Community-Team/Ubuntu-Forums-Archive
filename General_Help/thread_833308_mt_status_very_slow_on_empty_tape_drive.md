---
title: "mt status very slow on empty tape drive"
date: 2008-06-18
forum: General Help
---

### Post by mathog on 2008-06-18
Yesterday a server was upgraded from 7.04 to 8.04.  Afterwards I noticed that the tape drive was very slow to answer when empty:

% mt -f /dev/nst0 status
mt: /dev/nst0: rmtopen failed: No medium found

this took two minutes.  Put a cartridge in it and it comes back in a second or two.  I had not tested this previously on an empty drive, but on a Mandriva system the same command comes back instantly (different tape drive though, a Quantum SDLT320).

The tape drive on the Ubuntu system is an HP StorageWorks Ultrium 920 Tape Drive (Ultrium III) and the scsi adapter is an Adaptec ASC-29320ALP U320.

% uname -a
Linux Mascot-Server 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux

Is this a tape drive issue or some problem with mt on Ubuntu?

Thanks,

David Mathog

---

### Post by mathog on 2008-06-19
> **mathog said:**
> 
% mt -f /dev/nst0 status
mt: /dev/nst0: rmtopen failed: No medium found


The problem was that Ubuntu by default loads Gnu mt.  Kai
Makisara's mt does not have this long delay.  To install that do:

% apt-get install mt-st

and then, under the same circumstances (cartridge ejected
but not yet removed)

% mt -f /dev/nst0 status

comes back instantly with:

SCSI 2 tape drive:
File number=-1, block number=-1, partition=0.
Tape block size 0 bytes. Density code 0x0 (default).
Soft error count since last status=0
General status bits on (4050000):
 WR_PROT DR_OPEN IM_REP_EN

One might quibble with the "SCSI 2" part, as this is a U320
drive and controller, but the rest of the information is correct.

Regards,

David Mathog

---

