---
title: "Don't have permission to empty some files from trash"
date: 2008-05-04
forum: General Help
---

### Post by Bari on 2008-05-04
Hi,  I have been playing with Wine and one of the programmes I tried running didn't work so I uninstalled it. It didn't get rid of all of the folders so I shifted them to the trash (bottom right hand corner of the screen) However I now can't empty the trash as it says I don't have the necessary permissions. I assume this is because some of the files are .exe ones.  can anyone please tell me the necessary command to put after sudo in the terminal so I can free up some space.
 Apologies for this post I should have searched before posting all sorted now.

---

### Post by ghost_ryder35 on 2008-05-04
Just an FYI for anyone else in this boat
Pre Hardy 8.04
```

sudo rm -rf ~/.Trash/*

```
Hardy 8.04
```

sudo rm -fr ~/.local/share/Trash/files/*

```
edit: stole the hardy one from sisco311's post ;)

---

### Post by sisco311 on 2008-05-04
Try this:
[http://ubuntuforums.org/showpost.php?p=4861760&postcount=4](http://ubuntuforums.org/showpost.php?p=4861760&postcount=4)

---

### Post by raven302 on 2008-05-04
Oh wow thanks! Had this problem as well.

---

