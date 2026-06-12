---
title: "a way to change file view"
date: 2014-06-11
forum: General Help
---

### Post by jgw on 2014-06-11
Is there a command which will change the default file view from icons to list?

Thank you...............

---

### Post by ajgreeny on 2014-06-11
If you go to the View menu item it may tell you what the keyboard shortcut is.  I use Xubuntu with thunar as file manager and in that it is Ctrl+1 for Icons, Ctrl+2 for detailed list and Ctrl+3 for compact list. so it is worth trying those, but I do not have nautilus to try it out.

---

### Post by jgw on 2014-06-11
Thanks for the reply.  The shortcut is not there.  Everytime I want a list I must goto view and then click on 'list'  there has to be a better way.  The best way would be to change the default.  Ubuntu will have a way to do that but its a bit secret <g>

---

### Post by Hazzabin on 2014-06-11
In Nautilus it's [COLOR=#000000] is Ctrl+1 for Icons, Ctrl+2 for list That's in Ubuntu 14.04 Unity[/COLOR]

---

### Post by steeldriver on 2014-06-11
In 12.04 you can change the default for nautilus using the graphical dconf editor (from package dconf-tools), or from the command line using

```

gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view'

```

Other variants may use different file managers (e.g. thunar, pcmanfm). The nautilus key / schema may have changed in later versions as things moved from gconf to dconf.

---

### Post by jgw on 2014-06-12
Thanks for the replies.  I eventually found the ^1 but setting the default is even better!

Thanks again!

---

