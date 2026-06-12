---
title: "how do you empty trash from mounted network shares?"
date: 2006-12-03
forum: General Help
---

### Post by spudley on 2006-12-03
I still have files in my 'trash' can that won't empty through the usual methods.

My windows machines don't show files in the trash directory on the disk but Ubuntu does.  Not sure if there is some quirk on the go or not, but I'd still like to get rid of either the files on the disk (if they are there) and/or the ubuntu system showing files in the trash can.

Thanks!

---

### Post by aysiu on 2006-12-03
If you're using Gnome, the trash can files live in /home/spudley/.Trash

---

### Post by spudley on 2006-12-03
> **aysiu said:**
> If you're using Gnome, the trash can files live in /home/spudley/.Trash

Except for the mounts correct?  Because my trash still shows files deleted from my mounted network shares (SMBFS).

Example: /media/nasDisk/.trash-spudley
- that shows 3 files, 3 directories

When I click the trash can icon, it shows lots of files, emptying the trash, deletes all from /home/spudley/.Trash - but NOT the /mdia/nasDisk/.trash-spudley directory.

Those files and directories still remain, and my trash bin still shows files in it....

Thanks for the try though.. any other thoughts?

---

### Post by aysiu on 2006-12-03
Couldn't you force remove those items with this command? ```
sudo rm -r /media/nasDisk/.trash-spudley/*
```

---

