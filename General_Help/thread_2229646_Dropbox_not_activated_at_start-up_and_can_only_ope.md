---
title: "Dropbox not activated at start-up and can only open via terminal."
date: 2014-06-14
forum: General Help
---

### Post by Mike1977 on 2014-06-14
Ubuntu 14.04 unity.
So I recently installed Dropbox via command:
```
***cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -***
```

Then I run:
```
***~/.dropbox-dist/dropboxd ***
```
  I got a log in window, and it created Dropbox folders in my home directory. However, whenever I start up computer, I have to run:
```
[I][B]~/.dropbox-dist/dropboxd 
   
[/B][/I]
```
to open or sync dropbox. After which I get an error message```
(dropbox:7543): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
```
 Until I do that I have no icon in toolbar.
I see Dropbox in software center for Gnome. I'm on Unity. How do I get Dropbox to sync and run on startup?

---

