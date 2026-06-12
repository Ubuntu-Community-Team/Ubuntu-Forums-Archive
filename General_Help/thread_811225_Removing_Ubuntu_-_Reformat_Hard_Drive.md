---
title: "Removing Ubuntu - Reformat Hard Drive"
date: 2008-05-28
forum: General Help
---

### Post by Lanc1988 on 2008-05-28
I have a computer with two hard drives in it. On one hard drive I have windows vista and on the other i have ubuntu.. I would like to reformat the hard drive with ubuntu to be NTFS again because I need the space for something else. I also plan to reinstall vista on its hard drive as well.

How can I reformat this drive with ubuntu since when im in vista it doesnt see ubuntu's hard drive?

---

### Post by werries on 2008-05-28
easiest way would be using the livecd w/ gparted.

---

### Post by Lanc1988 on 2008-05-28
how do i do that? i have the live cd but i dont know what to do with it to get to the gparted.

---

### Post by k3lt01 on 2008-05-28
If you are going to re-install Vista onto that drive then use the Vista disk and follow the prompts. It will show you what drives are on the machine and you then select the 2nd drive and reformat it.

---

### Post by Lanc1988 on 2008-05-29
i would rather not reinstall vista yet, i was hoping to reformat the ubuntu drive first so i could move about 15gb of files to it and then install vista.

anyway, i found the gparted and i deleted the ubuntu partition but it wont let me delete the 'linux-swap' and 'extended' partitions, they have a lock next to them.

---

### Post by werries on 2008-05-29
thats because they're in use. right click on the swap partition entry and click "Swap Off", then you can delete them.

---

### Post by k3lt01 on 2008-05-29
> **Lanc1988 said:**
> i would rather not reinstall vista yet, i was hoping to reformat the ubuntu drive first so i could move about 15gb of files to it and then install vista.You don't have to reinstall Vista at all, all you need to do is use the Vista disk and follow the instructions to format the appropriate drive. You could use a Win 2000 disk or NT4 disk to do the exact same thing and the NTFS format is native to Windows.

---

