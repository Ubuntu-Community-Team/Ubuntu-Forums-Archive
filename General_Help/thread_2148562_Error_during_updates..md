---
title: "Error during updates."
date: 2013-05-25
forum: General Help
---

### Post by Silvernail on 2013-05-25
Ubuntu 12.04
Gnome3

When i get update notices and use the command ```
gksudo update-manager
``` in a terminal to install them, I get a long list of this message:
```

(update-manager:6093): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint

```
Should I worry about it or is there a way to correct it.

---

### Post by ibjsb4 on 2013-05-25
Its just a warning, nothing to worry about.  When using gksudo gtk warnings will appear.

Why are you using terminal to bring up the GUI?  Why not just ..

```
sudo apt-get update
sudo apt-get upgrade
```

If you want to also upgrade the kernel ..

```
sudo apt-get dist-upgrade
```

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Silvernail on 2013-05-26
> **ibjsb4 said:**
> 
Why are you using terminal to bring up the GUI? 
I was having errors in another application I called from the command line, someone said to use gkedit.

This was an extremely helpful link, thanks for posting.
> 
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Silvernail on 2013-05-30
I would like to mark this thread solved but how do I do that since the update?

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]Silvernail;[/COLOR]

Pleasing that ya got it worked out, See the link in my sig for continued education and please visit:
[http://ubuntuforums.org/showthread.php?t=2110857&page=1](http://ubuntuforums.org/showthread.php?t=2110857&page=1) and leave a commit.
Interim method to mark as solved:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT]
enjoy

[/INDENT]

---

