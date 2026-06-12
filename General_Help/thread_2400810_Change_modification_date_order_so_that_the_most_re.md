---
title: "Change modification date order so that the most recent is at the bottom"
date: 2018-09-10
forum: General Help
---

### Post by archaeometrist on 2018-09-10
I was just forced to update from 14.04 to 18.04 due to a hard drive crash.  I've run into a frustrating problem.

I prefer to have folders and files sorted by last modification date (simply done) - but I need to change the order so that the most recent is at the BOTTOM, rather than the top (the way I had it set up before the hard drive crashed).

I've not found a way to do that - and it's causing a lot of headaches for me.

Does anyone know how to change this - and if so, please share it!

Thanks!

Bob

(The sort order is important because of the research and stuff I do - it makes things a lot easier.)

---

### Post by ajgreeny on 2018-09-10
I don't use gnome or nautilus but doesn't clicking on the column header for modification date toggle that property?

---

### Post by raleigh3 on 2018-09-10
Clicking on date modified will do what you want in both Caja and Thunar.

---

### Post by archaeometrist on 2018-09-10
I view the contents of folders using icons, not in detail mode.  It makes things easier.  Using detail mode, yes, I can click on the column heading for "Modified" and it will sort by time, with the newest at the bottom or the top - but as soon as I go back to Icon mode, it puts the latest file at the top.

As far as the file manager - I'm using Nautilus (I only use Gnome Flashback desktop).

---

### Post by ajgreeny on 2018-09-10
Does a right click in empty space give you any options for the sorting?

---

### Post by archaeometrist on 2018-09-10
Nope - no options shown as far as sort order.  I think I'm going to have to go into the "nuts and bolts" and do some editing, or something like that.  I'm not sure where to begin however.

---

### Post by Dennis N on 2018-09-10
When using icon view mode in Files, you change the sort order from the options button on the window header - see screenshot. "First Modified" puts oldest file first.

---

### Post by archaeometrist on 2018-09-10
Funny, not on my system.  Oldest file is LAST - when that should be the newest file.

---

### Post by Dennis N on 2018-09-10
The sort options shown in post #7 are not displayed unless you switch to icon view first, then open that options dialog.

Version of Files (a.k.a. Nautilus) in my Ubuntu 18.04:
```
dmn@Roxanne:~$ apt show nautilus
Package: nautilus
Version: 1:3.26.3-0ubuntu4

```

---

### Post by archaeometrist on 2018-09-11
I already knew how to find the options dialog (simple) - but on my system, the newest file is at the top of the list, and the oldest at the bottom (Icon mode).  I need to find out how to reverse the order so that the newest is LAST.

---

### Post by Claus7 on 2018-09-15
Hello,

> **archaeometrist said:**
> Nope - no options shown as far as sort order.  I think I'm going to have to go into the "nuts and bolts" and do some editing, or something like that.  I'm not sure where to begin however.

using ubuntu flashback 18.04 and nautilus (GNOME nautilus 3.26.4) I have exactly the same options as *Dennis N* has. 
I do not think that you have to mess with coding. I would advice you to reset your system, so as these options to appear. Backup your current configuration first:
dconf dump / > dconf_bup

then reset:
dconf reset -f /

then restart

and after that load once again your configuration:
dconf load / < dconf_bup

comments:
1) this might fix your issue
2) another option will be instead of loading your dump backup file, to reset your system manually back to what you had before resetting
3) even if you load your previous state, it might require some extra additional steps so as to bring your system configurations the way they were before resetting

Regards!

---

