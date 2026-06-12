---
title: "How to change size of ubuntu partition from within?"
date: 2013-01-19
forum: General Help
---

### Post by JonatanK on 2013-01-19
Hi Everyone!
I have a question regarding the change of size of the logical partition on which I have installed my Ubuntu. How could I change it, without reinstalling the OS?
I have tried using the GParted Partition Manager, but in order to change I would need to unmount. It is impossible to unmount it.
I don't have any other OS, to do it from there.

How can I change the size?

Cheers!
Jonatan

P.s.
I'm running Ubuntu 12.10.

---

### Post by mansonfan78 on 2013-01-19
You can use gparted on a live cd, just download and burn the iso image.  You may need to resize the filesystem afterwards using resize2fs.  Not sure if this is done automatically or not.

---

### Post by JonatanK on 2013-01-19
That's a very good idea. Thank you.
Could you please tell me how to resize the file system (from a live-cd or live-usb)? I don't want to mess up and loose my data.

---

### Post by mansonfan78 on 2013-01-19
Just resize the partition first and then reboot and check the size Ubuntu reports, you may not need to do anything.  If you do, reboot with the live cd and from a terminal type "resize2fs /dev/sdx" (minus the quotes, and replace "sdx" with the drive you're resizing).

---

### Post by mansonfan78 on 2013-01-19
Almost forgot, before resizing you have to unmount with "umount /dev/sdx"

---

### Post by JonatanK on 2013-01-19
Thank you very much!
I'll try this first thing tomorrow.

---

