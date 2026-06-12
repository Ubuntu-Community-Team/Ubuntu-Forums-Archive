---
title: "Where is the Cache for the Built-in &quot;Copy Disc&quot; Utility?"
date: 2007-12-09
forum: General Help
---

### Post by OzzyFrank on 2007-12-09
I was showing a friend new to computers how much easier it is to copy discs in Ubuntu than in Windows, by just popping in the CD or DVD, waiting for the icon to appear on the desktop, and choosing "Copy Disc" from the context (right-click) menu, and he was indeed impressed. However, after a few DVDs, we went to do another and it couldn't, because suddenly there was only 2.2Gb left on his Ubuntu drive. So obviously the cache wasn't being cleared, like if you were using GnomeBaker which clears its cache on exit.

So it begs the question: Where is the cache used for this task, so I can go and delete any temporary files in the future? Thanks in advance.

---

### Post by pebo on 2007-12-09
Well they are usually in the /tmp folder somewhere, if you're in kde, in /tmp/kde-$HOME. But it's worth checking the log files in /var/log cos they can get out of hand sometimes. You could install filelight which will show graphically where the biggies are.

---

### Post by OzzyFrank on 2007-12-09
No, the cache doesn't seem to be in /tmp for this task, unless on my PC it has been flushed. I have a few folders in there but only take up 85Kb in all. Will look there on my friend's PC another time, just in case. So if anyone knows what folder is the cache for "Copy Disc", and the names of the temp files even, please let us know.

As for the tip for Firelight, thanks! That's really a good little app. I found some .vob and .iso files I forgot were there which means locating them for deletion is a breeze. Well worth installing! Cheers

---

