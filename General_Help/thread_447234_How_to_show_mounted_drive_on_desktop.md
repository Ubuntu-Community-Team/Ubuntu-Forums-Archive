---
title: "How to show mounted drive on desktop"
date: 2007-05-17
forum: General Help
---

### Post by forchessonly on 2007-05-17
I have a new hard drive that works great. I can access it in /media/hda1/. Only problem is I'd like a link to the drive on my desktop and I can't figure out how.

Anyone know how to get the drive to show up on my desktop?

Thanks

---

### Post by mikewhatever on 2007-05-17
Alt+F2 and type gconf-editor
Navigate to apps/nautilus/desktop and check the box for 'volumes visible'.

---

### Post by crispy_420 on 2007-05-17
Even easier way:

If you can see it in Places -> Computer. Just drag to desktop. That should work for other locations too.

---

### Post by forchessonly on 2007-05-17
I didn't get a chance to try your all suggestions, I found something on another site that worked first. The drive was showing in the ubuntu disks manager and was accessible through /media/hda1 , but there was no entry for it in /etc/fstab/. So I followed a quick tutorial and made an fstab entry for it and now it shows on my desktop.

---

### Post by fragos on 2007-05-18
> **crispy_420 said:**
> Even easier way:

If you can see it in Places -> Computer. Just drag to desktop. That should work for other locations too.

Dragging to the desktop creates a folder and copies the files.  Changes on the drive or the folder wouldn't be synchronized.  I'm not sure that's what the poster wanted.

---

