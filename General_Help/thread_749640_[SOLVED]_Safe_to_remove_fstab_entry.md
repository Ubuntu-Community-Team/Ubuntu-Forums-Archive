---
title: "[SOLVED] Safe to remove fstab entry?"
date: 2008-04-08
forum: General Help
---

### Post by duckgoesoink on 2008-04-08
Hi,

I would just like to confirm that it is safe to completely remove the NTFS entry from the fstab? I read through other posts, but want to be REALLY sure I don't stuff anything up following bad advice (I've ruined enough things in the past doing that). 

I don't want my Windows partition automounting every time someone logs in. Actually I don't see any need to ever mount it (I have a shared FAT32 partition automounting to share data between systems).

Thank-you lovely people :-)

---

### Post by Belak on 2008-04-08
The fstab just tells linux what to mount where when it boots up.
You should not have any problems if you remove the line for your NTFS partition.

---

### Post by Rocket2DMn on 2008-04-08
You can add "noauto" to the options column of the fstab entry to stop it from mounting.  You can try commenting out the entry by placing a "#" at the front of the line, but then it may try to automount under HAL rather than finding it in fstab.
So your line may go from this
```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
to this
```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8,noauto 0 0
```

---

### Post by davidpbrown on 2008-04-08
I'm relatively new to Ubuntu but I've done alsorts to the fstab.

Yes, you can remove a line safely.. but do a backup beforehand.

Worst case is that you foul it up completely but even then, if you have your /home on a separate partition, you can reinstall and your settings mostly stored in /home will just return everything as it was. That is - changing fstab doesn't change the partitions just the loading of them.

Hope that helps.

---

### Post by duckgoesoink on 2008-04-08
Thanks everyone, I tried the noauto option (was confused before - there was nothing called auto to change to noauto). Seems to work fine.

Have a great night :-)

---

### Post by bodhi.zazen on 2008-04-08
> **duckgoesoink said:**
> Hi,

I would just like to confirm that it is safe to completely remove the NTFS entry from the fstab? I read through other posts, but want to be REALLY sure I don't stuff anything up following bad advice (I've ruined enough things in the past doing that). 

I don't want my Windows partition automounting every time someone logs in. Actually I don't see any need to ever mount it (I have a shared FAT32 partition automounting to share data between systems).

Thank-you lovely people :-)

Solved:

Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help ...

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


====================


Also, FYI, when editing system files use comments to document (to yourself) your changes.

Comments start with a #
#Everything after the comment is ignored by the system.

Rather then deleting lines
# Comment them out
# Note to self: date : commented out to disable mounting of the partition

---

### Post by duckgoesoink on 2008-04-08
> **bodhi.zazen said:**
> 
Please mark this thread as solved, it saves the time of many volunteers looking to help ...


Whoops, marked as solved now. Never did know where to find that button till now. Cheers :-)

---

### Post by Belak on 2008-04-08
Wow. I didn't know that button existed. You learn something new every day.

---

