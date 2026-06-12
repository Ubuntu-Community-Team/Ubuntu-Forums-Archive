---
title: "corrupted totem-gstreamer package"
date: 2007-02-26
forum: General Help
---

### Post by icetortoise on 2007-02-26
On my 6.10 ubuntu, every time I install/remove softwares, I get an error message with totem-gstreamer package. I can't remove or re-install the package either. What should I do to get rid of the problem?

Below is what I have when trying to remove the package:

--------
sudo apt-get remove totem-gstreamer
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
imlib11 kdebase-data bittornado libxcomposite1 tcltls docker totem-gstreamer
sox tcl8.4 imlib-base libsvnqt2 tk8.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
totem-gstreamer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 6136kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 130736 files and directories currently installed.)
Removing totem-gstreamer ...

(update-desktop-database:5637): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing totem-gstreamer (--remove):
subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
totem-gstreamer
E: Sub-process /usr/bin/dpkg returned an error code (1)

-------

---

### Post by an.echte.trilingue on 2007-02-26
What happens with 
```
sudo dpkg --force-remove totem-gestreamer
```
?

Take care
-mat

---

### Post by icetortoise on 2007-02-26
the command gives this:
dpkg: unknown force/refuse option `remove'

then I tried sudo dpkg --force-remove-essential totem-gestreamer
and get this:
dpkg: need an action option

---

### Post by an.echte.trilingue on 2007-02-26
Sorry I made a really bad typo.

sudo dpkg -r --force-remove-reinstreq totem-gstreamer

---

### Post by icetortoise on 2007-02-26
sudo dpkg -r --force-remove-reinstreq totem-gstreamer
(Reading database ... 131384 files and directories currently installed.)
Removing totem-gstreamer ...

(update-desktop-database:10435): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing totem-gstreamer (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 totem-gstreamer

---

### Post by an.echte.trilingue on 2007-02-26
Wow.  OK, what happens with sudo apt-get -f remove totem-gstreamer?

---

### Post by icetortoise on 2007-02-26
Still the same one...

---
sudo apt-get -f remove totem-gstreamer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  totem-gstreamer
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  totem-gstreamer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 6136kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131384 files and directories currently installed.)
Removing totem-gstreamer ...

(update-desktop-database:13894): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing totem-gstreamer (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 totem-gstreamer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by icetortoise on 2007-02-26
Still the same one...

---
sudo apt-get -f remove totem-gstreamer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  totem-gstreamer
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  totem-gstreamer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 6136kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131384 files and directories currently installed.)
Removing totem-gstreamer ...

(update-desktop-database:13894): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing totem-gstreamer (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 totem-gstreamer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by an.echte.trilingue on 2007-02-27
OK.  You'll have to remove it manually.  Make backups in case this does not work.

First, list all the installed files for totem-gstreamer:

```
dpkg-query -L totem-gstreamer
```

then remove each and every one of those files.

Then open this file in a text editor:

```
/var/lib/dpkg/status
```

and find the section for totem-gstreamer, and delete it.

then 
```

sudo aptitude update
sudo aptitude upgrade
```

---

### Post by icetortoise on 2007-02-27
Thanks, that got rid of it.

---

### Post by an.echte.trilingue on 2007-02-28
Glad to be of help.

Take care
-mat

---

### Post by wyndblade on 2007-04-13
an.echte.trilingue,

     Thank you for this nice easy way to quickly fix dpkg, I had a problem removing a 3rd party package for fbsplash out of my system and this worked.  :guitar:

---

