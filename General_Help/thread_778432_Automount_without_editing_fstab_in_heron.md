---
title: "Automount without editing fstab in heron?"
date: 2008-05-02
forum: General Help
---

### Post by vdawg on 2008-05-02
Hi there, another question...

On the new hardy heron, there is a policy saying that internal media is non mounted... I gave my account full priviliges and if I try to access an internal drive it gets mounted. However I would like the mounting to happen right as I login as all my data is shared with windblows so inevitably I will be having to mount the drive.

So short of editing the fstab to mount automatically, is there another solution?

---

### Post by Zorael on 2008-05-02
Subscribing and tagging for interest, inquiring minds want to know.

The solution I picked was to mount it in fstab, yes. I mounted the drive to /media/windows, and then did mount --binds to share key directories between OSs. Particularly ~/desktop to /media/windows/Documents\040and\040Settings/Zorael/Desktop, heh. I also tried out /media/windows/Documents\040and\040Settings/Zorael/Application\040Data/Mozilla/Firefox mounted to ~/.mozilla/firefox for a while, but I had to redo paths every time I booted into the other OS, so not really recommended.

---

### Post by clint1010 on 2008-05-30
if its an NTFS drive then try ntfs-config

see [this thread]("http://ubuntuforums.org/showthread.php?t=785263") for info

---

