---
title: "LVM logical volume segments"
date: 2015-01-22
forum: General Help
---

### Post by redrumrogue on 2015-01-22
Hi all,

My ubuntu machine has an LVM2 Volume Group (VG) containing a  number of Logical Volumes (LV).  The VG is composed of 2 Physical  Volumes (PV).  All of my LVs were created striped with 2 stripes each.   Running ```
sudo lvs --segments
``` was showing the list of LVs all  having only one segment.  I've recently extended one of my LVs to  increase it's size by 50G, using ```
sudo lvextend -i2 -L+50G VGname/LVname
``` and now I've noticed that ```
sudo lvs --segments
```  is showing 2 segements for the LV which I extended.  When viewd using  the LVM GUI I can see that the two segements exist at different  locations on each PV.  I imagine that this may reduce IO performance for  that LV.  So I have two questions:

  
[LIST=1]
[*]Is there a better way to extend an LV which maintains just 1 segment? 
[*]Now that I ahve two segments is there a way to merge the segments into 1 again? 
[/LIST]
  Thanks - JJB

---

### Post by Nutria on 2015-01-24
The output of your commands would be handy.

---

### Post by redrumrogue on 2015-01-24
Hi there.  Output from [B]sudo lvs --segments

[/B]```

LV              VG     Attr      #Str Type    SSize  
  lvdata          data   -wi-ao---    2 striped   3.64t
  inspiron        vmpool -wi-a----    2 striped 130.00g
  ubuntu140401srv vmpool -wi-ao---    2 striped  50.00g
  v6r2013xsrv     vmpool -wi-a----    2 striped 105.00g
  v6r2014xsrv     vmpool -wi-a----    2 striped 105.00g
  vmtemp          vmpool -wi-ao---    2 striped 250.00g
  win7pro         vmpool -wi-ao---    2 striped  55.00g
  win7pro         vmpool -wi-ao---    2 striped  45.00g

```

As you can see win7pro appears twice after using [B]lvextend -i 2 -L +50G vmpool/win7pro

[/B]**sudo lvdisplay vmpool/win7pro** also shows 2 segments ...
```

--- Logical volume ---
  LV Path                /dev/vmpool/win7pro
  LV Name                win7pro
  VG Name                vmpool
  LV UUID                fArfz4-tqkD-B1sg-AJSx-z9uL-SMRH-lJIHaa
  LV Write Access        read/write
  LV Creation host, time IXTREME, 2014-08-12 12:08:56 +0100
  LV Status              available
  # open                 1
  LV Size                100.00 GiB
  Current LE             25600
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     512
  Block device           252:3

```

And using the LVM2 GUI you can see that the two segments are at different locations on the physical volumes (at least that's how I'm interpretting the image) ... [ATTACH=CONFIG]259472[/ATTACH]
If, with two segemtns, the data is split in two locations on the physical disks, that surely can onlt have a detrimental effect on read/write speeds for that LV?  I'd prefer for the LV to have just one segment as it did before I extended it.

---

### Post by Nutria on 2015-01-24
The image is a bit too small for my old eyes to see clearly.  Was the place that the new segment was added to the "best" place for it to be added?

---

### Post by redrumrogue on 2015-01-25
The image in my previous message is a thumbnail link.  You can click on it to see a larger version - did you do that?

---

### Post by Nutria on 2015-01-25
> **redrumrogue said:**
> The image in my previous message is a thumbnail link.  You can click on it to see a larger version - did you do that?

Yup...  I just downloaded it and opened it in ristretto, but at 150% zoom the words are too blurry for me to read.

Could it be that this is where lvm thought it was best to put the segment?  (First available 50G, or something like that?)

---

### Post by redrumrogue on 2015-01-25
I'll have to take a look at the other LVs postions on disk.  It probably is the case that the extra 50G i added was just created at the next available 50G block of free spsce.  I understand and accept that if that's the case.  I'm wondering if there's a way to merge the two segments for the win7pro LV, and i suppose this would probably mean moving the other LVs to make space ... i'll read the man pages and see if there's a way to move the extents of an LV.

---

### Post by Nutria on 2015-01-25
> **redrumrogue said:**
> i'll read the man pages and see if there's a way to move the extents of an LV.

There is, but you'll need enough free space to to temporarily park that 50GB.  (You can't just "shift" the segment...)

---

### Post by Ossipon on 2015-03-25
It is possible to merge segments, but you will need an area of contiguous free space on a PV equal to the size of both segments, or an area of contiguous free space equal to the size of the second segment after the first segment.

Some useful commands:
**lvs --segments -o +pe_ranges** will show you where exactly which segments are located on the physical volumes.
**lvdisplay -m *LogicalVolumePath*** will show you which segments belong to your LV and, importantly, in which order; because sometimes the second part of an LV can be located before the first part on the physical volume. This was the case in my setup, but probably not in yours.

To prevent an LV from splitting in the first place, use **lvchange --contiguous *LogicalVolumePath***. However this will make it hard for you to extend your LV. Contiguous logical volumes can only be extended if there is free space directly following it, just like non-lvm partitions. This takes away one of the major advantages of LVM.
Anyway, I don't think having more than one segment will have much of an impact on IO performance. (see [http://unix.stackexchange.com/questions/64233/is-there-any-performance-penalty-to-having-multiple-segments-for-one-volume-in-l]("http://unix.stackexchange.com/questions/64233/is-there-any-performance-penalty-to-having-multiple-segments-for-one-volume-in-l"))

---

