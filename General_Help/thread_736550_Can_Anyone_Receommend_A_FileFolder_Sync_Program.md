---
title: "Can Anyone Receommend A File/Folder Sync Program?"
date: 2008-03-26
forum: General Help
---

### Post by Eddy5 on 2008-03-26
I'm looking for a decent folder/file sync program for Ubuntu. I've tried rsync and unison in the past and they were awkward to use and didn't really do what I want.
I've been using Beyond Compare in Windows and it's exactly what I want. It compares 2 dirs recursively, and shows me which folders/files don't match in a tree list. I can then select files to sync or not sync as required.
[http://www.scootersoftware.com/](http://www.scootersoftware.com/)
Is there anything available like this in Ubuntu?

---

### Post by 67GTA on 2008-03-26
I've never used Beyond Compare. I use grsync to sync my files/folders between linux and windows. It is a gui front end to rsync. You can set it to ignore existing files, keep permissions, etc. It doesn't have a file or tree view of things though. It does have a simulate option to let you simulate the sync and see what would happen.

---

### Post by ricegf on 2008-03-26
> **Eddy5 said:**
> I'm looking for a decent folder/file sync program for Ubuntu. I've tried rsync and unison in the past and they were awkward to use and didn't really do what I want.
I've been using Beyond Compare in Windows and it's exactly what I want. It compares 2 dirs recursively, and shows me which folders/files don't match in a tree list. I can then select files to sync or not sync as required.
[http://www.scootersoftware.com/](http://www.scootersoftware.com/)
Is there anything available like this in Ubuntu?
I'm very fond of Beyond Compare on Windows. No clone is available on Ubuntu as far as I know, but Gnome Commander (from Universe) has a lot of similar functionality (compare as well as sync folders), plus MUCH greater file management capability. 

You'll need to invest a little time to learn it, but I think you might find it the better option. Fortunately, it's also available on WIndows (as Midnight Commander).  :-)

---

### Post by Fury5000 on 2008-03-27
I tried a few from the repository and settled on Krusader.  Its an advanced twin-panel file management/sync app.  It was the closest thing to a windows app "Allway Sync" I was running before dropping Win completely.

Give it a try on some test directory's first.

---

### Post by earobinson on 2008-03-27
I use a an svn repo, synced, backedup and changes are saved :)

---

### Post by Jumbao on 2008-03-29
> **Eddy5 said:**
> I'm looking for a decent folder/file sync program for Ubuntu. I've tried rsync and unison in the past and they were awkward to use and didn't really do what I want.
I've been using Beyond Compare in Windows and it's exactly what I want. It compares 2 dirs recursively, and shows me which folders/files don't match in a tree list. I can then select files to sync or not sync as required.
[http://www.scootersoftware.com/](http://www.scootersoftware.com/)
Is there anything available like this in Ubuntu?


You have to try kdiff3. Is is better tnah Beyond Compare.

---

### Post by Eddy5 on 2008-04-11
I had a few stability issues with Krusader but Gnome Commander looks great and works well. However when I click on Diff or Synchronise nothing happens. The diff command seems to be installed OK on my machine. Do you know how I can fix this?

---

### Post by oygle on 2008-04-14
I have been using beyond Compare for many years now, LOTS of features, and I doubt if there is anything that runs on Linux that can do 'all' that BC can do.

People have used it under WINE, and there are plans to have a Beyond Compare for Linux in the next version.

See [Scooter Forums: BC2 running on Linux!]("http://www.scootersoftware.com/ubbthreads/showflat.php?Cat=0&Board=stories&Number=9470&Searchpage=1&Main=9320&Words=linux&topic=&Search=true#Post9470")

---

### Post by oygle on 2008-04-15
See [The Beyond Compare V3 Beta]("http://www.scootersoftware.com/beta3/index.php") page for all the info.  It is due for release at the end of this week.

---

