---
title: "Can't write to my file system and it's causing problems"
date: 2008-04-22
forum: General Help
---

### Post by Jarramundi on 2008-04-22
Hi guys, I'm having a wee problem with Gutsy (I'm sure it's solvable by someone with a bit more exp. than me.

When I'm surfing around in my file system in X I can't Write to any files even as admin, I have to open a terminal and su everything which is a bit of a pain. Also.. I'm trying to play a game called egoboo, but I can't get past the first level because egoboo can't export anything to the file system /usr/share/egoboo. I expect it's because it doesn't have permissions. In fact even when I try to start the game in Konsole I must be root before it will launch, so I can't create a menu item for it, it does nothing. Is there something I'm missing? Please help.

---

### Post by Jarramundi on 2008-04-22
*bump* anyone?

---

### Post by 3rdalbum on 2008-04-22
I don't know too much about Xubuntu, but the reason why you can't modify files in the filesystem without being root is because of basic Linux security systems. You can create a custom application launcher on your XFCE panel to bring up a root file browser. Use the following command in the launcher:

```
gksudo thunar
```

As for Egoboo, try the following command:

```
sudo chmod a+rw /usr/share/egoboo
```

Sudo gives administrator privileges, chmod is the name of the command, "a" stands for "all users", the + says "add the following privileges", rw stands for "read and write".

(note: There is a GUI way to do it, but I'm not familiar enough with Xubuntu to be able to walk you through it).

---

### Post by Jarramundi on 2008-04-22
Thanks! :)
Do I need to gksudo thunar everytime?

---

