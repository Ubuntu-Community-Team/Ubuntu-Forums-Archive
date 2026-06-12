---
title: "/home/&lt;user&gt;/.thumbnails  - Overpopulation?"
date: 2014-10-30
forum: General Help
---

### Post by EnglishElectricAndy on 2014-10-30
Having experienced some difficulties with the thumbnail generating process 'tumblerd' hogging CPU capacity I searched around, and among other things, I found out that the directory in this thread title retains thumbnails for stuff that I've long since deleted or moved to an external drive.

I'm assuming I can safely delete these thumbnails since the original files/directories no longer exist on this machines disk, and I can access them elsewhere.

What I'm puzzled by though, is why these thumbnails are retained after the originating directories/files are no longer present?

---

### Post by EnglishElectricAndy on 2014-10-30
Addendum: my /home/<user>/.thumbnail directory currently stands at 1.4GB!! :shock:

---

### Post by Habitual on 2014-10-30
I'd nuke 'em to orbit if my ~/.thumbnails directory were that large.

---

### Post by EnglishElectricAndy on 2014-10-30
Yes, 73,000 of the blighters! Music videos and albums, films, lots of stuff that I'd either deleted because they weren't to my taste or moved to an external drive for saving.

Still, I now know to keep an eye on this directory. One lives and learns...

---

### Post by ibjsb4 on 2014-10-30
Install dconf-tools and see if your default setting has been changed.
[ATTACH=CONFIG]257624[/ATTACH]

---

### Post by EnglishElectricAndy on 2014-11-01
> **ibjsb4 said:**
> Install dconf-tools and see if your default setting has been changed.
[ATTACH=CONFIG]257624[/ATTACH]

Thanks for that, looks like being a handy utility. Experimentally, I've changed the cache retention setting to 7 days to see if that reduces the overpopulation.

---

