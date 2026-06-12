---
title: "How to change permissions?"
date: 2008-02-04
forum: General Help
---

### Post by LoneWolfUK on 2008-02-04
I am trying to delete a folder and it keeps saying I can't because "you do not have permissions to change it or its parent folder."

The owner of the folder is root.

I have done some searches on this and tried a few commands, but I can't seem to change permissions on this folder. I am still very new on Ubuntu and finding this very confusing.

If somebody could give me the correct command I would be very greatful.

It is not a system folder so shouldn't screw anything up.

Many thanks in advance.

---

### Post by stooshbunutu on 2008-02-04
If you are using terminal commands then try simply putting *sudo *before the command and then it will simply prompt for you password.

Else, try right click, porperties, permissions and try changing the owner to you rather than root (root is the administrator).

As a very very last resort if you desperately wish to delete the folder log-in as root with your initial set-up password, but this is not advised as if you do other things in root it could let you do something you shouldn't

Hope this helps :)

---

### Post by OffAxis on 2008-02-04
```
sudo rm  [/path/foldername]
```

rm = remove (file OR directory)
rmdir = remove EMPTY directory

**rm **works better than **rmdir **(if that's what you're using)

you can also use 
```
sudo rm -r [/path/foldername]
```

if there are files or subfolders within the folder you're trying to remove.

---

### Post by anaconda on 2008-02-04
or you could start nautilus (file-browser) with root rights with (in terminal):
sudo nautilus

---

