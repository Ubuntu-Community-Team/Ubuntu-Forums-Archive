---
title: "[SOLVED] Ubuntu deleting files (in Windows) without clearing HD space"
date: 2008-02-28
forum: General Help
---

### Post by Pepperonipizza on 2008-02-28
Here's the thing:

I was in running Ubuntu and browsing through some of my files I have on the partition of my HD where I put my Windows files. I copied 5 GB worth of files onto an Ubuntu folder. That went good. Then I went to the folder that was "in Windows" (it was a submap of my usermap in windows) and selected the files I had just copied and pressed the "delete" button.

Waah! Nothing anymore in the folder, but no space cleared on the disk either! Where did the files go then? Did I manage to just lose 5 GB capacity of my HD by doing something very stupid?

PS: Don't ask me why I didn't just cut and paste. It makes me feel stupid (and I don't want to be reminded of that lol) :-P

Anyways, thanks for all help in advance,
Pepperonipizza

---

### Post by Islington on 2008-02-28
check your trash they might be in there.

---

### Post by Pepperonipizza on 2008-02-28
Nope, checked both Windows and Ubuntu trash folders. Not in there

---

### Post by froy02 on 2008-02-28
Try changing the option in Nautilus to show hidden files then look for a directory name .Trash in that drive.  If I am not mistaken the deleted files on ntfs partition do not go to the regular trash in Ubuntu.  They stay in that drive and are stored in .Trash directory.  You can then just delete that '.Trash' directory.

---

### Post by Pepperonipizza on 2008-02-29
You're right. It was a subfolder in the /media/disk folder, named ".Trash-*username*". I just deleted all files in there (and deleted the folder althogether) and now I've got my space back! Yihaa, thank you!

---

