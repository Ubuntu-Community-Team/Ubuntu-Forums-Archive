---
title: "desktop icons broken? Along with image viewer?"
date: 2007-09-22
forum: General Help
---

### Post by Rapax on 2007-09-22
Hi guys

I was fiddling with compiz, trying to get it to work (I've posted elsewhere about that), and I seem to somehow have broken my desktop icons.

They're still there, in principle, but they now all show the extension '.desktop', and have a standard empty file icon instead of the correct ones. They also no longer work as launchers, opening the contents of the actual .desktop file in an editor instead.
The same applies to any new launchers I create.
Alos, and probably connected: For any .gif .png or .jpg file, when i try to open it, I get the following:
"No application suitable for automatic installation is available for handling this kind of file."
Similar behaviour when I try to assign an icon to the .desktop files. The requester window opens, but does not display any image files.

This is weird. Can anyone help?

---

### Post by Rapax on 2007-09-22
Another detail:
Opening image files in some other tool, such as EyeOfGnome or Gimp works fine. But it seem like whatever Gnome relies on, isn't working.

---

### Post by Rapax on 2007-09-23
Can someone tell me what Gnome uses per default to display images such as icons? Maybe I can reinstall that package.

---

### Post by Wolki on 2007-09-23
Looks like you broke your mime-type settings.

Is ubuntu-desktop installed?

If yes, try creating and logging in as another user. Does the problem persist? If not, it might be a problematic configuration file in your .local/ folder, try renaming the folder to .local-backup and let it get regenerated.

---

