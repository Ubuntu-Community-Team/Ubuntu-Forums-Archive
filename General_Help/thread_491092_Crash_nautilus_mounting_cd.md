---
title: "Crash nautilus mounting cd"
date: 2007-07-03
forum: General Help
---

### Post by AllCrash on 2007-07-03
Hi all!
I have this bad problem...when i insert a cd or dvd in ubuntu feisty, nautilus crash...i cant find an answer to this...so i hope in you!
this is the output of xsession-errors when i insert the cd...i think it will be be of aid

```
** ERROR **: file nautilus-directory.c: line 594 (add_to_hash_table): assertion failed: (g_hash_table_lookup (directory->details->file_hash, file->details->relative_uri) == NULL)
aborting...
Initializing gnome-mount extension

(avant-window-navigator:4830): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:4830): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:4830): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:4830): Wnck-WARNING **: Unhandled action type (nil)
the settings directory exists
```
;)

---

### Post by ashwin_cse on 2007-07-03
The error shows the cause is avant menu bar. Try uninstalling avant & see it solves the problem. If it does then you may ask in avant mailing list or forum. Probably one experienced with avant may answer better.

---

### Post by AllCrash on 2007-07-03
i've uninstalled awn but nothing changed!now xsession doesn't give any output....but nautilus always crash:(
what can i do??:(:(:(

---

### Post by AllCrash on 2007-07-03
ps...i've just tested that if i login like root nautilus works perfectly...i think that this is important...
if i delete all configuration files of nautilus???maybe i solve the problem??](*,)

---

### Post by ashwin_cse on 2007-07-04
Have you posted about this at avant mailing list or forum. Whats their answer. If that doesn't help try posting a bug report in ubuntu launchpad. If that doesn't help, try other cd burner application like x-cdroast , (search with google for other similar apps). If you cant find any suitable, then open console & become root. ```
$sudo su - 
``` Then use the command line version of GUI cd burning apps. **mkisofs** is used to create image file of the data you want to burn. **cdrdao** or **cdreacord** to burn the create image to disc. Be root when creating the image & burning the image to disc. Use the man pages of these cmd line apps or search the web to find tutorial on how to use these apps.

---

### Post by AllCrash on 2007-07-04
tnx for the answer...but probably u haven't understand my problem;)
i havent problem burning file etc...and it doesnt depends from AWN...
any type of cd/dvd that i insert on my feisty makes nautilus crash & reboot.
for a few seconds all desktop icons disappears, all windows are closed and after all home directory is open!:(

---

