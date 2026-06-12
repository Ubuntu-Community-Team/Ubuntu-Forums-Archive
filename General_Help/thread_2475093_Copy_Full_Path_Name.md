---
title: "Copy Full Path Name"
date: 2022-05-16
forum: General Help
---

### Post by Quarkrad on 2022-05-16
Running Mate 22.04.  How do I copy the full name and path of a file via caja?  Pressing Ctrl C just copies the file name - I would like to be able to copy and then be able to paste the full path and file name - if possible(?).

---

### Post by yetimon_64 on 2022-05-16
That could be done with a small caja script in ~/.config/caja/scripts. I use this next script to extract full path and filename of any file in caja to a file on my desktop...
```
{
echo $(realpath "$1") >> $HOME/Desktop/realpath-names
}
```
Give it a name like "path-extractor", or something that suits you, make it executable and place it in "~/.config/caja/scripts".

Once set up it is as simple as right clicking any file in caja, choose the "Scripts" menu and use "path-extractor"; the full path and filename to the file you want to record will show up in a file on your desktop. Then you can copy/paste the path/filename from within the file on the desktop.

---

