---
title: "FSCK check failed  exit status 4"
date: 2008-05-08
forum: General Help
---

### Post by bannik on 2008-05-08
basically every time my ubuntu starts it does a fsck check and fails exist status I wait and it tells me to re check manually, now I dont know what the problem is but if you can tell me and also tell me how to manually check my fsck that would be great 

thanks




a super bump

---

### Post by Angry_Mushi on 2008-12-23
I have the same problem, but I think the cause of mine is an incomplete download of a torrent (bcause it shows the file I was downloading.

No Idea what to do

Any help would be appreciated

---

### Post by Feivel on 2008-12-23
Same trouble here. Once the check found the error (which apparently is a bad file), I reboot and hit esc to bypass the disk check. Is there any way to find out what the problem is or is there any way to turn off the automatic disk check after x boots? It is getting old really fast and the only real annoyance with Ubuntu having to hit ESC on every reboot to bypass a disk check.

---

### Post by Titan8990 on 2008-12-23
To remove automatic disk checking you have to edit /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=567bbf65-3e84-4fc1-831e-74ee1603dd62 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
UUID=1649f5ce-e869-4a3f-b7a9-e638e0bfdc80       /media/backup   ext3    defaults0       0

```

You would change the 0 1 (as shown for my main filesystem drive) options for your main filesystem drive to 0 0 (as shown for my /media/backup drive).

---

### Post by p_quarles on 2008-12-23
> **Titan8990 said:**
> To remove automatic disk checking you have to edit /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=567bbf65-3e84-4fc1-831e-74ee1603dd62 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
UUID=1649f5ce-e869-4a3f-b7a9-e638e0bfdc80       /media/backup   ext3    defaults0       0

```

You would change the 0 1 (as shown for my main filesystem drive) options for your main filesystem drive to 0 0 (as shown for my /media/backup drive).

You don't want to do that. For pretty much the same reason that you don't unplug a smoke detector when the noise starts bothering you.

---

### Post by Feivel on 2008-12-23
> **Titan8990 said:**
> 

You would change the 0 1 (as shown for my main filesystem drive) options for your main filesystem drive to 0 0 (as shown for my /media/backup drive).

Did it, reboot with my fingers crossed (Windows scarred my reboot experiences) and it worked like a charm. Thanks :)

---

### Post by p_quarles on 2008-12-23
> **Feivel said:**
> Did it, reboot with my fingers crossed (Windows scarred my reboot experiences) and it worked like a charm. Thanks :)

And now your system will never tell you when the filesystem is getting corrupted or filling up with garbage. You're actually in a worse long term position now.

---

### Post by Feivel on 2008-12-23
> **p_quarles said:**
> You don't want to do that. For pretty much the same reason that you don't unplug a smoke detector when the noise starts bothering you.

Can't I run fsck manually, correct the error (which seems to be a corrupt file) then reactivate fsck in fstab? Even the Windows chkdsk was nothing more than an annoyance.

---

### Post by Titan8990 on 2008-12-23
I have to agree with p_quarles. You **can** disable automatic checking, but should you?


I have it disabled on my backup drive because FSCK is not supported over a USB interface.

---

### Post by Feivel on 2008-12-23
> **p_quarles said:**
> And now your system will never tell you when the filesystem is getting corrupted or filling up with garbage. You're actually in a worse long term position now.

See my reply to you :)

---

### Post by Titan8990 on 2008-12-23
Yes, you can but you shouldn't put it off for too long.

---

### Post by p_quarles on 2008-12-23
> **Feivel said:**
> See my reply to you :)
I gave the procedure as I recall it (though it's something you do rarely, so it may need somee tuning) in Angry_Mushi's own thread on the subject. Unfortunately, when people post the same question in multiple places, it gets much more difficult to track issues.

---

### Post by Angry_Mushi on 2008-12-26
> **p_quarles said:**
> I gave the procedure as I recall it (though it's something you do rarely, so it may need somee tuning) in Angry_Mushi's own thread on the subject. Unfortunately, when people post the same question in multiple places, it gets much more difficult to track issues.

Sorry about that, but since this was an older thread and it hadn't gotten any replies I hadn't much hope in getting replies here...

and I agree on the disabling the fliecheck...

---

