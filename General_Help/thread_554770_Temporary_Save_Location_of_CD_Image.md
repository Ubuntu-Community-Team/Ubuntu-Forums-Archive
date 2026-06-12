---
title: "Temporary Save Location of CD Image"
date: 2007-09-19
forum: General Help
---

### Post by Baufo on 2007-09-19
I started copying a CD but canceled while it was still creating the disc image (I only have one CD drive). Looking at the free space counter afterwards I noticed that some free space (about the size of the CD) had mysteriously vanished. So I guess this CD image was not deleted and is still somewhere on my hard disk. I wonder if anyone could tell me where these temporary images are saved so I can remove it manually?

Thanks in advance,
Baufo

---

### Post by tszanon on 2007-09-19
I think it depends on the program you were using. I know that k3b writes everything to /tmp, unless you specify another location. But probably it's under /tmp or you home folder.

---

### Post by Baufo on 2007-09-19
I used what I found preinstalled on Feisty Fawn. (Just right-clicked on the CD icon and chose copy.)

---

### Post by tszanon on 2007-09-19
> **Baufo said:**
> I used what I found preinstalled on Feisty Fawn. (Just right-clicked on the CD icon and chose copy.)
I'm using Dapper. When I right click on cd icon > Copy disk, a dialog box appears. If I choose "ISO Image", it asks me where I want to save the image. If I choose the cd recorder, it saves the image in /tmp. The file name was /tmp/image.iso.iSQspU. Of course, that suffix "iSQspU" is random.

So, in Feisty, probably the image is also saved in /tmp. :)

---

