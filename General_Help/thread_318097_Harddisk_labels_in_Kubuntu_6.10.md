---
title: "Harddisk labels in Kubuntu 6.10?"
date: 2006-12-13
forum: General Help
---

### Post by Morientes on 2006-12-13
When Kubuntu mounts my harddisks, they do not have their correct label e.g. "Games". Insted they are called hdc5 and so on. How do I make their labels appear insted of the hdc5 name?

---

### Post by klmklm1967 on 2006-12-13
Look in your /media folder.

You'll probably see an entry for hdc5.

What you want to do is:

Unmount the drive you refer to as "Games" but ubuntu refers to as "hdc5"

In the /media folder, create a new folder called "Games" (without quotes)

Then, modify your fstab file to point not to /media/hdc5 but to /media/games

The command for that would be:

sudo nano /etc/fstab
(replace nano with your favorite editor, such as Gedit or Kate or *cough* Vi)

Locate the line that looks like:

/dev/hdc1     /media/**hdc1**  morestuffherethatyoudontchange

change the bolded entry to "Games" (no quotes and it is case-sensitive)

---

### Post by Morientes on 2006-12-13
Thank you, but is there no way of making it read the labels itself and do it automatically? Ubuntu 6.10 does this, I know...

---

