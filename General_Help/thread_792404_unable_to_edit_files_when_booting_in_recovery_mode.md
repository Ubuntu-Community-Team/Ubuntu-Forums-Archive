---
title: "unable to edit files when booting in recovery mode..."
date: 2008-05-12
forum: General Help
---

### Post by Mia_tech on 2008-05-12
I'm trying to edit the xorg.conf file when booting in recovery mode the only problem is that it won't let me it says that the file is a read only file....I'm using nano for this
any help appreciated..

thanks

---

### Post by MaindotC on 2008-05-12
Did you log in as root?

---

### Post by Mia_tech on 2008-05-12
> **strAlan said:**
> Did you log in as root?

when you boot into recovery mode the shell you get is something like

root@thispc$

or something similar, I'm assuming I'm logged in as root at that time, but still can't make changes to files
correct me if I'm wrong.

thanks

---

### Post by MaindotC on 2008-05-12
You should be logged in as root, unless you made your username "root" or something wacky like that.  Try preceding your commands with sudo.  Also, try this method of copying the file, making the changes you need, then moving it back so it is referenced as xorg.conf:

```

cp xorg.conf xorg.conf.edit

```
Edit the xorg.conf.edit file using nano as you wish.
```

cp xorg.conf xorg.conf.backup

```
Here's a backup just in case something goes awry.
```

mv xorg.conf.edit xorg.conf

```

This may give you an error if it will not let you replace xorg.conf with the file you edited.  If it does allow you, restart your x-server or from the recovery console you can reboot.

---

### Post by MaindotC on 2008-05-20
Mia what's the status on this issue?  Does your display work alright?

---

