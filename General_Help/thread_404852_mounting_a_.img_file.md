---
title: "mounting a .img file"
date: 2007-04-09
forum: General Help
---

### Post by darthc0da on 2007-04-09
hey, i recently installed ubuntu and have worked with linux for a while. Well, it killed my windows installation so i used ntfsclone to copy the windows partition onto another computer. So, i now have an ntfs.img on another computer. How do I mount it? I can't figure out how to do it with the knowledge I have now.

---

### Post by aysiu on 2007-04-09
I'm about 90% sure you do it this way, but I'm not 100% sure. You may want to wait for someone more knowledgeable to jump in.

Go to [the terminal](http://www.psychocats.net/ubuntu/terminal) and type ```
sudo mkdir /recovery
sudo mount -t ntfs /path/to/ntfs.img /recovery -o nls=utf8,umask=000
cd /recovery
ls
``` Of course, since you said the *ntfs.img* file is on another computer, you'll have to figure out what that /path/to is... maybe some kind of smb://#.#.#.#

---

