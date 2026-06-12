---
title: "More about ATi... I discovered something wrong (I think)"
date: 2006-10-29
forum: General Help
---

### Post by Amt0571 on 2006-10-29
As I've explained in other post, both the fglrx and the ati driver are crashing on my machine. After looking for a while in KSystemLog, I have found out some strange lines that reference some type of memory error:

```
29/10/06 11:23:49	SGP3	kdm_greet[4158]	Internal error: memory corruption detected

29/10/06 11:23:52	SGP3	kernel	[17179634.512000]  0:0:0:0: Attempting to queue an ABORT message

29/10/06 11:23:52	SGP3	kernel	[17179634.512000]  0:0:0:0: Command already completed

29/10/06 11:23:52	SGP3	kernel	[17179634.512000]  0:0:0:0: scsi: Device offlined - not ready after error recovery

29/10/06 11:23:52	SGP3	kernel	[17179634.512000] aic7xxx_abort returns 0x2002

29/10/06 11:23:52	SGP3	kernel	[17179634.512000] CDB: 0x0 0x0 0x0 0x0 0x0 0x0

29/10/06 11:23:57	SGP3	kernel	[17179640.012000]  0:0:1:0: Attempting to queue an ABORT message

29/10/06 11:23:57	SGP3	kernel	[17179640.012000]  0:0:1:0: Command already completed

29/10/06 11:23:57	SGP3	kernel	[17179640.012000] aic7xxx_abort returns 0x2002

29/10/06 11:23:57	SGP3	kernel	[17179640.012000] CDB: 0x12 0x0 0x0 0x0 0x24 0x0

29/10/06 11:24:07	SGP3	hcid[4257]	Default passkey agent (:1.3, /org/bluez/passkey_agent_4544) registered

29/10/06 11:24:07	SGP3	hcid[4257]	name_listener_add(:1.3)

29/10/06 11:24:07	SGP3	kernel	[17179650.012000]  0:0:1:0: Attempting to queue an ABORT message

29/10/06 11:24:07	SGP3	kernel	[17179650.012000]  0:0:1:0: Attempting to queue a TARGET RESET message

29/10/06 11:24:07	SGP3	kernel	[17179650.012000]  0:0:1:0: Command already completed

29/10/06 11:24:07	SGP3	kernel	[17179650.012000]  0:0:1:0: Command not found

29/10/06 11:24:07	SGP3	kernel	[17179650.012000] aic7xxx_abort returns 0x2002

29/10/06 11:24:07	SGP3	kernel	[17179650.012000] aic7xxx_dev_reset returns 0x2002
```

And this goes on and on for a lot of lines in the log. Then, just after the memory corruption error on the log I have found this other lines:


```
29/10/06 11:29:05	SGP3	kernel	[17179620.752000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.

29/10/06 11:29:05	SGP3	kernel	[17179620.752000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode

29/10/06 11:29:05	SGP3	kernel	[17179620.752000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode

As you can see, for some reason it's putting my Radeon 8500 in AGP 1x mode. I have checked in KInfoCenter and it also tells me that the card is running in AGP 1x... very strange I think.

29/10/06 11:29:05	SGP3	kernel	[17179620.752000] mtrr: 0xd0000000,0x8000000 overlaps existing 0xd0000000,0x4000000

29/10/06 11:29:05	SGP3	kernel	[17179621.120000] [drm] Loading R200 Microcode

29/10/06 11:29:05	SGP3	kernel	[17179621.120000] [drm] Setting GART location based on new memory map

29/10/06 11:29:05	SGP3	kernel	[17179621.120000] [drm] writeback test succeeded in 1 usecs
```


I'm starting to feel sick about this ATi issue... in Dapper I had no problems... and this is a fresh install!

Well, thanks for your patience!


EDIT: I have discovered some more things looking at the log. This time, I have loaded the fglrx driver, and let it crash. The I've looked at syslog and found that the las entry before the crash is: 

```
Oct 29 13:01:54 SGP3 kdm_greet[4166]: Internal error: memory corruption detected
```

This means that I'll have a memory problem or something? I don't notice anything wrong under Windows XP... this is very strange...

Also, when using fglrx the memory corruption errors that I described above don't appear in the log...

Any suggestion of where the problem can be?

Thanks!

UPDATE: I have succesfully passed memtest 86, so I'm even more confused now...

ANOTHER UPDATE: I have also discovered that it does not crash in KDM (or GDM), it only crashes once it's loading the desktop. I think that the error is produced by something which is loaded at startup that produces the crash. It does it even after a fresh install, so it must be something that comes with Ubuntu. Is there anything loaded that can cause the crash? (I definitely have composite disabled).

---

