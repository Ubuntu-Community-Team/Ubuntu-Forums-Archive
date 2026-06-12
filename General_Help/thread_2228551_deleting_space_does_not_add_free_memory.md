---
title: "deleting space does not add free memory"
date: 2014-06-08
forum: General Help
---

### Post by angelofbrokendreams on 2014-06-08
Dear all,
when I delete files from the disk, free space is not added. My special case is that I delete files from a local NTFS partition of my HDD, but this problem occurs both when I delete these files from Ubuntu and I also tried to do so on windows.
I also found old posts with other guys having this problem, but none of them solved it. Can you help me ?

```

acham@acham-fisso:/$ find ~/ -size +200M
acham@acham-fisso:/$

```

I also deleted temps, old kernels and all with ubuntu tweaks.
Of course, recycle bins are empty  (both on ubuntu and on windows).

ubuntu 12.04 (precise) 64 bit
Kernel Linux 3.2.0-64-generic
intel® Core&#8482; i5-2300 CPU @ 2.80GHz × 4 
7,8 GiB

---

### Post by bapoumba on 2014-06-08
What do you mean by "free space is not added" ? Say you have 100 "free space" and delete 100 and expect to have 200 "free space" ? But where is your measure made ?
```
df -h
```
Will give you an overview of available space on your hard drive.
```
du -sh <path>
```
Will show space used by <path>.

---

### Post by angelofbrokendreams on 2014-06-08
Dear Bapoumba,
thanks for your answer. That's how you say: > **bapoumba said:**
> Say you have 100 "free space" and delete 100 and expect to have 200 "free space"

I take the measurement of free space from Nautilus, but as a matter of fact, something strange happened. The space is now updated regularly in Nautilus and by terminal... I tried to update the system and already rebooted without success this morning, but now it simply works again. I think we could close the post. For future people with this issue, it may be that the solution was in the system update, as in other posts they stated so.

Thank you, Bapoumba

---

### Post by bapoumba on 2014-06-08
You are most welcome.
One way to inform other users is to mark your thread as solved (under Thread Tools), thanks.

---

