---
title: "Constant error with 'gedit' in 14.04"
date: 2014-07-30
forum: General Help
---

### Post by WB0HYQ on 2014-07-30
Every time I launch Gedit (from a terminal) and giving it no input file I get this error:

(gedit:30299): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/bill/.local/share/recently-used.xbel', but the parser failed: Failed to open file '/home/bill/.local/share/recently-used.xbel': Permission denied.

If I give the gedit command WITH an input file name, I get these errors:

(gedit:30137): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:30137): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

Can some kind soul help clear this up for me?

Bill

---

### Post by papibe on 2014-07-30
Hi WB0HYQ.

Could you run these commands and post back the results?
```
ls -ld ~/.local/ ~/.local/share/ ~/.local/share/recently-used.xbel 

find -not -user youruser
```
replace 'youruser' with your actual username.

Regards.

---

### Post by WB0HYQ on 2014-07-30
Sure.

First command =

bill@bill-UBU:~/Desktop$ ls -ld ~/.local/ ~/.local/share/ ~/.local/share/recentyl-used.xbel
ls: cannot access /home/bill/.local/share/recentyl-used.xbel: No such file or directory
drwxr-xr-x  3 bill bill 4096 Jun  1  2013 /home/bill/.local/
drwxr-xr-x 27 bill bill 4096 Jul 30 20:42 /home/bill/.local/share/

Second command =

(nothing) prompt came back without printing anything at all


EDIT:  Sorry, messed up command string.  Results of first command are:

drwxr-xr-x  3 bill bill 4096 Jun  1  2013 /home/bill/.local/
drwxr-xr-x 27 bill bill 4096 Jul 30 20:55 /home/bill/.local/share/
-rw-------  1 bill bill 5018 Jul 30 20:55 /home/bill/.local/share/recently-used.

Bill

---

### Post by papibe on 2014-07-30
Thanks.

Try this:
```
touch ~/.local/share/recently-used.xbel
```
Hope it helps. Let us know how it goes.
Regards.

Note: you ran this, right?
```
find -not -user [COLOR="#FF0000"]**bill**[/COLOR]
```

---

### Post by WB0HYQ on 2014-07-30
The touch command was run and the three lines of output from the 'ls' command remained the same as above.

Yes, I did run the command as you stated.  Still no output at all.


EDIT:  Ah.  That command has to be run when I am in my HOME directory.  The output is:

bill@bill-UBU:~$ find -not -user bill
./.cache/dconf/user
./.rpmdb
./.rpmdb/Name
./.rpmdb/Sigmd5
./.rpmdb/Packages
./.rpmdb/__db.001
./.rpmdb/.dbenv.lock
./.rpmdb/__db.003
./.rpmdb/Triggername
./.rpmdb/Obsoletename
./.rpmdb/Dirnames
./.rpmdb/Group
./.rpmdb/Requirename
./.rpmdb/Installtid
./.rpmdb/__db.002
./.rpmdb/Sha1header
./.rpmdb/Basenames
./.rpmdb/Conflictname
./.rpmdb/Providename

Bill

---

### Post by papibe on 2014-07-30
Ohh, sorry, yes. The proper command should've been:
```
find [COLOR="#FF0000"]**~/**[/COLOR] -not -user youruser
```

Are you running this with sudo? If that's the case I don't recommended. Install gksu instead, and use gksudo:
```
sudo apt-get install gksu

gksudo gedit
```
That's that help?
Regards.

---

### Post by WB0HYQ on 2014-07-30
If I run the command: gedit

I get a text editor window (with no error now, for some strange reason)

If I run the command: sudo gedit

I get the following:

bill@bill-UBU:~$ sudo gedit
[sudo] password for bill: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory


and a text editor window.

If I run the last command and give it a filename to edit, I get the text editor and no error.

Very strange results.  Apparently, the original error(s) have gone away with my experimentation and I can now start up a gedit window just fine using either 'sudo gedit' or plain 'gedit'.  Well, 14.04 is still pretty new so I guess there are bound to be strange happenings until they get straightened out.  For instance, I am still getting "Malformed file, Pressenter to continue" on bootup.  But that's another problem that others have seen.

Thank you for your help.  I'm going to mark this as "Solved".

EDIT:  I am wrong.  Now when I run this command, I get:

bill@bill-UBU:~$ sudo gedit x.txt

(gedit:9594): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

and a editor window for 'x.txt'.

I have a feeling something in the exec is definitely out of kilter.

Bill

---

### Post by vasa1 on 2014-07-30
Why are you using sudo gedit instead of gksudo gedit as advised by papibe?

---

### Post by WB0HYQ on 2014-07-30
Because 'gksudo' ALWAYS asks me for my Password and that's a pain to keep repeating every time I want to issue a command.  'sudo' doesn't always ask me for it.

Bill

---

