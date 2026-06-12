---
title: "Global Menu not global"
date: 2008-05-01
forum: General Help
---

### Post by AZX3RIC on 2008-05-01
I went through the steps to download, install, and run the global menu. When I was finished I ended up with one icon that reads the name of the program that's running (as you can see in the picture). I'm using 8.04 and am posting this hoping to get some help so I can use the Global menu the way it was intended.

---

### Post by fahimdadream on 2008-05-02
Yea same here, I have the same problem. I cant seem to get it work at all.

---

### Post by fahimdadream on 2008-05-03
bump

---

### Post by queno on 2009-01-04
The fix for this is to create a new file named ".gnomerc" in your home-directory (Pay attention to the dot in front of the filename -> it's a hidden file) and paste the following into it:

```

# Uncomment to load the GTK module
export GTK_MODULES=globalmenu-gnome

# Uncomment to tell the GTK module to open a Gtk
# TreeView for all menus in the application you start.
# export GNOMENU_FUN=1

# Uncomment to disable global menu.
# export GNOMENU_DISABLED=1

# Uncomment to print a lot of debugging messages
# export GNOMENU_VERBOSE=1

# Uncomment to save the debugging messages to the given file.
# export GNOMENU_LOG_FILE=/tmp/gnomenu.log

# Uncomment to disable the plugin for specific programs.
# export GTK_MENUBAR_NO_MAC="fast-user-switch-applet"
```

The first, uncommented line enables globalmenu to get + display the menu of an GTK-application. The rest of the lines are optional. See [**this blog-entry**]("http://nancib.wordpress.com/2008/11/26/get-the-globalmenu-without-all-of-the-hassle/") for more detail.

After you've created & saved the file, you have to restart your current Gnome-session. A simple logout+login will do.

---

