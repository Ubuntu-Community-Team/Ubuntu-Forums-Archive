---
title: "What Disks Smart data line corresponds to &quot;current pending sector count&quot;?"
date: 2019-06-21
forum: General Help
---

### Post by dora5 on 2019-06-21
Disks utility in Ubuntu 12 had a line called "Current pending sector count" under smart data.   It corresponds to the number of sectors waiting to be remapped.   It is not the same thing as number of uncorrectable errors.  

Disks utility in Ubuntu 18 does not have that category - or it might, but perhaps it calls it something different.   

What does Disks Utility in Ubuntu 18 call the current pending sector count?

When I google the matter I learn that you fix current pending sectors  by finding and fixing the badblocks.   Perhaps this is a clue what they're called in Ubuntu 18's version of the disk utility?

Thanks!

Yours,
Dora Smith

---

### Post by kpatz on 2019-06-21
I see current pending sector count in Disks in Ubuntu 18.04.  Click the hamburger menu after selecting the disk to check, then click SMART Data & Self-Tests.  A window will appear with SMART Attributes.  Current Pending Sector Count has ID 197.  If you don't see it, you may need to either scroll the box or enlarge the window, as it's near the bottom of the list.

---

### Post by coffeecat on 2019-06-21
> **dora5 said:**
> 
Disks utility in Ubuntu 18 does not have that category - or it might, but perhaps it calls it something different.   


It does in my 18.04 system. ID = 197. Perhaps it's off the bottom of the list in the SMART Data & Self-Tests window - try scrolling down a bit.

**Edit:** ninja'd! :)

---

### Post by dora5 on 2019-06-21
I suspect it does report current pending sector count.  I'm testing solid state m sata's, and they don't always show everything.   In one case where the drive had far too many bad sectors to begin with the current pending sector count came up, though it was 0.   I'll likely never see it with regular hard drives, because they get tested on our homemade hard drive tester that uses the Ubuntu 12 utility.

---

### Post by TheFu on 2019-06-21
SSDs lie.  SMART data isn't really useful, beyond that number at the bottom showing the total written bytes.  TBW is an important number and included in all reputable SSD warranties.  Inside an SSD, everything is logical, so we can't assume the position of any sector relative to any other sector.  Better SSD controllers do wear levelling whenever data is written to the storage. Think about how you would implement wear levelling.  Basically, I would write data in a sequence always, and just maintain a table that maps the real sectors to the logical sectors presented to the NVMe or SATA interface.  Reality would have little/nothing to do with that presented storage.

If you are doing data forensics, there are specialized devices to help with SSDs, but really there is only a 50/50 chance of getting data from a dead/dying SSD according to my friend in the business.  He wrote a white paper about all of this ... 

Basically, for SSDs, watch the TBW number.

For spinning disks, watch the raw numbers (which Gnome-Disks doesn't show) provided by smartctl.  gnome-disks hides all the useful information.

---

