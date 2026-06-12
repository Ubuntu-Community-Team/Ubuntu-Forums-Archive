---
title: "How do I extend my Ubuntu ext4 partition?"
date: 2013-02-18
forum: General Help
---

### Post by Redronn on 2013-02-18
I have unallocated space after my ext4 partition at the end, and I want to combine them.

HOW?! ](*,)

---

### Post by dcstar on 2013-02-18
> **Redronn said:**
> I have unallocated space after my ext4 partition at the end, and I want to combine them.

HOW?! ](*,)

Do a search and pick one of the hundreds of existing threads that already exist explaining how to do it.

---

### Post by sudodus on 2013-02-18
> **Redronn said:**
> I have unallocated space after my ext4 partition at the end, and I want to combine them.

HOW?! ](*,)

There is always a risk of destroying data when you are editing partitions, so I suggest that you ***start by backing up your data*** on that drive to an external drive.

Then boot from another drive, for example from your Ubuntu install CD or USB drive. Use ***gparted*** a tool with graphical user interface to do it. It is rather easy, can be done either via the pull-down menus, via right-clicking or even by 'dragging the border of the partition' with the cursor until the unallocated space is used.

But this is only indicating your intent. You need to click on the tick icon at the top of the gparted window, to start performing the task(s).

---

