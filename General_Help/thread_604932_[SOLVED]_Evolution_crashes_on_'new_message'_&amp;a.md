---
title: "[SOLVED] Evolution crashes on 'new message' &amp;amp; 'add signature'"
date: 2007-11-06
forum: General Help
---

### Post by elliotjreed on 2007-11-06
[SIZE="2"]Whenever I try to click on 'New Message' in Evolution the program shuts immediatly. I ran in from the terminal and got the following:[/SIZE]

```
elliot@MyPC:~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...
(evolution:31161): e-data-server-DEBUG: Loading categories from "/home/elliot/.evolution/categories.xml"
(evolution:31161): e-data-server-DEBUG: Loaded 29 categories

(evolution:31161): XML-CRITICAL **: Document is empty


(evolution:31161): XML-CRITICAL **: Start tag expected, '<' not found


(evolution:31161): GLib-CRITICAL **: g_string_free: assertion `string != NULL' failed

(evolution:31161): libglade-WARNING **: did not finish in PARSER_FINISH state

** ERROR **: Could not load glade file.
aborting...
Aborted (core dumped)
```

It also crashes when I try to 'Add Signature'. The terminal churns out the following:

```
elliot@MyPC:~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...

** (evolution:31271): CRITICAL **: factory: assertion `upgrade == 2' failed

(evolution:31271): evolution-shell-WARNING **: Cannot activate OAFIID:GNOME_Evolution_RSS:2.12 -- Factory `OAFIID:GNOME_Evolution_RSS_Factory:2.12' returned NIL for `OAFIID:GNOME_Evolution_RSS:2.12'

(evolution:31271): XML-CRITICAL **: Document is empty


(evolution:31271): XML-CRITICAL **: Start tag expected, '<' not found


(evolution:31271): GLib-CRITICAL **: g_string_free: assertion `string != NULL' failed

(evolution:31271): libglade-WARNING **: did not finish in PARSER_FINISH state

** ERROR **: Could not load glade file.
aborting...
Aborted (core dumped)
```

PLEASE help me! I just didn't like Thunderbird in Gnome (which is what I used to use in Windows!), and Evolution seems the best integrated into Gnome!

Won't you please, please help me! (Yay for the Beatles...)

---

### Post by dcstar on 2007-11-06
> **elliotjreed said:**
> [SIZE="2"]Whenever I try to click on 'New Message' in Evolution the program shuts immediatly. I ran in from the terminal and got the following:[/SIZE]
.......
Won't you please, please help me! (Yay for the Beatles...)

Rename the (hidden) .evolution directory, and then restart Evolution (this should create a fresh profile).

If things now work (there was some corruption), you can copy your old e-mails from the old directory into the same place in the new one.

---

