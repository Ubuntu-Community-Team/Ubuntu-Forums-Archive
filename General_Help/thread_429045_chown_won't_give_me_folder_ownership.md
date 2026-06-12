---
title: "chown won't give me folder ownership"
date: 2007-04-30
forum: General Help
---

### Post by Raos on 2007-04-30
I was trying to change ownership of my .wine directory, because for some reason it's set as root, so I can't write to it, and I was using the chown command just like given in the userguide
```
sudo chown system_username /location_of_files_or_folders
```
 but the ownership would never change.  As a test, I took a different random folder that I had ownership of, and tried changing the ownership to root, which worked, but will also not change back, so it seems to be just giving myself ownership that doesn't work.  It doesn't give any error message saying the username doesn't exist or anything, it acts the exact same as when I successful changed ownership to root, but nothing actually changes.

---

### Post by tbodine on 2007-04-30
Try...
```
sudo chown -R user /dir/ect/ory
```

The -R option will recursively change the ownership.

---

### Post by trak87 on 2007-04-30
Perhaps you have a syntax problem? It's hard to tell from your example, but I use the command more like this:

```
sudo chown owner:group location_of_files_or_folders/
```

This example would only change a directory named "location_of_files_or_folder". If you want to change files within that directory, use this:

```
sudo chown owner:group location_of_files_or_folders/*
```

Note the colon separating the owner from the group. And note the absence of '/' at the beginning of the directory since it would be pretty rare that one would change a directory at the root level.

Also, if you want to change all the file ownership from the specified directory downward (a recursive chown), then do this: 

```
sudo chown -R owner:group location_of_files_or_folders/
```

And one more thing, if your owner and group are the same you can omit the group, but keep the colon like this:

```
sudo chown -R owner: location_of_files_or_folders/
```

---

### Post by dagrump on 2007-04-30
i could be all wet here as i'm think you might need to be root try sudo su, to change root to something other.  sorry ignore this.

---

### Post by Raos on 2007-04-30
Thanks, but nothing is still happening.  Ownership remains as root without changing.

---

### Post by taurus on 2007-04-30
What's the output of this command from a terminal?

```
ls -la ~
```

---

### Post by Raos on 2007-04-30
A bit long, but this:
> total 532
drwxr-xr-x 54 adam adam   4096 2007-04-30 19:26 .
drwxr-xr-x  4 root root   4096 2007-04-27 18:19 ..
-rw-r--r--  1 adam adam    253 2007-04-28 17:53 .audacity
drwxr-xr-x  2 adam root   4096 2007-04-28 12:39 .automatix
-rw-r--r--  1 adam adam 226532 2007-04-28 01:43 automatix2_1.1-3.12-7.04feisty_i386.deb
-rw-------  1 adam adam   1722 2007-04-30 19:45 .bash_history
-rw-r--r--  1 adam adam    220 2007-04-27 18:19 .bash_logout
-rw-r--r--  1 adam adam   2298 2007-04-27 18:19 .bashrc
drwx------  7 adam adam   4096 2007-04-30 14:58 .beagle
drwxr-xr-x  2 adam adam   4096 2007-04-29 18:07 .checkgmail
drwxr-xr-x  5 adam adam   4096 2007-04-11 20:29 Cheer
drwxr-xr-x  3 adam adam   4096 2007-04-29 23:04 Computer Related
drwxr-xr-x  4 adam adam   4096 2007-04-28 01:33 .config
drwxr-xr-x  4 adam adam   4096 2007-04-30 00:08 Desktop
-rw-------  1 adam adam     26 2007-04-28 00:33 .dmrc
drwxr-xr-x  8 adam adam   4096 2007-04-30 00:08 Downloads
drwxr-xr-x 10 adam adam   4096 2007-04-28 13:28 Education
-rw-------  1 adam adam     16 2007-04-28 00:33 .esd_auth
drwxr-xr-x  3 adam adam   4096 2007-04-28 00:35 .evolution
lrwxrwxrwx  1 adam adam     26 2007-04-27 18:19 Examples -> /usr/share/example-content
drwxr-xr-x  2 adam adam   4096 2007-04-28 02:39 .fontconfig
drwx------  3 adam adam   4096 2007-04-28 13:37 .gaim
drwx------  6 adam adam   4096 2007-04-30 14:07 .gconf
drwx------  2 adam adam   4096 2007-04-30 20:02 .gconfd
drwxr-xr-x  7 adam adam   4096 2007-04-28 14:03 .gdesklets
-rw-r-----  1 adam adam      0 2007-04-30 02:04 .gksu.lock
drwxr-xr-x  2 adam adam   4096 2007-04-28 13:10 .glchess
drwxr-xr-x  4 adam adam   4096 2007-04-28 00:50 .gnome
drwx------ 11 adam adam   4096 2007-04-30 03:09 .gnome2
drwx------  2 adam adam   4096 2007-04-28 00:33 .gnome2_private
-rw-r--r--  1 adam adam    956 2007-04-29 14:32 .gnome-hearts.cfg
drwxr-xr-x  2 adam adam   4096 2007-04-28 13:29 .gstreamer-0.10
-rw-r--r--  1 adam adam     86 2007-04-28 00:33 .gtkrc-1.2-gnome2
drwx------  2 adam adam   4096 2007-04-29 06:04 .gxine
-rw-------  1 adam adam    539 2007-04-30 14:07 .ICEauthority
drwxr-xr-x  2 adam adam   4096 2007-04-28 00:50 .icons
drwx------  3 adam adam   4096 2007-04-29 05:52 .kde
drwx------  4 adam adam   4096 2007-04-30 20:08 .liferea_1.2
drwxr-xr-x  3 adam adam   4096 2007-04-28 00:39 .local
drwx------  3 adam adam   4096 2007-04-28 12:50 .macromedia
drwxr-xr-x  3 adam adam   4096 2007-04-29 06:04 .mcop
-rw-------  1 adam adam     31 2007-04-29 18:10 .mcoprc
drwx------  3 adam adam   4096 2007-04-28 00:33 .metacity
drwxr-xr-x  5 adam adam   4096 2007-04-11 20:29 Miscellaneous
drwxr-xr-x  3 adam adam   4096 2007-04-11 21:03 Movies
drwx------  3 adam adam   4096 2007-04-28 12:50 .mozilla
drwx------  3 adam adam   4096 2007-04-28 02:25 .mozilla-thunderbird
drwxr-xr-x  2 adam adam   4096 2007-04-30 14:53 .mplayer
drwxr-xr-x 13 adam adam   4096 2007-04-28 13:26 Music
drwxr-xr-x  3 adam adam   4096 2007-04-30 03:09 .nautilus
-rw-------  1 adam adam    194 2007-04-30 02:03 .notifier.conf
drwx------  3 adam adam   4096 2007-04-28 18:05 .openoffice.org2
drwxr-xr-x 16 adam adam   4096 2007-04-28 13:24 Pictures
-rw-r--r--  1 adam adam    566 2007-04-27 18:19 .profile
drwx------  3 adam adam   4096 2007-04-29 23:42 .qalculate
drwxr-xr-x  2 adam adam   4096 2007-04-29 06:04 .qt
-rw-------  1 adam adam   1044 2007-04-28 18:05 .recently-used
-rw-r--r--  1 adam adam  15827 2007-04-30 19:26 .recently-used.xbel
-rw-r--r--  1 adam adam      0 2007-04-28 00:33 .sudo_as_admin_successful
drwxr-xr-x  2 adam adam   4096 2007-04-28 00:55 .themes
drwx------  4 adam adam   4096 2007-04-28 01:06 .thumbnails
drwxr-xr-x  3 adam adam   4096 2007-04-28 22:03 .tomboy
-rw-r--r--  1 adam adam   1651 2007-04-28 22:03 .tomboy.log
drwx------  5 adam adam   4096 2007-04-29 23:05 .Trash
drwx------  2 adam adam   4096 2007-04-29 18:00 .tsclient
drwxr-xr-x  2 adam adam   4096 2007-04-28 01:00 .update-manager-core
drwx------  2 adam adam   4096 2007-04-28 00:33 .update-notifier
drwxr-xr-x  3 adam adam   4096 2007-04-29 06:05 .vlc
drwx------  2 adam adam   4096 2007-04-30 02:02 .w3m
drwxr-xr-x  2 adam adam   4096 2007-04-30 14:07 .wapi
drwxr-x---  7 adam adam   4096 2007-04-28 14:03 .wesnoth
drwxr-xr-x  4 adam adam   4096 2007-04-28 21:49 .wine
-rw-------  1 adam adam    122 2007-04-30 14:07 .Xauthority
drwxr-xr-x  2 adam adam   4096 2007-04-28 13:27 .xine
-rw-r--r--  1 adam adam   8938 2007-04-30 19:31 .xsession-errors


---

### Post by taurus on 2007-04-30
Well, you are the owner of ~/.wine.

```
**drwxr-xr-x 4 adam adam 4096 2007-04-28 21:49 .wine**
```

```
ls -la ~/.wine
```

---

### Post by Raos on 2007-04-30
Hrm, so I see.  When I check the properties after, it still gave the owner as root, but I tried restarting, and when I started up again, the properties gave me as the owner.

Thanks for help, all!

---

