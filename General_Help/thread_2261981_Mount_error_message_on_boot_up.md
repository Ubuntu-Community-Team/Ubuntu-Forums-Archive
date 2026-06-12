---
title: "Mount error message on boot up"
date: 2015-01-22
forum: General Help
---

### Post by michael-piziak on 2015-01-22
When I booted up this morning, an error came across the screen stating that the disk drive was not ready yet and asked me if I wanted to wait, skip, or unmount (or mount I can't remember).

After waiting a few seconds, it booted right on into the desktop as usual.

I restarted to try to reproduce the error, but no luck.

Perhaps the HD is going bad?   Is there a utility that I can get in software center or that is already on my system to test the hard drive ?

---

### Post by deadflowr on 2015-01-22
Disks.
Already installed.
You can run some SMART tests.
It'll also tell you outright when you click on the hard disk(it lists all the connected storage devices so you need to select the hard drive)basic information about the disk.
Such as temp, how long it's been powered up, and the state of it's health, and among other things.

---

### Post by michael-piziak on 2015-01-22
Are you speaking of "disk utility"  ?
I don't see a file named "Disks" anywhere.

---

### Post by oldrocker99 on 2015-01-22
Here's what you need:
```
sudo apt-get install gnome-disk-utility
```

it can be found in the Accessories folder.

---

### Post by deadflowr on 2015-01-22
> **michael-piziak said:**
> Are you speaking of "disk utility"  ?
I don't see a file named "Disks" anywhere.

Assumptions on my part.
I'm unclear on which release, so yes if using 12.04 it's disk utility.
The name was  shortened to just Disks for newer releases, such as 14.04.

---

### Post by michael-piziak on 2015-01-22
> **oldrocker99 said:**
> Here's what you need:
```
sudo apt-get install gnome-disk-utility
```

it can be found in the Accessories folder.

I found disk utility and it says the hd is healthy.

BTW, where is the accessories folder?   I don't think I've ever seen that folder.

---

### Post by deadflowr on 2015-01-22
> **michael-piziak said:**
> I found disk utility and it says the hd is healthy.

BTW, where is the accessories folder?   I don't think I've ever seen that folder.

Accessories folder = classic gnome/ gnome-flashback, or mate.
I guess in unity you could filter it in the dash...

(Open the dash go to the applications icon/section, and then you should see a section/dropdown in the top right corner marked filters.
You can adjust it so that only certain things are shown (ie, games, intenet, accessories, et cetera et cetera)


Edit: It's highly possible that nothing was ever wrong with the disk, but maybe something didn't properly shutdown and so the fsck disk checking utility that Ubuntu uses to  help keep the file system clean, was 
invoked...

---

### Post by michael-piziak on 2015-01-22
Thanks, I had not noticed that filter option on the top right.

Marking this thread as solved.

---

