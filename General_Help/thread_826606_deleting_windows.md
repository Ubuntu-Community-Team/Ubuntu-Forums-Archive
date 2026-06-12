---
title: "deleting windows"
date: 2008-06-12
forum: General Help
---

### Post by daberger on 2008-06-12
well i got a nice little xubuntu install goin on but i am VERY low on disk space. on a 30g hdd i have a 4g xubuntu install but windows is MASSIVE
and i really dont think its the media i have bcuz ive deleted all of that

basically can i delete windows wihtout havin to download another ISO and burn it

---

### Post by abhiroopb on 2008-06-12
If you are happy with ubuntu and you JUST want to delete the windows isntall do the following:

sudo gparted

This will open up the partition editor.
Look for the partition that has NTFS written next to it (if you are unsure take a screenshot and post it).

Hit delete, and apply.

---

### Post by ago on 2008-06-12
> **abhiroopb said:**
> This will open up the partition editor.
Look for the partition that has NTFS written next to it (if you are unsure take a screenshot and post it).

If wubi is sitting on it, it is not going to work to well...
You will have to move wubi to a dedicated partition with LVPM or wubiguide script first.
It is easier just to install from CD and take over the disk

---

