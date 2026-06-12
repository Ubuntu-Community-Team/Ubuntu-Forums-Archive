---
title: "Help with partitions and fstab"
date: 2007-01-22
forum: General Help
---

### Post by aretei on 2007-01-22
Can anyone tell me how to fix this problem?

[IMG]http://www.humanisticsociety.com/pics/Screenshot.png[/IMG]

Just as shown in the image, the places bar (on the left) in nautilus shows duplicate mount points for my USB drive, the mounted ones and unmounted ones. My fstab is shown on the right side of the screen. Basically what I want to do is fix as the way default ubuntu handles partitions and have it show the partitions as they are mounted and hide them when they are not mounted. I used [this guide]("http://www.ubuntuforums.org/showthread.php?t=283131") to fix my problems but I can't figure out what caused this to happen. Please help me out, thanks!

---

### Post by Shatrat on 2007-01-22
I dont think you need that stuff in your fstab, the hal daemon automatically mounts removable media.
Try commenting out all the fstab entries by putting a # in front of the lines that start with /dev/sbd* and plugging and unplugging one of your removable drives

I'm still not entirely sure what you've done or what you are wanting but hopefully this helps.

---

### Post by aretei on 2007-01-22
Thanks for the response. I guess that will do the job, but what I wanted to do was to set the label for each partition rather than have them appear as "usbdisk-*". Do you have any clue how I can do that?

---

### Post by bodhi.zazen on 2007-01-22
Hi aretei

I saw your other post and I only have a partial answer :(

Removable devices are managed by gnome-volume-manager (gvm) and as you know gvm is configured to select it's own mount point.

If you add you device to fstab, you can (should) use LABEL=<label> /mount_point however, in Edgy or Feisty you may need to use UUID= :p

But, the device will not auto mount :(

I do not know how to configure gvm to allow both auto mounting and setting the mount point.

Perhaps someone more knowledgeable then myself will respond.

HTH

---

### Post by aretei on 2007-01-22
Well maybe the quickest way is to simply hook up my USB drive to a Windows machine and rename my partitions as that is how my partitions were before. I believe then, the partition label becomes the name of the partition set under Windows. I'm just going through this problem because one of my partition had problems and so I formatted all 3 partitions. (I'm not even sure if I'm making my points explicit as I should be, but I thought in order to set the LABELS, you need to reformat the entire partition?)

---

### Post by bodhi.zazen on 2007-01-22
You do not need to re-format to set the label from Linux.

See the thread on "how to fstab", I wrote an entire section on how to label.

You can set a label without re-formatting.

---

### Post by aretei on 2007-01-22
Hey bodhi, everything seems to work the way I hoped, thank you so much for your help =D> :D :KS

---

