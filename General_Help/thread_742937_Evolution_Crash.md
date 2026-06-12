---
title: "Evolution Crash"
date: 2008-04-02
forum: General Help
---

### Post by Penguin Power on 2008-04-02
Evolution Mail immediately crashes when I open certain emails...

sean@sean-desktop:~$ evolution
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
** (evolution:7717): DEBUG: mailto URL command: evolution %s
** (evolution:7717): DEBUG: mailto URL program: evolution
Segmentation fault (core dumped)

Any ideas?

---

### Post by erginemr on 2008-04-02
I have fired up Evolution from the terminal, and it came up with the same set of startup text messages except the crash (i.e. segmentation fault).
```
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
** (evolution:7958): DEBUG: mailto URL command: evolution %s
** (evolution:7958): DEBUG: mailto URL program: evolution
```
So unfortunately, this text doesn't contain any valuable hints to the reason of the crash...

---

### Post by erginemr on 2008-04-02
To narrow down the possibilities, you may try to start evolution with:
```
evolution --disable-eplugin
```
which will temporarily disable all plugins, and check whether it crashes while viewing those specific mails.

Alternatively:
```
evolution 1>output.txt 2>error.txt
```
will produce two files in your home directory, one for standard output and one for error messages.

---

### Post by Penguin Power on 2008-04-02
I tried running both of those commands, and Evolution still segfaults.

The two output files don't appear to provide any new information. I ran exactly the command you suggested:

[quote=output.txt]CalDAV Eplugin starting up ...
** (evolution:15929): DEBUG: mailto URL command: evolution %s
** (evolution:15929): DEBUG: mailto URL program: evolution[/quote]

[quote=error.txt]evolution-shell-Message: Killing old version of evolution-data-server...[/quote]

---

### Post by phillipchandler on 2008-04-02
Ive started getting evolution crashes. Im running 7.04 32 bit on a Dell Inspiron. After running evolution from a terminal I get the following, any help would be appreciated :

CalDAV Eplugin starting up ...

(evolution-2.10:6610): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:6610): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:6610): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:6610): DEBUG: mailto URL program: evolution
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
(evolution-2.10:6610): e-data-server-DEBUG: Loading categories from "/home/pchandler/.evolution/categories.xml"
(evolution-2.10:6610): e-data-server-DEBUG: Loaded 29 categories
index:0
process 6610: The last reference on a connection was dropped without closing the connection. This is a bug in an application. See dbus_connection_unref() documentation for details.
Most likely, the application was supposed to call dbus_connection_close(), since this is a private connection.

---

