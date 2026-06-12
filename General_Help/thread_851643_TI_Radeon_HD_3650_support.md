---
title: "TI Radeon HD 3650 support"
date: 2008-07-06
forum: General Help
---

### Post by josephmo on 2008-07-06
My monitor supports 1680x1050 resolution, and I have an ATI Radeon HD 3650 card with 512MB RAM. I downloaded the ATI driver, and tried to double click on it (it has a .run extension), but nothing happens. I am a Windows user, just installed UBUNTU. What do I do to get this driver installed, and should I expect any issues with support for the ATI 3650?

---

### Post by AlyCat on 2008-07-07
try opening a terminal and typing chmod +x *name of file* and press enter. then use ./*name of file* to run it. remember to include the extension.

---

### Post by josephmo on 2008-07-07
It's telling me I need to be logged in as a super-user to run it.

---

### Post by PetruM on 2008-07-07
Then just add **sudo** before the command. :D
**sudo** allows you to run programs as super-user/root, but be careful when using it. :)

---

### Post by josephmo on 2008-07-07
> **PetruM said:**
> Then just add **sudo** before the command. :D
**sudo** allows you to run programs as super-user/root, but be careful when using it. :)


It's telling me "command not found"

---

### Post by edwinw on 2008-07-07
Usually when you download a file, the default location will be the desktop.  However when you log into a terminal, by default you will be in the user home directory.  So try these commands once you open a terminal - first change the directory:

```

cd Desktop

```

Change the permission of the file to make it executable as stated earlier:

```

sudo chmod +x <<name of downloaded file>>

```

Then run it:

```

sudo sh ./<<name of downloaded file>>

```

Hope this helps!

---

