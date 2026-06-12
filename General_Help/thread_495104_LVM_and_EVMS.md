---
title: "LVM and EVMS"
date: 2007-07-07
forum: General Help
---

### Post by GaryParr on 2007-07-07
I installed Feisty Fawn from the alternate CD because I wanted to create logical volumes. That and I didn't want to wait for the Live CD to load in order to start installing :-)  While I'm OK with running LVM commands from the command line (I have 2 edgy servers running right now with RAID and LVM) I was looking for an easy to use GUI for resizing and playing around with my logical volumes. I installed both the EVMS GUI (why isn't it in the package manager gui? had to do command line...) and also the LVM GUI as described in a forum post. I now have a few questions...

1) Why does the LVM GUI only offer Ext2 and Ext3 file systems? It doesn't recognize my ReiserFS file systems. This makes me afraid to use LVM GUI to do anything to my existing volumes... like resize!

2) Why does EVMS GUI not recognize the mounts for my volumes? If I mount a new volume through EVMS, running mount shows a mapping through evms instead of the regular mapper... I assume this is why EVMS doesn't recognize the existing mounts for /var and /home etc? This also makes me afraid to resize my existing volumes through the EVMS GUI.

3) is there a performance/stability difference between mounting through lvm and evms?

Thanks in advance for any help!

---

### Post by GaryParr on 2007-07-14
No one?

---

### Post by igoddard on 2007-07-28
Still no one?

What's the relationship between LVM & EVMS?

---

### Post by hotdoog on 2007-10-13
I am considering LVM. I've read that "EVMS is like LVM on steroids"
That's about all I know about it so far.
[http://ubuntuforums.org/showthread.php?t=70706]("http://ubuntuforums.org/showthread.php?t=70706")

---

