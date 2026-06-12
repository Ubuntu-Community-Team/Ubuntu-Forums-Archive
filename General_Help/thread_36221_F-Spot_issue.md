---
title: "F-Spot issue"
date: 2005-05-22
forum: General Help
---

### Post by Romu on 2005-05-22
I've installed f-spot 0.0.12 through the universe.

Everything worked fine except, when I tried to really work with.

As I'm French, I began to delete the existing categories to create my own ones, and this is the point where problem raised.

I keeped only the "favorites" category and when I added a new one, it never appeared  in the list.

Now f-spot doesn't start, I briefly see the main window (less than 1 s) and when I try to run it in the command line I get the following output :

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in [0x000b7] (at /build/buildd/f-spot-0.0.12/src/PhotoStore.cs:1099) PhotoStore:Query (Tag[],PhotoStore/DateRange)
in [0x0001d] (at /build/buildd/f-spot-0.0.12/src/PhotoQuery.cs:17) FSpot.PhotoQuery:.ctor (PhotoStore)
in [0x0023e] (at /build/buildd/f-spot-0.0.12/src/MainWindow.cs:169) MainWindow:.ctor (Db)
in [0x0006f] (at /build/buildd/f-spot-0.0.12/src/main.cs:28) Driver:Main (string[])


I've tried to remove /re-install f-spot without any success, I think some stuff remain on the disk but I don't know where.

Any help will be greatly appreciated.

---

### Post by tread on 2005-05-22
If you modified any fspot settings, those modifications should reside in your home directory. Look for some .fspot or similar file/folder in your directory and delete it .. the default fspot should start again after that.

---

### Post by Romu on 2005-05-22
Whow, thank you, indeed there is a hidden folder into the .gnome2 folder.
And now it works.

Thanks a lot.

---

