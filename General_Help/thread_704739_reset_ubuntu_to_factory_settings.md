---
title: "reset ubuntu to factory settings"
date: 2008-02-22
forum: General Help
---

### Post by ajkiwi88 on 2008-02-22
ok so i finaly got ubuntu working fully on my laptop but then i started playing around with settings and the text has messed up and also their is a lot of packages which i have installed and dont want anymore think i have removed most of them but is there any way to reset the system back to when i first installed it?

---

### Post by lifewithryan on 2008-02-22
To be honest, I think you're out of luck with that one.  I could be wrong, but I don't think there's a way to do what you're asking short of reinstalling.  (Or going through the various configs on the apps that are "messed up" and seeing if they have a Reset to Defaults under their options...but that sounds like more of a pain than a  quick reinstall).

---

### Post by Crooksey on 2008-02-22
They are just user edited settings, so just run...

```

rm -rf ~/.*
```

---

### Post by samkline on 2008-02-22
In synaptic package manager, if you go to "File -> History" and then you can see what you installed and when.

If you  want to clear all the settings you've changed, you can do [FONT="Courier New"]sudo rm -rf ~/.*[/FONT] but be careful that you've typed it correctly and know that it will delete ***all*** of your settings (including, for example, Firefox bookmarks, etc).

---

### Post by cdtech on 2008-02-22
If you really want to start from new, just reinstall. It wont take that long to do, then your really sure its back to original.

---

### Post by phyrewall on 2008-04-09
> **cdtech said:**
> If you really want to start from new, just reinstall. It wont take that long to do, then your really sure its back to original.

That won't work if you've got your /HOME on a different partition. Unless, of course, you let the installer re-partition the whole drive.

Couldn't you... create a new user and use that profile instead? Wouldn't that be at defaults? After all, if the OP wanted to reset system settings, rm'ing ~ wouldn't affect system settings (/etc/*).

---

