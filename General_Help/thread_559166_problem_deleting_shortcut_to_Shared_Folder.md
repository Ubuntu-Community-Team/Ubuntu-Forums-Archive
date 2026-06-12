---
title: "problem deleting shortcut to Shared Folder"
date: 2007-09-24
forum: General Help
---

### Post by tmetzcc325 on 2007-09-24
Hi all,

I have two computers, one running Ubuntu Feisty, and the other WinXP.  I have a shared documents folder on the windows box that I use to share fies with the Ubuntu box.  Obviously, this folder appears under Network/Windows Network/etc...

The problem I am having is that I made a link to that folder on my desktop on the ubuntu box, but when I attempt to delete it (graphically) I get this message:

"/home/tom/...esktop.ini" cannot be deleted because you do not have permissions to modify its parent folder."

I have tried running a root shell and removing the directory as well, but no dice...any idea how I can delete this stupid thing?

Thanks,
Tom

---

### Post by qpieus on 2007-09-24
Please post the commands you used to try to delete the link, maybe there was an error there.
Also go into a terminal and type```
ls -la ~/Desktop
```
and post the results here and also identify which file you want to get rid of. Links will have a lowercase L at the beginning of the line, like this

```
lrwxrwxrwx   1 joe joe        32 2007-08-31 21:05 .thunderbird -> home/joe/.mozilla-thunderbird
```

---

