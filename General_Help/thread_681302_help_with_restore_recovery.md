---
title: "help with restore recovery"
date: 2008-01-28
forum: General Help
---

### Post by robsarm on 2008-01-28
Ok I've been searching the forums for awhile now and haven't found exactly what I need. I did try to post the following (in Quotes) on the ubuntu rescue remix forums but haven't received any help.

"I made a stupid mistake when installing ubuntu to my desktop and reformatted my entire hard drive. Fortunately the truly important (i.e. work) data was backed up, unfortunately all my less critical data, family photos, music, etc was not.
So I have downloaded the rescue remix cd and tried using parted with no luck. I then ran testdisk to search for missing partitions and I can actually see several hpfs-ntsf partitions as well as a fat 32 LBA partition. I tried to use the copy command to copy specific directories but was unable to actually find any files that were copied.
Per the data recovery wiki from ubuntu community I am now running ddrescue to copy from my /dev/hda disc (my main hard drive) to my /dev/sda1 (external usb drive). If I am reading correctly that will copy the entire disk from /dev/hda
to /dev/sda1 where I can then try to use foremost and photorec to recover the files at my leisure, while still using my main (/dev/had) hard drive without fear of further damaging my lost files. Is this correct?
Although I love my awesome new ubuntu os, I fear that I still need to use windows for two specific tasks while I make the transition to Ubuntu only and would like to try again to partition my main drive for dual boot windows / ubuntu, but I want to assure that I have copied everything that might be recoverable to my external hard drive first.
Have I badly misread this or am I on the right track.
Thanks for any help you can give me."

Since posting the above to the rescue remix forums, DDRescue finished copying my internal drive to my external drive at which point I quit the rescue cd and rebooted to my internal hard drive.
everything is fine but I can't see my external hard drive at all anymore.
I am completely at a loss here since I assumed that ddrescue would copy my internal drive to my external drive and now I can't even see my external hard drive at all.
any thoughts?

---

