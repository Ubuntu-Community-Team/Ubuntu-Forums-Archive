---
title: "How can I find the &quot;date created&quot; for files?"
date: 2007-11-16
forum: General Help
---

### Post by jeeves on 2007-11-16
One thing I still miss about windoz is Explorer had a column that showed the date files were created. Is there anyway to get the same information in Linux? 

I use Thunar as my main file browser, but even a command line solution would be welcomed.

---

### Post by bingoUV on 2007-11-16
There is no concept of "date created" in unix filesystems, and by extension, in linux.

Many editors while editing file foo.bar, create another temporary file, say .foo.bar.tmp, and when you save they simply rename .foo.bar.tmp to foo.bar. Now the file is created every time you save, but you feel as if you just made another save to the file. For this reason and more, created date may not mean anything sensible.

---

### Post by nikhilsinha on 2008-04-12
I too want to know what the File Create date was...

Few Observations
Source : [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
[LIST]
[*]ext2, ext3 doesn't support "Creation timestamps"
[*]But.... upcoming ext4 supports "Creation timestamps".
[/LIST]
I guess therefore the Gnome File Manager, Nautilus doesn't implement "Create Date Time", I guess they could show the "Create Date Time" for the Fat32, NTFS but they don't.

May be after the inclusion of ext4, we will be able to see "Creation Timestamps".

Nikhil Sinha.
Linux   User #434133	Register at [http://counter.li.org](http://counter.li.org)
Ubuntu User # 15505	Register at [http://ubuntucounter.geekosophical.net/](http://ubuntucounter.geekosophical.net/)

---

