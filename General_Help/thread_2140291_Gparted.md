---
title: "Gparted"
date: 2013-04-29
forum: General Help
---

### Post by chribuntu on 2013-04-29
Hi!
I am trying "fix" my partitions in Gparted.



[ATTACH=CONFIG]241951[/ATTACH]
This is my layout. I want to extend the sdb partition with the unallocated space but the SWAP partition is in the way.

---

### Post by Mark Phelps on 2013-04-29
You can't -- wrap around an existing partition.

If you can, you would "move" the extended partition to the "right" -- to leave unallocated space to the "left".  Then, you can expand the first partition.

---

### Post by ibjsb4 on 2013-04-29
Looks to me that you can move "unallocated" to sdb2 and then move it to sdb1.

---

### Post by gabriella on 2013-04-29
Why don't you just delete your swap partition and then re-create it at the end of the unallocated space.

---

### Post by Mark Phelps on 2013-04-29
> **ibjsb4 said:**
> Looks to me that you can move "unallocated" to sdb2 and then move it to sdb1.

You can't move "unallocated" space; instead, you have to move the "allocated space" -- which results, indirectly, in the relocation of the unallocated space.

---

### Post by ibjsb4 on 2013-04-29
> **Mark Phelps said:**
> You can't move "unallocated" space; instead, you have to move the "allocated space" -- which results, indirectly, in the relocation of the unallocated space.

Ok, maybe I just didn't say it right.  

Looks to me sdb2 can be resized to include that unallocated 36G and then passed on to sdb1.  That swap is not in the way.

---

### Post by ssreddy555 on 2013-04-29
> **gabriella said:**
> Why don't you just delete your swap partition and then re-create it at the end of the unallocated space.

Perhaps, it's the easiest, fastest & least uncomplicated method.

---

### Post by grahammechanical on 2013-04-29
Do not forget that the key symbol is reminding you that those file systems are mounted. You have to do this from sda (if it is Ubuntu) or from a live session. You will have to mark swap as swap off. The live session will most probably make use of the swap partition so it will stll be marked as swap on.

May I suggest that you do this. If the others agree to the order of events.

1) resize/expanded the extended partition (sdb2) to take up all the unallocated space.
2) move the swap partition (sdb5) to the right end of the now enlarged extended partition.
3) resize/shrink the extended partition (sdb2) to create unallocated space to the left of it. As much space as you want/need/can.
4) resize/expand the / partition (sdb1) to take up the unallocated space to its right.
or create a new partition out of the unallocated space, if you want to.

Gparted in a live session will make a list of the actions/tasks that you are setting and run each action one after the other. It will take time. I like to run each action on its own and then start again. It is my personal preference. It gives me confidence that the actions are being completed.

Regards.

---

### Post by chribuntu on 2013-04-29
Hmm yes. Thanks for quick resonse. I had college today and I couldn't respond. But thankyou all for helping.

---

