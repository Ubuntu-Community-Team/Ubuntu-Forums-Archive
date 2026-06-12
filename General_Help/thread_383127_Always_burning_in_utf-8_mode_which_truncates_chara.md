---
title: "Always burning in utf-8 mode which truncates characters."
date: 2007-03-12
forum: General Help
---

### Post by microsafe17 on 2007-03-12
I have a problem that has been bugging me.  I had the same issue on Edgy, but I am currently running Feisty.

Using the most updated version of Gnome Baker available in the repositories.

Every time i burn something it ends up using UTF-8 mode and truncating so many characters that most of the time the data is indistinguishable from the other data.  I thought at first it was because I hadn't selected Joliet or Rockridge on the setup while burning, but that doesn't appear to be the case.  I didn't think I would have to change my local settings, but I am having problems using the I: -input-charset, not really sure when I call that.  Here is the log.

And I actually checked both formats this last time, but normally I don't do that.

```
Executing 'genisoimage -gui -V Books 7 -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-joel/gnomebaker-PDSEPT | builtin_dd of=/dev/hdd obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using [SHORT_NAME] for [A MUCH LONGER NAME THAT SHOULD BE SUPPORTED]
/dev/hdd: "Current Write Speed" is 6.1x1352KBps.
Total translation table size: 0
Total rockridge attributes bytes: 22047
Total directory bytes: 53248
Path table size(bytes): 894
Max brk space used 21000
2282977 extents written (4458 MB)
/dev/hdd: flushing cache
/dev/hdd: updating RMA
/dev/hdd: closing disc

```

Anyone have any clue, everything used to burn fine on Hoary and Dapper.  I did a clean install of Edgy though so I might have had some different settings.  I have used several DVD's that have data I have to manually sort every time I look at it now (need to burn new copies) instead of allowing the Gnome Disk Catalog to do everything for me.  

Edit:  Final note I did load this from an existing ISO in this case.  The ISO created fine without any similar message.

Thanks for looking.

---

### Post by microsafe17 on 2007-03-17
Anyone have any ideas.  Any help would be greatly appreciated.  I couldn't find anything through all my searching.

---

### Post by microsafe17 on 2007-03-24
Well, sorry I didn't look further, apparently it is actually just failing and changing the names to unreadable if there is a (-) hyphen in the filename.  It doesn't seem to matter if it is in the folder name, but it fails when it is in the filename.  Anyone know of a way to disable this?  I switched to a mode other than UTF-8 and it wasn't corrected, looking at it I am not sure that is the problem now.

---

