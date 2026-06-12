---
title: "Mount External HD (Fat)"
date: 2008-06-30
forum: General Help
---

### Post by Snader on 2008-06-30
Hi there,

Due to some major problems, I'm now in Ubuntu on a LiveCD (Ubuntu 7.04). I'm trying to make a back-up of my files to an external harddrive (NTFS). The problem is. The harddrive appears automatically, but I don't have write permissions.

I tried opening nautilus as root, but it was still locked.

Changing permissions with:
```
sudo chmod -w /media/WD\ Combo
``` or
```
sudo chmod 777 /media/WD\ Combo
```
Gave me the error:
chmod: changing permissions of `/media/WD Combo': Read-only file system

Thanks for your time. Any help would be appreciated. :)

Sander

---

### Post by Snader on 2008-06-30
Sorry for bumping the thread. :) It is not my habit to do so. I'm a little desperate for an answer, because I have a party tonight and I need this machine for the music.

Again, thanks for your time.

---

### Post by Snader on 2008-06-30
Solved. Solution: Copied all the files to an NTFS partition, installed good old Windows and moved everything to the external HD. :)

Still... I would like to have an answer, so I can learn from this.

---

