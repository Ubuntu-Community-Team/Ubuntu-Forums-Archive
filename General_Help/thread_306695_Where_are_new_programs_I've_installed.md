---
title: "Where are new programs I've installed"
date: 2006-11-25
forum: General Help
---

### Post by redo109 on 2006-11-25
Hi I've used Synaptic package manager to install several programs but cannot find where they are or how to launch the new programs.
Help please.
Cheers
Richard

---

### Post by taurus on 2006-11-25
What programs?  If you know them by names, you can run them from a terminal, Applications -> Accessories -> Terminal.

```
<program name>
```

---

### Post by Marsolin on 2006-11-25
Unfortunately, not all programs have menu entries. Sometimes one has a menu entry, but the menu doesn't update right away. I'm not sure why that is.

If a menu entry doesn't appear, find the package in Synaptic and select the Installed Files tab from Properties. Any file in the /bin or /usr/bin directories are executable and can be started from the terminal.

---

### Post by fragos on 2006-11-25
You can use the menu editor to add these lost programs to the application menus.  I find the Deskbar applet very handy if your not positive of the name.  It will make best guesses as you enter each character.  Entering the word edit will show you all editors even if they don't have edit in the file names.

---

