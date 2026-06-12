---
title: "[SOLVED] Certain system adminstration apps won't start"
date: 2007-07-07
forum: General Help
---

### Post by Tom Voros on 2007-07-07
Some of my system administration apps simply don't start.  For example, the "Network" app.  When I try to start it (from the Ubuntu menu, System > Administration > Network) it asks me for my password, which I enter, then I see a "Starting Network" app in the window list.  A few seconds later the "Starting Network" app disappears.

Some other apps that have the same problem are "Shared Folders" and "Users and Groups".

I'm using Ubuntu Feisty and I have all the latest updates.

Any help would be appreciated!

---

### Post by darkdigger on 2007-07-07
Do you get any error messages when you try to start them from the command line? To try it, open up a terminal window and start the network administration tool by typing:

```

gksudo network-admin

```

-Arash

---

### Post by Tom Voros on 2007-07-07
I tried what you suggested but it didn't work.  However, I think I got some useful error messages.  Here is the output:

```

(network-admin:15395): XML-CRITICAL **: Document is empty


(network-admin:15395): XML-CRITICAL **: Start tag expected, '<' not found


(network-admin:15395): GLib-CRITICAL **: g_string_free: assertion `string != NULL' failed

(network-admin:15395): libglade-WARNING **: did not finish in PARSER_FINISH state

** ERROR **: Could not load /usr/share/gnome-system-tools/interfaces/common.glade

aborting...

```

---

### Post by Tom Voros on 2007-07-07
It seems that a bunch of the files in /usr/share/gnome-system-tools/interfaces were empty.  I was able to fix the problem by reinstalling gnome-system-tools with Synaptic.

Thanks for the help, darkdigger!

---

### Post by darkdigger on 2007-07-08
Sweet! Glad you figured it out. :)

-Arash

---

