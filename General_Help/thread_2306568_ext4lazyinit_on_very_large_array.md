---
title: "ext4lazyinit on very large array"
date: 2015-12-16
forum: General Help
---

### Post by XBNCPRk on 2015-12-16
I decided recently to upgrade all the 2tb drives in a HTPC to 4tb drives (thank you black friday sales). Originally it was 2 arrays, each with 8 2tb drives in raid5. Because of the longer recovery times involved should there be an issue, I also decided to migrate them to raid6 arrays, each consisting of 8 4tb drives, for a total of 32tb each (22.8 usable). 

I built the array, transferred the data, went to expand it and ran into my first issue - namely that I forgot ext3 wont work with an array that large. No problem, converted it to ext4 and added the 64bit filesystem tag. I should have also told it not to use the lazy method of initializing inodes and just put the time in up front, because now the disks are all hit every few seconds by short bursts as it writes them in the background. 

Here now we arrive to my question(s).... 
-The arrays have been up and running now for about 48 hours, and ext4lazyinit is still kicking in every couple seconds. Anyone have any experience or an estimate on how long this will continue for on an array of this size?
-Is there any way that google couldnt find to speed this up? I dont care if it thrashes on the disks for a few hours nonstop, that would be preferable to very slowly doing it over days. The only result I could find on google was a one line quip that the slow speed of it seems hardcoded... 
-Is there any way to find the progress of this? Its displayed on screen when doing it the non-lazy way, so assumably its tracked somewhere fairly easily accessible. That would at least help me decide if I should let it finish running painfully slowly in the background or if I should just cut my losses, wipe the array and start from scratch again.

---

### Post by deepakdeshp on 2015-12-18
This may be useful

[https://www.thomas-krenn.com/en/wiki/Ext4_Filesystem](https://www.thomas-krenn.com/en/wiki/Ext4_Filesystem)
[http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html](http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html)

Give a higher priority to the process [http://www.slashroot.in/nice-and-renice-command-usage-examples-process-priority-linux](http://www.slashroot.in/nice-and-renice-command-usage-examples-process-priority-linux)

---

### Post by XBNCPRk on 2015-12-18
Thanks deepakdeshp, but Id unfortunately already read through those pages. While the first does a good job of explaining what the ext4lazyinit process is, it doesnt provide any way of interacting with or modifying its behaviour. And the second page only refers to building the array, not the filesystem (also, not all of their tips are actually correct, though thats better suited for another thread). 

Giving the ext4lazyinit process a higher priority would seem to be a sensible solution, however the process only runs for perhaps 1 second out of every four, never consumes more than ~12% of i/o bandwidth and miniscule cpu cycles. That makes sense since its intent is to run unnoticed in the background while you use your newly set up system. I would rather though force it to run continuously at best possible speed regardless of what resources it needs to hoard, but it seems like that may not be possible. 

BTW - 72 hours and counting, and the process is still churning away slowly in the background...

---

### Post by XBNCPRk on 2015-12-21
After four plus days of the annoying ext4lazyinit process running, and no signs of it ever finishing, I just scrapped the array and rebuilt it from scratch using the extended mkfs.ext4 options to initialize the itables and journal from the start. Annoyingly this only took about fifteen minutes for the whole 32tb array, so Im not entirely sure why the default is to use the delayed background initialization under the auspices of saving time during setup.

For anyone else encountering this issue, the slow cycling time of the ext4lazyinit process is indeed hardcoded, and cannot be changed or forced. Similarly, there is no way (at least from ridiculously extensive googling) that I could discern to check its progress. 

The takeaway from this is - dont use ext3 for large filesystems, dont assume ubuntu will add the 64bit flag on its own (though why it wouldnt on any multi-tb drive or array is honestly beyond me), and absolutely disable the lazyinit feature when creating an ext4 filesystem.

---

