---
title: "Totem thrasing dvd-r?"
date: 2007-02-20
forum: General Help
---

### Post by darkali on 2007-02-20
I have some movie backups and when I pop them into Ubuntu, totem starts plays for less than 30 seconds then spits a message about libdvdcss (which I have installed), then when I try to play it again the disc simply doesn´t work anymore, even in the hardware dvd I have.

I took my five dvd-rs to notice this was happening, but I still don´t know how to solve it,
the discs were working before but now they aren´t, when looked in the system logs I saw a strange log being repeated over and over.
Here´s the message:

> 19-02-2007 23:04:21	localhost	kernel	[17179755.688000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
19-02-2007 23:04:21	localhost	kernel	[17179755.688000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
19-02-2007 23:04:21	localhost	kernel	[17179755.688000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
19-02-2007 23:04:21	localhost	kernel	[17179755.688000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
19-02-2007 23:04:21	localhost	kernel	[17179755.688000] end_request: I/O error, dev hdc, sector 42396
19-02-2007 23:04:21	localhost	kernel	[17179755.688000] end_request: I/O error, dev hdc, sector 42392
19-02-2007 23:04:21	localhost	kernel	[17179755.680000] ide: failed opcode was: unknown
19-02-2007 23:04:21	localhost	kernel	[17179755.680000] ide: failed opcode was: unknown

The log I saved is about 102kb and 95% of it is this message repeated.

Any help appreciated.

---

