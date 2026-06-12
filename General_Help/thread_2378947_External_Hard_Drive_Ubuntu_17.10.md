---
title: "External Hard Drive Ubuntu 17.10"
date: 2017-11-29
forum: General Help
---

### Post by Howie Williams on 2017-11-29
Hi, I upgraded to 17.10 yesterday and though I selected to install keeping my present files it did a complete fresh install. I had backed up my files to external hard drive but when I mount it it shows up as a text icon on the desktop. I can open that and my files are there, The problem comes when trying to copy files from ExHD to folder. It says there is not enough space when there is over 160Gb available. Its as if the ExHD has actually downloaded on to my laptop.

---

### Post by oldfred on 2017-11-29
With external drive mounted post these:
sudo parted -l
df -h

---

