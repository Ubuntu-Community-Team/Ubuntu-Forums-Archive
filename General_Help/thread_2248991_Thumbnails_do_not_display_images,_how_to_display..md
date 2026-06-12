---
title: "Thumbnails do not display images, how to display."
date: 2014-10-18
forum: General Help
---

### Post by RT236 on 2014-10-18
On several occasions, new OS load, adding on disks, etc. sometimes thumbnails have not displayed the image, for example, of jpegs across my entire file structure. I've had this happen in nautilus and nemo. I just had this happen today when building up a system and adding disks and thought I would post a solution that has always worked for me across several releases of Ubuntu and also Mint. 

I have to give credit to whomever posted an obscure post once in a Google search describing a fix that worked for them. It's always worked for me and it's so simple.

It is not necessary to be root. One can do this just in the file manager. Go to <your home directory>/.cache and make a link for thumbnails.

Go back to your home directory and delete .thumbnails
Then, copy/paste the link you made into your home directory. I always reboot, and all of the images for the thumbnails will/should be present.

---

