---
title: "Restore from Backup  failed due to unknown error using Deja-dup"
date: 2021-12-07
forum: General Help
---

### Post by Robbyx on 2021-12-07
File to be recovered 155kb

**Relevant free space:**
/tmp space available: 36.7GiB free  (total 52GiB)
Backup location: 291GiB free

**Steps to the problem:**
Via Nautilus find file to be recovered. 
Start restore of file choosing the day from the drop down choice of dates.  Restoring starts.
All ok until authentication is needed to run /USR/libexec/deja-dup/duplicity as super user.
I have failed to restore on 3 dates for the file. 


Error message immediately after authentication:

**Restore failed Unknown error: **

[I]Can I please have suggestions as to how to restore the file.
It might help if I could post a trace, but how do I turn on Trace in Backup?
[/I]

---

### Post by TheFu on 2021-12-08
/USR/libexec/deja-dup/duplicity  Looks like an incorrect name.

---

### Post by Robbyx on 2021-12-08
Following your comment, I have just reinstalled Deja-dup. I still have the same fault. It is quite important for me to be able to recover the file. Any other ideas as to how to proceed?

---

### Post by deadflowr on 2021-12-08
Are you sure it wants your superuser and not the deja-dup encryption set password?
Are these system files or your user's files?

---

### Post by Robbyx on 2021-12-08
I copied the backup to another drive, but I still get Restore failed with unknown error. 

(I used the correct authentication password.)

Any other solutions?

---

### Post by Robbyx on 2021-12-08
I have found this link which I have not been able to follow successfully
[https://bbs.archlinux.org/viewtopic.php?id=159329](https://bbs.archlinux.org/viewtopic.php?id=159329)

Here is an example:

$ LANG=C DEJA_DUP_DEBUG=1 deja-dup --restore
Unable to init server: Could not connect: Connection refused

(org.gnome.DejaDup:83356): Gtk-WARNING **: 20:10:42.611: cannot open display: DISPLAY XAUTHORITY=$XAUTHORITY DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS

Am I right to assume I can restore the backed up files using duplicity?

I note man duplicity is referred to in the article

---

### Post by Robbyx on 2021-12-08
I have found this link which I have not been able to follow successfully
[https://bbs.archlinux.org/viewtopic.php?id=159329](https://bbs.archlinux.org/viewtopic.php?id=159329)

Here is an example:

$ LANG=C DEJA_DUP_DEBUG=1 deja-dup --restore
Unable to init server: Could not connect: Connection refused

(org.gnome.DejaDup:83356): Gtk-WARNING **: 20:10:42.611: cannot open display: DISPLAY XAUTHORITY=$XAUTHORITY DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS

Am I right to assume I can restore the backed up files using duplicity?

I note "man duplicity" is referred to in the article and the files are duplicity files so I am assuming that I can use the advice at 

[https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase](https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase)

In view of the difficulty with the above solution, I propose to l proceed with the following two steps:

mkdir -p /tmp/restore
~$ duplicity --gio file:///media/backup /tmp/restore

I attach a screen shot of the backup files. 

Does anyone know how to rename the "file:///media/backup" in the sample so as to extract the backup file for Monday?

---

### Post by TheFu on 2021-12-08
```
Unable to init server: Could not connect: Connection refused
```
That probably means that the deja-dup "server" port cannot be connected.  Is it running? Is there a firewall in the way?

```
(org.gnome.DejaDup:83356): Gtk-WARNING **: 20:10:42.611: cannot open display: DISPLAY XAUTHORITY=$XAUTHORITY DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS
```
That's an X/Windows error plus a Gnome error.

Appears from here that some GUI problem, before DejaDup, is the issue.  Is X/Windows running?  Is the gnome DBus working?

I don't like GUI backup tools. They are too complicated.  Have you ever been able to restore files before?

---

### Post by Robbyx on 2021-12-08
Thank you for your reply. 

I have been able to restore files before.

Is X/Windows part of MS Windows? I am only using Ubuntu 20.04

How do I check if the Gnome D/Bus is running and if missing put it back?

---

### Post by Robbyx on 2021-12-08
The other part of my post dealt with restoring without the GUI.

How do I  change the example "file:///media/backup"  so as to recreate  the file for Monday in the attachment. I ask because I do not understand which of the files shown in the attached screenshot, should be linked together for recovery. Is it purely based on the date in the name of the backup files?

---

### Post by TheFu on 2021-12-08
> **Robbyx said:**
> Thank you for your reply. 
Always welcome. Sorry I don't know the answer. I've never used DejaDup.

> **Robbyx said:**
> I have been able to restore files before. 
That's important.

> **Robbyx said:**
> Is X/Windows part of MS Windows? I am only using Ubuntu 20.04 
No!  X/Windows is the Unix Windowing system. It Predates MS-Windows and you've probably been using it until 20.04 on any Unix/Linux OS with a GUI.  In 20.04, Canonical tried Wayland (again), with a fallback to X/Windows.  This is very important general Linux knowledge.  In the packages installed, we see "xorg" ... which means X/Windows stuff.

> **Robbyx said:**
> How do I check if the Gnome D/Bus is running and if missing put it back?
You look for a process with dbus in the name?   There should be at least 4 processes in the process table. Some running as your userid, some as the display manager (the login screen) and some as a messenger passing data between the GUI and the system, I'd guess (but I don't really know).  

I bet architecture diagrams for dbus and X/Windows are on wikipedia.  I know X/Windows has one.  Yep.
[https://en.wikipedia.org/wiki/D-Bus](https://en.wikipedia.org/wiki/D-Bus)   Looks like I was blaming Gnome, when I should have been blaming some other team for dbus.
> The freedesktop.org project also developed a free and open-source software library called libdbus, as a reference implementation of the specification. This library should not be confused with D-Bus itself, as other implementations of the D-Bus specification also exist, such as GDBus (GNOME),[9] QtDBus (Qt/KDE),[10] dbus-java[11] and sd-bus (part of systemd).[12]

And X/Windows ... [https://en.wikipedia.org/wiki/X_Window_System](https://en.wikipedia.org/wiki/X_Window_System)

Does duplicity have a command option to validate a backup set against corruption?  I'd run that.  [https://unix.stackexchange.com/questions/424553/how-to-verify-a-deja-dup-backup-using-duplicity](https://unix.stackexchange.com/questions/424553/how-to-verify-a-deja-dup-backup-using-duplicity) seems the answer. Yes, there is a command.  Give that a shot.  If the backup set is corrupt, probably isn't much that can be done, but reading up on duplicity would be where I started.

---

