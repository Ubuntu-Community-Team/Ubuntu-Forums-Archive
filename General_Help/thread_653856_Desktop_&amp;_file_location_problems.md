---
title: "Desktop &amp; file location problems"
date: 2007-12-30
forum: General Help
---

### Post by jhamric on 2007-12-30
I used the Configuration manager to add the Home icon to my desktop. When I opened up the icon, my desktop was suddenly populated with the graphics files, folders and several "."folders . In addition I lost my internet/network connection. I can delete them from the desktop, but they also disappear from the Home/user folder.

How can I restore the files to the original locations and recover my original desktop?

---

### Post by Vixis on 2007-12-30
in the terminal:
```
gconf-editor
```

check:
```
/apps/nautilus/desktop/home_icon_visible
/apps/nautilus/desktop/network_icon_visible
```


unckeck:
```
/apps/nautilus/preferences/desktop_is_home_dir
```

---

### Post by jhamric on 2007-12-30
Thanks Vixis for the reply.

 Tried your suggestion, but it didn't do anything. I still have all the graphics files that were in my home/user folder on the desktop along with all sorts of "." folders (e.g., .beryl, .config, etc.)  I have no idea what happened or what I did.

How can I move these files back to where they belong and how can I tell where they go?

---

### Post by jhamric on 2008-01-01
Solved the rash of desktop files by unchecking & re-checking the "Show desktop" option! That cleared off the desktop of the unwanted files. Guess the "." files are the user system hidden files that I never realized were there because I usually have the "Hide System Files" option checked in the file viewer.

The only bad thing is that I lost my wireless connection & I haven't figured out hoe to get it back :(

---

