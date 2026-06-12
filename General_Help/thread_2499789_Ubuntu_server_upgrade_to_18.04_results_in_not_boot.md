---
title: "Ubuntu server upgrade to 18.04 results in not booting"
date: 2024-08-10
forum: General Help
---

### Post by alldunn2 on 2024-08-10
I have a server running fakeraid (RAID 1) that was running on 16.04.  I ran the upgrader to 18.04.  After the reboot, I got to the grub rescue screen.  I ran the boot-repair live disk and I am including the pastebin link on the last run in the hopes that someone may be able to point me in the right direction.  Note that I have even gone as far as unplugging all other hard drives so that the only ones available were the 2 in the array.  I've ran the automatic and gone through the advanced options and am at a loss at this point.  Any help in getting my system to boot without a rebuild is very much appreciated.

[URL="https://paste.ubuntu.com/p/pQ7PvdmGQW/"]https://paste.ubuntu.com/p/pQ7PvdmGQW/
[/URL]
Thanks.

---

### Post by TheFu on 2024-08-11
Really need to learn about support periods.

16.04 standard support ended in 2021.
18.04 standard support ended in 2023.

The oldest release anyone should be installing today is 22.04.
If you aren't risk adverse and your main applications are supported on 24.04, then use that, if you are ubuntu centric.  I have a few major servers that are unlikely to be able to run their main application until 1Q 2025 on 24.04. The companies behind those applications take their time moving to new LTS releases and never bother with non-LTS versions at all.

Update: I just checked one of my main enterprise applications.  They don't support 22.04 yet!  Crazy, right?   I do see lots of 20.04 guides for it, however.  When the 22.04 update guide is out, I'll migrate.  Best to move when possible, not after support ends.  End Update.  

Of course, if you have paid ESM support, you'll have a contact number for that.

Also, FakeRAID really shouldn't be used since around 2005.  It has all the limitations/restrictions of HW-RAID, but none of the added safety.  You can use this as an opportunity to remove that albatross from your system.

---

### Post by yancek on 2024-08-11
What method did you use to try this upgrade?  The standard upgrade method won't work since neither 16.04 nor 18.04 are supported and you would have had to change your sources.list to find the archive for 18.04.

Line 121 of boot repair shows you booted in UEFI mode but the installed systems are in Legacy mode even though the hardware is UEFI capable.  There is a lot of information that is usually shown with boot repair that is not shown in your output.  The content of the various partitions, particularly the boot files is usually shown at the beginning of boot repair and your output does not show anything.

It might be easier to just do a new install of a supported system and restore data from backups.

---

