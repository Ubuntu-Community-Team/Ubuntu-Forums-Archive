---
title: "URGENT HELP PLEASE *File roller*"
date: 2007-02-22
forum: General Help
---

### Post by Kingfield on 2007-02-22
Hey guys, I'm getting this really strange error - i dunno why, File-roller doesn't have the extract to [location] option... (see attatched file). In terminal, the error i get is:

```
(file-roller:5207): libglade-WARNING **: unknown widget class 'GtkFileChooserButton'

(file-roller:5207): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkFileChooser'

(file-roller:5207): Gtk-CRITICAL **: gtk_file_chooser_set_current_folder: assertion `GTK_IS_FILE_CHOOSER (chooser)' failed

```

Yes, i have tried reinstalling, and rebooting - didn't work. Any suggestions?

Thnx in advance.

EDIT: i think it may be a glade problem... it also gives errors with alacarte....

---

### Post by Kingfield on 2007-02-22
Bump ~ please help

---

### Post by Kingfield on 2007-02-22
Last bump for the night

---

### Post by ^rooker on 2007-02-22
Looks like your gtk version is incompatible with your version of file roller (it's trying to instantiate a class unknown to your libglade) 

- did you change anything in that corner? 
(e.g. install kubuntu desktop on ubuntu sometimes confuses gtk apps)

---

### Post by Kingfield on 2007-02-22
i dunno... dont think so... but then i have now tried reinstalling gtk+, but im getting an error, that i need to remove my old glib versio... realy troublesome. but i DID install a new version of libglade.

---

### Post by Kingfield on 2007-02-22
im installing new vsn of gtk+ now

---

### Post by Kingfield on 2007-02-23
anyone can help?

---

### Post by Kingfield on 2007-02-23
please i really need help

---

### Post by Kingfield on 2007-02-23
W00T! its working again.. i think i solved it by reinstalling libglade 2.6... but my alacarte is still messed up.... with libglade errors..

---

### Post by Kingfield on 2007-03-17
Can ayneone help? alacarte is screwed up, as well as camorama... it says something about something failing GTK_IS_FILE_CHOOSER. Help please?

---

### Post by Kingfield on 2007-05-14
Sorry but i have to bump back up this thread... i have no idea what to do.... and its realy bugging me cuz of alacarte...

---

### Post by Kingfield on 2007-05-19
could someone at least please give me an alternative to alacarte?

---

