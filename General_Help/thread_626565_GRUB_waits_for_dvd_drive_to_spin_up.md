---
title: "GRUB waits for dvd drive to spin up"
date: 2007-11-29
forum: General Help
---

### Post by aashay on 2007-11-29
On startup, while grub is loading, it waits for the dvd to spin up completely (about 5-10 secs). This happens between the "loading stage 1.5" and "loading grub, please wait" messages. GRUB proceeds only once the dvd/cd has been recognized and the busy light on the drive goes off. 
If there is no media in the drive, this delay is avoided completely. Even if I eject the media during this delay, grub immediately proceeds to the next stage.
AFAIK, grub shouldn't have anything to do with the dvd drive. 
Is this a known issue? Can I shave off these few seconds to speed up the boot process?

---

### Post by Firestone on 2007-11-29
Are you sure it is grub that is doing it? Since you say it occurs before it is loaded, my bet goes to a wrong boot sequence in the bios. Better check if the 1st boot device isn't your dvd drive.

---

### Post by aashay on 2007-11-29
I'm pretty sure its grub (boot order is correct)
heres how it goes:
1. GRUB loading stage 1.5
2. dvd starts spinning (5-10 secs, more for scratched disks)
3. dvd stops spinning
4. GRUB loading please wait (displayed for half a second)
5. GRUB menu

---

