---
title: "Is DD Reliable?"
date: 2007-06-25
forum: General Help
---

### Post by OzzyFrank on 2007-06-25
Hi. I've used DD before to copy over images of hard drives, and think it is a very useful command. However, the other day while looking through Synaptic I came across another program/command (sorry I didn't note the name!) that basically claimed to do the same thing as DD, but be more reliable on larger drives. I'd like input on whether you guys see DD as being unreliable on large drives, or whether thiis was hype from the developers of that command. Obviously I'd rather go with the more reliable alternative if there are issues with DD.

---

### Post by kidders on 2007-07-14
Hi there,

I've never had any problems with dd. I suppose it's conceivable that using it to dump large amounts of data could be described as "unreliable" because the probability of a freak bit error would be higher, due simply to the sheer number of consecutive reads/writes.

Perhaps the app you found performs some additional checks, just to make sure the source & destination data really are the same. That's something you can do yourself anyway, if you feel concerned.

That's just a wild guess ... but you've started quite a number of unanswered threads, so I thought I'd at least try. :-)

---

### Post by HermanAB on 2007-07-14
The 'dd' program is as reliable as the underlying hardware.  I have used it to clone many disks and have never experienced trouble.  It is a production quality tool.

---

### Post by OzzyFrank on 2007-07-14
> **kidders said:**
> That's just a wild guess ... but you've started quite a number of unanswered threads, so I thought I'd at least try. :-)

Yes, nobody likes me, hehe... except for you guys. Hehe...

Actually thought this thread would get a few comments, but no such luck. Not sure what the command/program is (as I actually haven't got it) but the claims against DD's reliability seemed to come from the author of the alternative.

Personally, I used DD to copy over Windows XP from a dying drive (thankfully just mechanical startup problem, no corruption) and it was (to my knowledge) perfect. And that was 130Gb of data on a 200Gb drive (I'm pretty sure it copied the whole 200Gb though, but the 2 drives were actually identical size, make and model, so I'm not sure, as I didn't have to mess with partition sizes afterwards, etc).

As far as I can see, there is no reason for me to not recommend DD as a fast and simple image backup. I'm bragging to Windows users how I can backup my Windows drive while surfing the web in Ubuntu, unlike using Ghost or something, where you'd leave your PC alone for 4 or 5 hours.

---

### Post by Mr. C. on 2007-07-15
The dd program simply uses the underlying OS read/write system calls.  It is no more or less reliable than any other program.

Use it with confidence.
MrC

---

### Post by Beamerboy on 2007-07-15
> **OzzyFrank said:**
> Hi. I've used DD before to copy over images of hard drives, and think it is a very useful command. However, the other day while looking through Synaptic I came across another program/command (sorry I didn't note the name!) that basically claimed to do the same thing as DD, but be more reliable on larger drives. I'd like input on whether you guys see DD as being unreliable on large drives, or whether thiis was hype from the developers of that command. Obviously I'd rather go with the more reliable alternative if there are issues with DD.

Well last week I had a corrupted superblock on my main research machine.  It was a 250GB drive, so whereas not the largest, certainly not small.  I dd'd the drive to a spare 250GB carried out badblocks and fixed the superblock.  Booted the machine with the new clone and it booted fine and all my services launched and carried on where they left off without so much as a hiccup.  I am still using the cloned drive today.

So yes dd works fine for me.

Paladine

---

### Post by kidders on 2007-07-15
Just for the heck of it, I googled "more reliable than dd", to see what would happen. The only even *vaguely* relevant results I got seemed to have to do with the obvious susceptibility to sniffing, when dumps are transmitted raw, over a network.

Imo, the only changes one could make to dd are ones that would make it more suited to very specific uses, and less like the generic tool that it is ... *dis*improvements, if you ask me hehe.

Incidentally, someone here might know this one: If you'd just done something like **dd if=/dev/sda1 of=whatever**, and you were feeling paranoid, would it be naïve to think you could compare md5sums "/dev/sda1" and "whatever", to guard against hardware problems? The reason I ask is that (as HermanAB and I mentioned) errors caused by the underlying hardware are pretty much the only thing I can imagine going wrong with a dump.

---

### Post by Mr. C. on 2007-07-15
> **kidders said:**
> Incidentally, someone here might know this one: If you'd just done something like **dd if=/dev/sda1 of=whatever**, and you were feeling paranoid, would it be naïve to think you could compare md5sums "/dev/sda1" and "whatever", to guard against hardware problems? The reason I ask is that (as HermanAB and I mentioned) errors caused by the underlying hardware are pretty much the only thing I can imagine going wrong with a dump.

This would not work.  The superblock of the filesystem, and other timestamps change the contents of the inodes, which of course are also in the file system on the disk.  Therefore, a checksum on the byte stream create via dd would not be useful.

MrC

---

### Post by az on 2007-07-15
> **Beamerboy said:**
> Well last week I had a corrupted superblock on my main research machine.  It was a 250GB drive, so whereas not the largest, certainly not small.  I dd'd the drive to a spare 250GB carried out badblocks and fixed the superblock.  Booted the machine with the new clone and it booted fine and all my services launched and carried on where they left off without so much as a hiccup.  I am still using the cloned drive today.

So yes dd works fine for me.

Paladine

You're lucky.  Whatever caused your problem could have been hardware-related and permanent.

On faulty hardware GNU DDRescue will read and re-read the drive to get an accurate copy where dd will juct quit.  It will read backwards and forwards and will keep a log of errored bytes so that you can go back at a later time and try to read just those blocks again to complete your image copy.  In the meantime, it zeroes out unreadable blocks,  Gnu DDrescue if a first-line data recovery tool.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by OzzyFrank on 2007-07-15
Spent the last hour searching through Synaptic and finally found the one with lofty claims of being more reliable than dd:

multithreaded (raw) disk copying program
Tool for large disk to disk copying.
 .
** pcopy** is intended to be used when doing large disk (partition)
to disk (partition) copying where [B]dd is just too slow (and error
prone)[/B]. It also displays a progress counter while doing the
copying.

 Homepage: [http://directory.fsf.org/sysadmin/Backup/pcopy.html](http://directory.fsf.org/sysadmin/Backup/pcopy.html)


As you can see, someone is asserting that dd is "error prone", which is what prompted me to start this thread. I can see now this is just another "My program is the best!" developer claim.

---

