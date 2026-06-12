---
title: "GTK/LIBGLADE/LIBGLIB problems. HELP!"
date: 2007-03-18
forum: General Help
---

### Post by Kingfield on 2007-03-18
hey.. if i open a few select applications - ie. right now camorama and alacarte.. i get errors like this :

```
(file-roller:5207): libglade-WARNING **: unknown widget class 'GtkFileChooserButton'

(file-roller:5207): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkFileChooser'

(file-roller:5207): Gtk-CRITICAL **: gtk_file_chooser_set_current_folder: assertion `GTK_IS_FILE_CHOOSER (chooser)' failed
```

i also had this problem for file roller but i fixed it/it fixed itself.

Help please, anything, comments, suggestions, would be greatly appreciated.. i have spend days trying to fix it

Thanks in advance for any help and advice 

Kingfield

---

### Post by Kingfield on 2007-03-18
bumpity bump

---

### Post by hikaricore on 2007-03-18
Do the programs actually crash? If not I wouldn't worry about it.

Alot of gtk software dumps garbage errors to terminal windows.
Most of this is never seen unless you actually run them from a terminal.  :)

---

### Post by Kingfield on 2007-03-18
yes, it crashes on startup.

---

### Post by Kingfield on 2007-03-19
Er.. well any help please?

---

### Post by Kingfield on 2007-03-20
err... bump? please hepl guys this is important

---

### Post by Kingfield on 2007-03-20
BUMPPP~~

I'm begging youguys... can anyone help?

---

### Post by hikaricore on 2007-03-20
Sorry i've never known the apps to crash with that kinda output, the only thing i can think is there may be a corrupt file or two in your installation causing this.  I can't even begin to imagine what to tell you to install, you might get more assistance from anyone who happens to read your thread if you mention which version of Ubuntu you are running.

---

### Post by Kingfield on 2007-03-21
I';m using Dapper.

---

### Post by Kingfield on 2007-03-22
Help please guys... if this error is unsolvable then at least state it...

---

### Post by Kingfield on 2007-03-23
bump yet again.

---

### Post by Adramelech on 2007-03-23
(file-roller:5207): libglade-WARNING **: unknown widget class 'GtkFileChooserButton'

(file-roller:5207): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkFileChooser'

(file-roller:5207): Gtk-CRITICAL **: gtk_file_chooser_set_current_folder: assertion `GTK_IS_FILE_CHOOSER (chooser)' failed

I guess you have an old version of libglade. try updating.

Support for GtkFileChooserButton was added on [libglade-2.5.0: 29-November-2004]("http://ftp.gnome.org/pub/GNOME/platform/2.9/2.9.2/NEWS").

---

### Post by Kingfield on 2007-03-23
but i have libglade 2.6..

---

