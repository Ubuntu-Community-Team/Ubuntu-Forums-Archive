---
title: "Nautilus CD/DVD Creator from command line"
date: 2008-01-06
forum: General Help
---

### Post by Greasyfingers on 2008-01-06
I can run the Nautilus CD/DVD Creator from the command line or a script with ```
nautilus-cd-burner
``` but I can't figure out how to load a file into it. For example, this doesn't work...```
nautilus-cd-burner /path/to/file
```...it just brings up a message box saying "Unable to create CD/DVD - No files were selected."

Alternatively, I'd settle for bringing up the CD/DVD Creator file manager window with ```
nautilus burn:///
``` but again I can't see how to load a file into it.

Setting the 'Disc name' field from the command line would be useful, too, if anyone knows how to do this?

---

### Post by jken146 on 2008-01-06
There are command line tools for burning CDs; **cdrecord** is what I think it's called (I would check, but I'm stuck using Vista atm :'( ).  Try reqding the man pages for the commands you want to run.
```
man cdrecord
```

---

### Post by Greasyfingers on 2008-01-06
> **jken146 said:**
> There are command line tools for burning CDs; **cdrecord** is what I think it's called

Yup; in fact I think most graphical interfaces (including Nautilus) are just front ends to cdrecord.

What I'm actually trying to do is bring up that graphical interface - with file(s) loaded - so that it'll fit in with a zenity driven script I'm trying to write.

I can do what I need with K3b (default in KDE), so maybe I should settle for that; but I'm more comfortable with the Nautilus version.

Man pages don't seem to be available.

---

### Post by deepclutch on 2008-01-06
cdrecord is now off the debian/ubuntu repos.the fork which is used is "wodim".
and nautilus burner support is for drag and drop i suppose.or press CTRL+L and enter burn:///

---

