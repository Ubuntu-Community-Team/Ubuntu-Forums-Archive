---
title: "installing deb or bin files get error: no such file or directory!!"
date: 2007-01-27
forum: General Help
---

### Post by presbp on 2007-01-27
I do the sudo ./<name>.bin in the terminal it returned no such file or directory.  I also tried sudo chmod 755 <name>.bin and same error.  When I was trying to install deb I do sudo dpkg -i <name>.deb I also got the same error.  I know I have downloaded those files.. they are on my desktop

---

### Post by JamieC on 2007-01-27
Do the files have spaces in their names? Are you in the correct directory?

What is the output of the following:
```

ls - all

```

---

### Post by presbp on 2007-01-27
total 184
drwxr-xr-x 27 presbp presbp  4096 2007-01-27 17:35 .
drwxr-xr-x  3 root   root    4096 2007-01-27 07:20 ..
drwxr-xr-x  2 presbp root    4096 2007-01-27 16:50 .automatix
-rw-------  1 presbp presbp  2665 2007-01-27 17:35 .bash_history
-rw-r--r--  1 presbp presbp   220 2007-01-27 07:20 .bash_logout
-rw-r--r--  1 presbp presbp   414 2007-01-27 07:20 .bash_profile
-rw-r--r--  1 presbp presbp  2227 2007-01-27 07:20 .bashrc
drwxr-xr-x  2 presbp presbp  4096 2007-01-27 17:19 .beryl
-rw-r--r--  1 presbp presbp   185 2007-01-27 14:14 .beryl-managerrc
drwx------  4 presbp presbp  4096 2007-01-27 14:27 .config
drwxr-xr-x  2 presbp presbp  4096 2007-01-27 17:23 Desktop
-rw-------  1 presbp presbp    26 2007-01-27 07:33 .dmrc
drwxr-xr-x  2 presbp presbp  4096 2007-01-27 15:21 Documents
drwxr-xr-x  4 presbp presbp  4096 2007-01-27 14:20 .emerald
-rw-------  1 presbp presbp    16 2007-01-27 07:33 .esd_auth
drwxr-xr-x  8 presbp presbp  4096 2007-01-27 15:09 .evolution
lrwxrwxrwx  1 presbp presbp    26 2007-01-27 07:20 Examples -> /usr/share/example-content
-rw-r--r--  1 presbp presbp     0 2007-01-27 12:55 .fonts.cache-1
drwx------  5 presbp presbp  4096 2007-01-27 17:06 .gconf
drwx------  2 presbp presbp  4096 2007-01-27 17:36 .gconfd
-rw-r-----  1 presbp presbp     0 2007-01-27 16:41 .gksu.lock
drwx------  2 presbp presbp  4096 2007-01-27 17:04 .glipper
drwxr-xr-x  3 presbp presbp  4096 2007-01-27 07:33 .gnome
drwx------  9 presbp presbp  4096 2007-01-27 17:27 .gnome2
drwx------  2 presbp presbp  4096 2007-01-27 07:33 .gnome2_private
drwx------  2 presbp presbp  4096 2007-01-27 16:39 .gnupg
drwxr-xr-x  2 presbp presbp  4096 2007-01-27 16:52 .gstreamer-0.10
-rw-r--r--  1 presbp presbp    88 2007-01-27 07:33 .gtkrc-1.2-gnome2
-rw-------  1 presbp presbp   875 2007-01-27 14:12 .ICEauthority
-rw-r--r--  1 presbp presbp  1730 2007-01-24 22:56 key.gpg.asc
drwx------  3 presbp presbp  4096 2007-01-27 17:27 .local
drwx------  3 presbp presbp  4096 2007-01-27 15:16 .macromedia
drwx------  3 presbp presbp  4096 2007-01-27 07:33 .metacity
drwx------  4 presbp presbp  4096 2007-01-27 13:21 .mozilla
drwxr-xr-x  3 presbp presbp  4096 2007-01-27 12:57 .nautilus
drwx------  3 presbp presbp  4096 2007-01-27 17:35 .openoffice.org2
-rw-------  1 presbp presbp   766 2007-01-27 17:36 .recently-used
-rw-r--r--  1 presbp presbp  6257 2007-01-27 17:35 .recently-used.xbel
-rw-r--r--  1 presbp presbp     0 2007-01-27 12:39 .sudo_as_admin_successful
drwx------  4 presbp presbp  4096 2007-01-27 13:19 .thumbnails
drwx------  2 presbp presbp  4096 2007-01-27 17:08 .Trash
drwxr-xr-x  2 presbp presbp  4096 2007-01-27 12:39 .update-manager
drwx------  2 presbp presbp  4096 2007-01-27 07:33 .update-notifier
-rw-------  1 presbp presbp   125 2007-01-27 14:12 .Xauthority
-rw-r--r--  1 presbp presbp 20180 2007-01-27 17:36 .xsession-errors

---

### Post by dcstar on 2007-01-27
Perhaps you could tell people **exactly** what you are trying to do so they then have a chance to assist you?

---

### Post by JamieC on 2007-01-27
If they are on your desktop, you need to cd to it:
```

cd Desktop

```

Then find out the name of the .bin files:
```

ls | grep .bin

```

Then you can run or install what you wish.

---

### Post by presbp on 2007-01-27
thanks.  Once I got cd'ed into desktop I just had to do chmod 755 googleearthlinux.bin and then ./googleearthlinux.bin.  It installed and everything.  I didn't want to use automatix so I just installed automatix to get the repositories for the stuff automatix does automatically.  Thanks.  I guess I just  wasn't cd'ing right.. I know cd in Windows and I think it is pretty much the same I should've known better.

---

