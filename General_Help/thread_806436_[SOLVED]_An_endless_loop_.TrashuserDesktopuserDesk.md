---
title: "[SOLVED] An endless loop /.Trash/user/Desktop/user/Desktop"
date: 2008-05-24
forum: General Help
---

### Post by tich on 2008-05-24
i created a link or maybe re-created (accidently) my user folder (/home/user name) on my desktop.  then, realising that i had gone about creating it incorrectly i deleted it to the .Trash folder (or more colloquially, i deleted it).

whenever i try to empty the trash it is unable to delete this folder because it is something between an endless loop and a ghost.
an endless loop because opening the folder seems to go back and forth between two folders infinitely the user folder and the Desktop.  inside of the user folder is the Desktop and in the Desktop folder is the user.
(ending up with something as in the title)
and a ghost because it only shows up when i click the sidebar link to the trash.  if i navigate to the .Trash folder in nautilus (or gksudo nautilus) it doesn't show up.

if i attempt to move it out of the trash i get an error saying that the folder doesn't exist.

usually i would say that this is a minor annoyance and nothing to be concerned with but whenever i try to empty the trash nautilus seems to colapse.

is there some way i can go about removing this loopy ghost?

---

### Post by strabes on 2008-05-24
```
sudo rm -r ~/.local/share/Trash/files/*
```

Be careful with this command. Don't mess it up. Just paste it into the command line (by highlighting it and using middle click to paste the selection).

---

### Post by tich on 2008-05-25
> **strabes said:**
> ```
sudo rm -r ~/.local/share/Trash/files/*
```

Be careful with this command. Don't mess it up. Just paste it into the command line (by highlighting it and using middle click to paste the selection).

i have heard myths about this command... legends about its destructive powers.
what exactly does it do?

edit:
what does it do?... well it does that trick that's for sure!  as was nervous to use the command but it worked like a charm.

thanks strabes.

---

### Post by werries on 2008-05-25
sudo grants admin.
rm removes files.
-r enables removal of directories.
-f forces.
sudo rm -rf used incorrectly has the power to delete everything.
sudo rm -r may be essential here.

---

