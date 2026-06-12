---
title: "partition resizing"
date: 2007-06-28
forum: General Help
---

### Post by deepred on 2007-06-28
When I installed Ubuntu (Dapper Drake), I mounted /var on a separate partition which now is full. Is there a way to resize it as I have plenty of space elsewhere? Or is there a way to safely clean up /var for I'm not sure what can and cannot be deleted from there without breaking anything?
Thanks

---

### Post by bodhi.zazen on 2007-06-29
You can resize from a live cd with gparted

You might also want to look at LVM, this is exactly what LVM was designed to help with (you can re-size "on the fly").

---

### Post by deepred on 2007-06-29
Thanks, I'll try gparted from Live CD.
Will implementing LVM involve reinstalling the system?

---

