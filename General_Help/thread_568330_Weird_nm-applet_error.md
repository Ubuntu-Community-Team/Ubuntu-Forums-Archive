---
title: "Weird nm-applet error"
date: 2007-10-05
forum: General Help
---

### Post by edfredcoder on 2007-10-05
Hi,
I just reinstalled my OS (got cracked, unfortunatly). I installed the network-manager-gnome package. When I start up nm-applet, I get some gtk errors, and then it dies. Here is the error: 
```

(nm-applet:14080): Gtk-WARNING **: Could not find the icon 'nm-no-connection'. The 'hicolor' theme
was not found either, perhaps you need to install it. 

```
I googled a bit, and found this proposed solution:
```

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

```
But that gives me the error:
```

No theme index file in '/usr/share/icons/hicolor'.
If you really want to create an icon cache here, use --ignore-theme-index.

```
???
Could please someone explain this to me?
-Kevin

---

