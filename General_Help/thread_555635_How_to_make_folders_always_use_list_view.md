---
title: "How to make folders always use list view?"
date: 2007-09-20
forum: General Help
---

### Post by MegaSvensk on 2007-09-20
Hi,

Is there is any way I can make Ubuntu's file manager always display folder contents in list view? Because I prefer having it like that.

---

### Post by notwen on 2007-09-20
Unfortunately I don't have access to a Linux box here at work, but you may want to give gnome configuration editor a shot.  Type the following in a terminal and browse around your options in apps--->nautilus:

```
gconf-editor
```

Post back and let me know if you find anything. =]

---

### Post by orangey on 2007-09-20
notwen, you are great.  This had always bugged me but I never got around to figuring out how to fix it.  MegaSvensk posted the question, I tried your suggestion and the setting is right there.

Its in "app -> nautilus -> preferences -> default folder viewer".  Set that to list_view.  Done.

Edit: On a related question, how can you stop it from trying to generate thumbnails?
Edit2: Nevermind, also in preferences.  Set "show_image_thumbnail" to "never".  Done.

---

### Post by notwen on 2007-09-20
Cool, glad I didn't point you guys in the wrong direction. =]  If it's gnome related, you can just about always bet there's an option for it in gconf-editor.

---

### Post by Wolki on 2007-09-20
These options should also be available in the nautilus preferences (Edit -> Preferences), first tab for default view, fifth tab for thumbnails.

---

### Post by bdlyon on 2008-02-02
Thanks all of you for this! I have been annoyed by the folder view ever since loading Ubuntu and had spent considerable time looking for a file view preferences window with no luck. Your fix did the trick.

This should be something put into future versions of Ubuntu, something loaded by default to give the user quick and easy configuration of the folder and file view defaults.

Thanks again. You guys rock.
--Bruce

---

### Post by Ink-Jet on 2008-02-02
A very good idea is to keep root user as icons, with normal account as list.
It helps withf remembering that you could very easily mess things up.

---

