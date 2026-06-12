---
title: "Need default cupsd.conf file"
date: 2006-07-28
forum: General Help
---

### Post by Athanasius on 2006-07-28
I am trying to network my printers and like a complete idiot I didn't backup the default cupsd.conf file.  Could someone please post it for me?

---

### Post by bLaDeY on 2006-07-29
I don't have access to CUPS at the moment but 'apt-get remove cupsd' then 'apt-get install cupsd' should do the trick.

I am certain there is a 'reinstall' option but I can't recall it, something like --reinstall perhaps.

---

### Post by philippe_carlo on 2006-07-29
```
sudo aptitude reinstall cupsd
```
Reinstallation may keep exist config files, so make sure to move cupsd.conf out of the way.

---

### Post by Mitch on 2006-08-26
I had the same problem as Athanasius and followed the advice to reinstall cupsd.  I followed the above posts and got some errors, and then I went into synaptic and marked the cupsys package for reinstallation.  I got an error that said:

E: cupsys: subprocess post-installation script returned error exit status 3


When I go to system -> Administration -> printing I get:
The CUPS server could not be contacted.

When I type "cupsd" at the terminal I get:
Child exited on signal 15!


Is there anyway I can get my printing working again without a reinstall?


Also, if I do get back to where I was, I was trying to setup my Ubuntu Desktop to let me print on its printer with my xp laptop. If anyone can lead me in the right direction on that front I'd appreciate it.

PS the good news is that I think I have the default cupsd.conf file back :D

---

### Post by Mitch on 2006-08-27
I got things straight again by using "completely remove" CUPS in synaptic.  This option originally looked scary because it removed "ubuntu-desktop" as well.  I installed cups, and then looked for ubuntu-desktop and installed it.  Things seem back to normal.

---

### Post by Owdy on 2006-09-11
> **Mitch said:**
> I got things straight again by using "completely remove" CUPS in synaptic.  This option originally looked scary because it removed "ubuntu-desktop" as well.  I installed cups, and then looked for ubuntu-desktop and installed it.  Things seem back to normal.

I did same but didnt work. I still get that 
' The CUPS server could not be contacted.' error :(

---

### Post by Owdy on 2006-09-12
I really need help to fix this. I cant print anything :(

.xsessionerrors

```
** (gnome-cups-icon:6778): WARNING **: IPP request failed with status 1280
Initializing nautilus-open-terminal extension

(gnome-panel:6765): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 30

(gnome-panel:6765): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 
** (gnome-cups-icon:6778): WARNING **: Tulostimen tarjotin-ikonia ei voitu käynnistää, koska CUPS-palvelimeen ei saatu yhteyttä.
Ikkunointiohjelman varoitus: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(evince:6893): Gtk-CRITICAL **: gtk_tree_model_foreach: assertion `GTK_IS_TREE_MODEL (model)' failed

(evince:6893): Gtk-CRITICAL **: gtk_list_store_clear: assertion `GTK_IS_LIST_STORE (list_store)' failed
Ikkunointiohjelman varoitus: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

/var/lod/cups/error_log

```
I [12/Sep/2006:20:32:35 +0300] Listening to 127.0.0.1:631 (IPv4)
I [12/Sep/2006:20:32:35 +0300] Listening to /var/run/cups/cups.sock (Domain)
I [12/Sep/2006:20:32:35 +0300] Listening to :::631 (IPv6)
I [12/Sep/2006:20:32:35 +0300] Listening to 0.0.0.0:631 (IPv4)
I [12/Sep/2006:20:32:35 +0300] Listening to /var/run/cups/cups.sock (Domain)
I [12/Sep/2006:20:32:35 +0300] Loaded configuration file "/etc/cups/cupsd.conf"
I [12/Sep/2006:20:32:35 +0300] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [12/Sep/2006:20:32:35 +0300] Configured for up to 100 clients.
I [12/Sep/2006:20:32:35 +0300] Allowing up to 100 client connections per host.
I [12/Sep/2006:20:32:35 +0300] Using policy "default" as the default!
I [12/Sep/2006:20:32:35 +0300] Full reload is required.
I [12/Sep/2006:20:32:35 +0300] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
I [12/Sep/2006:20:32:35 +0300] Loading job cache file "/var/cache/cups/job.cache"...
I [12/Sep/2006:20:32:35 +0300] Full reload complete.
E [12/Sep/2006:20:32:35 +0300] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
I [12/Sep/2006:20:32:35 +0300] Listening to /var/run/cups/cups.sock on fd 0...
E [12/Sep/2006:20:32:35 +0300] Unable to bind socket for address :::631 - Address already in use.
E [12/Sep/2006:20:32:35 +0300] Unable to bind socket for address 0.0.0.0:631 - Address already in use.
I [12/Sep/2006:20:32:35 +0300] Listening to /var/run/cups/cups.sock on fd 1...
```

---

