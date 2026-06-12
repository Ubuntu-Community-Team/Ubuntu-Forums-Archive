---
title: "K3b's Temporary Directory in &quot;File System&quot; Section?"
date: 2008-01-03
forum: General Help
---

### Post by neilrizo on 2008-01-03
Would it be possible to put K3b's Default Temporary Directory in the "File System" Section of Ubuntu?

Please refer to the attached image to see what I mean by Ubuntu's "File System" Section.

---

### Post by p_quarles on 2008-01-03
Not without running K3b as root. Is there any specific reason you're trying to do this?

---

### Post by neilrizo on 2008-01-03
> **p_quarles said:**
> Not without running K3b as root. Is there any specific reason you're trying to do this?

I've noticed that I can't burn a DVD on K3b unless I have the same amount of free space on my "Home Folder". Since I've only got 1GB free on this folder and 6GB free in my "File System" I'm thinking of moving the temporary folder there.

How can I run K3b as root?

---

### Post by p_quarles on 2008-01-03
Only 1 GB free in the home folder? That's dangerously low, actually. You really don't want to see what happens when Ubuntu runs out of disk space on a given partition. I'd suggest freeing up some space, or expanding the home partition.

As for running K3b as root, you would do like so:
```
kdesu k3b
```
Or "gksudo k3b" if you're using K3b in Gnome or Xfce. I would strongly advise against doing this, however, as it's generally a bad practice to run programs as root when you don't need expanded privileges.

---

### Post by neilrizo on 2008-01-03
> **p_quarles said:**
> Only 1 GB free in the home folder? That's dangerously low, actually. You really don't want to see what happens when Ubuntu runs out of disk space on a given partition. I'd suggest freeing up some space, or expanding the home partition.

As for running K3b as root, you would do like so:
```
kdesu k3b
```
Or "gksudo k3b" if you're using K3b in Gnome or Xfce. I would strongly advise against doing this, however, as it's generally a bad practice to run programs as root when you don't need expanded privileges.

Thanks for the info.

And just as a follow-up, how much free space should I have on my home folder at a given time?

---

