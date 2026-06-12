---
title: "F-spot can't start"
date: 2005-09-03
forum: General Help
---

### Post by Davidios on 2005-09-03
When I start f-spot in the console this appear:
```
david@linux:~$ f-spot

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00213> PhotoStore:Query (.Tag[] tags, .DateRange range)
in <0x00029> FSpot.PhotoQuery:.ctor (.PhotoStore store)
in <0x005f3> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)
``` 

Then F-spot starts but in a second it closes. :?

---

### Post by Davidios on 2005-09-03
Please, it's very important :(

---

### Post by jeremytaylor on 2005-09-03
I had this problem... the answer is this thread.... [http://ubuntuforums.org/showthread.php?t=48300&highlight=f-spot](http://ubuntuforums.org/showthread.php?t=48300&highlight=f-spot)
hope that helps
jeremy

---

### Post by Davidios on 2005-09-03
Ok, I've got it!

> Hi all,

I just wanted to note a crash I've encountered:
If you rename the 'Hidden' tag in F-Spot to anything else, and quit
the program, when you come back next time the program will crash right
after showing the main window (without any controls inside it) The
error i get is:
--------------------------------
(these first two lines repeat many times before showing the Unhandled Exception)
(f-spot:6105): GLib-CRITICAL **: g_key_file_add_group: assertion
`g_key_file_loo kup_group_node (key_file, group_name) == NULL' failed

Unhandled Exception: System.NullReferenceException: Object reference
not set to an instance of an object
in <0x00213> PhotoStore:Query (.Tag[] tags, .DateRange range)
in <0x00029> FSpot.PhotoQuery:.ctor (.PhotoStore store)
in <0x00630> MainWindow:.ctor (.Db db)
in <0x00330> Driver:Main (System.String[] args)
--------------------------------
And the only way to make the program work again i've found is to
delete ~/.gnome2/f-spot/photos.db
So if you're going to reproduce the bug, backup the file or you'll
loose your entire photo collection. Renaming the rest of the tags
seems to work fine.
I'm using Mono 1.1.8.3 from nrpms on a Fedora 4 system, and I'm using
a F-Spot copy checked-out from the main gnome cvs server as of
yesterday night.
Hope the info is useful

---

