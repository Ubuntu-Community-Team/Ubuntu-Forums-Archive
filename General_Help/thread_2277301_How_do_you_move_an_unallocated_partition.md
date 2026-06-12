---
title: "How do you move an unallocated partition?"
date: 2015-05-07
forum: General Help
---

### Post by skinnydude on 2015-05-07
[COLOR=#111111][FONT=Ubuntu]For the life of me I cannot figure out how to move this partition so I can add it onto my ubuntu partition. I need to move it down two partitions so it is next to sda8, then I can add those partitions together. I cannot edit it in anyway unless I make it into a partition, But even when I do that and try to "resize/move" It only allows me to re size it. I have no clue, I have been trying to do this for over an hour. I have tried with gparted, gparted booted from a USB, the windows drive editor, and even another drive editor I downloaded onto my windows drive. Please help, thanks :)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://i.imgur.com/axk0BWu.png](http://i.imgur.com/axk0BWu.png)[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-05-08
To put it simply, you can't move what's not there.

The unallocated space is just that, free space. Nothing there, nothing on it, nothing to move. If you want the free space at the end, you need to move all the partitions that come after it to butt up to sda5. Consequently, if you move all partitions sda6 though sda11 to start from sda5 then your free space will end up at the end of the drive. 

This is best done booting from live media so all partitions are unmounted. It will probably take some time. Use Gparted NOT a Windows partition resizing tool. Good luck.

---

### Post by skinnydude on 2015-05-08
Yup, that did it. Thanks.

---

### Post by Bucky Ball on 2015-05-08
Good news. Please mark the thread as solved to help future travelers. See the second link in my signature. Thanks.

---

