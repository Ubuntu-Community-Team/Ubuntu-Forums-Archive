---
title: "Problem with CDemu 1.1.0"
date: 2008-07-04
forum: General Help
---

### Post by Philonimbus on 2008-07-04
Hi,

There seem to be a problem with the Ubuntu packages of CDemu 1.1.0.

The install process works correctly, but I can't get the daemon to run properly.

The command
$ sudo /etc/ini.d/cdemu-daemon start
doesn't start the deamon at all, making it impossible to run at start up, it does all the testing part though.

The only way to get the deamon running is by running
$ sudo cdemud -d
wich I can't figure how to run automatically at startup without being asked a password.

I also have problems loading some .CUE files, and get this error :
"org.freedesktop.DBus.GLib.UnmappedError.MirageErrorQuark.Code233492510: Data file cannot be opened or read."

---

