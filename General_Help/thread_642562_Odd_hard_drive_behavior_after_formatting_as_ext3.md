---
title: "Odd hard drive behavior after formatting as ext3"
date: 2007-12-16
forum: General Help
---

### Post by FuturePilot on 2007-12-16
About every 3 seconds my external hard drive make two clicks. I'm not talking about the click of death, I mean it's actually hard drive activity. It's not random either, it's very precise timing. The thing is I only noticed this after reformatting it as ext3. Before when it was FAT32 and also NTFS I never heard this noise. So I'm guessing it's something related to the ext3 file system? Anyone know what this is? Is it normal?

---

### Post by SoloSalsa on 2007-12-16
I don't know much, but I think that is proper.  I believe Ext filesystems reduce drive strain by caching data, and only writing after regular intervals.  So, the drive is writing *something*, but it is broken down to a few sectors at a time.
No guarantee my answer is not BS.

---

### Post by FuturePilot on 2007-12-16
That kind of makes sense, but would it be writing something if the system is idle?

---

### Post by logos34 on 2007-12-16
I had a similar mystery--except every 2 secs.  The HDD light would flash and I'd hear a tick.  For the life of me I could never figure out what it was.  Write-caching was disabled in hdparm.  I used 'noatime' kernel option.  Ran a generic (not -rt) kernel.  It followed me through a gutsy update.  Finally solved the issue with fresh install of x64 gutsy.  

May have been NSA spyware for all I know.

---

### Post by FuturePilot on 2007-12-16
> **logos34 said:**
> I had a similar mystery--except every 2 secs.  The HDD light would flash and I'd hear a tick.  For the life of me I could never figure out what it was.  Write-caching was disabled in hdparm.  I used 'noatime' kernel option.  Ran a generic (not -rt) kernel.  It followed me through a gutsy update.  Finally solved the issue with fresh install of x64 gutsy.  

May have been NSA spyware for all I know.

Lol :lolflag:
I'm thinking it might have something to do with the journal, but I really have no idea.

---

### Post by FuturePilot on 2007-12-17
Ok, I've been doing some reading and apparently the system writes data/updates the journal every 5 seconds. I timed this more accurately and it's more like 5 seconds not 3. So it would seem that this is normal.

---

