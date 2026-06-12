---
title: "Kubuntu Drive Icon Names"
date: 2007-07-09
forum: General Help
---

### Post by roastdawgg on 2007-07-09
I am running Feisty with the latest and greatest patches and updates. I have switched over to KDE from gnome and am loving every second of it. However I have an issue that I have been unable to find a resolution for. I have 3 ext3 partitions on a seperate hard drive that get automatically mounted and displayed on my desktop. I put the drives in the fstab and they mount to folders named mp3, downloads, storage. However when they display on the desktop they are named:

120 Gig (mp3)
210 Gig (downloads)
150 Gig (storage)

Why does KDE prepend the drive's size in the icon name? I just want it to be called what the mount point is. In the rest of the environment it is just referenced by the mount point name. Where can I go to turn off this labelling? 

And one more thing, How do I (can I) change the drive icon for each mounted drive independantly of the others? I thought I did but the icons I chose only show up in the file manager, they are all identicle on the desktop. I want each mounted drive to have a different icon on the desktop is this possible?

---

### Post by roastdawgg on 2007-07-11
So nobody has any idea how to fix this? Guess I will answer my own question. 

I fixed this issue by visiting each drive i wanted to have an icon for on my desktop in the konquerer file browser. I then dragged the icon from the address bar in konquerer to the desktop which prompted me with "move here" or "link here". I chose "link here" and voila, the drive is now linked on my desktop with the custom icon I chose. I then went into the desktop config and unchecked the option to show mounted drives on the desktop.

---

### Post by iceolate on 2007-08-18
So that's how you do it. I was messing with it for days.

---

