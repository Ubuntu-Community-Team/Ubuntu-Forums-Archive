---
title: "Can I Stop Nautilus 3.8.2 Auto-Opening Folders During Drag &amp; Drop? + Refresh Problem"
date: 2013-12-20
forum: General Help
---

### Post by OzzyFrank on 2013-12-20
Hi. After upgrading to 13.10, I couldn't help but notice some strange (and annoying) behaviour in File/Nautilus (3.8.2), and was wondering how to change/disable these. I'll outline the 2 main things that bug me, starting with the annoying "auto-refresh" which also affects drag & drop:

(1) Nautilus keeps refreshing/reloading the window after the most mundane of tasks, such as dragging a file from one open folder window to another. Before, for example, if I dragged a picture from my Downloads folder into a sub-folder of Pictures containing many images, it might take a second or two to draw the thumbnail for that image, but now the whole folder decides to reload, meaning it starts redrawing the thumbnails for all the pictures in the folder (which can take the better part of a minute, and will do that nearly every single time I drag a new file there).

(2a) Drag & drop of a file to a sub-folder of the current window results in Files opening the destination folder if I hover over it for more than half a second. Seriously, I have to be REALLY quick with the drop, as even a full second seems too long, and the window will open to the folder I am hovering on. Besides not wanting to end up in every folder I am dragging files into, as you can imagine it's really annoying accidentally ending up in surrounding folders simply because the dragging of a file took a couple of nanoseconds too long (I have to drag within the empty spaces between folders to avoid that!).

(2b) Previously, if I was to drag a file towards a folder in the same window, and that destination folder was out of view, I could hold that file near the top of the window, and it would scroll upwards until I reached the folder. Now, if I hold the file near the top, wishing for the window to scroll, it actually refreshes itself and then the very top of the window (ie: the first screen-load of folders) appears. This is really annoying if the desired folder was only a line or so out of view, as it means I end up at the top, then have to hold the file near the bottom so the window scrolls down.

So, any ideas how to disable these annoying auto-reload and drag & drop behaviours? (And please don't suggest using another file manager - I've already turned to Nemo, but would like to return Nautilus to how it was in 13.04).

---

### Post by mc4man on 2013-12-20
The 'auto open on hover' is not a user configurable item

Myself find it quite annoying & also sometimes useful so have approached this way
I wrote a patch to disable it in icon view but have left it enabled in list/tree view, on breadcrumbs  & in the sidebar.

If you wish to rebuild can attach patch, have it in at least one ppa but there are other changes that may not be desired
(toolbar adjust, open with on dir.'s, no ME on file owner
  - pkexec enabled w/ add. nautilus-pkexec binary
 revert-canvas-view-hover.patch
  - breadcrumbs, listtree & sidebar still active
default-win-size.patch )

---

### Post by vanadium on 2013-12-21
I am no sure to what extent useability of new features are being tested. This feature makes it unworkeable to sort a few files in a few different folders.

---

### Post by OzzyFrank on 2013-12-21
It seems the Nautilus team is committed to not only the gradual dumbing-down of a once-great file manager, but also adding new annoying behaviours that pretty much coincide with each new Ubuntu release. I figure they assume everyone likes relearning how to use their file manager at least once a year. To me, it was annoying enough when they removed the status bar - sure, I understand that was because of where Gnome 3 was headed, removing status bars and other use things, but to not think of doing something like having the free disk space in the title bar or something (or at the very least in the floating status bar that appears when clicking a file) was bound to irritate a lot of users (with that, the answer was always "Oh, all you have to do is right-click and choose Properties!" - idiotic). Now this latest crap has seen me move to Nemo, and now that I've found myself playing around in KDE, I might even start using Dolphin (now that I've disabled that annoying one-click to open function). Nautilus is losing users in droves, so I simply can't understand their logic. It's like they're deliberately trying to get everyone to stop using it.

---

### Post by vanadium on 2013-12-22
What drove me away is that nautilus now resolves symbolic links rather than just following them. This degrades the powefull symbolic links of linux/unix to dumb windows 95 style shortcuts, and prevents you from organizing the data you want. 
> And please don't suggest using another file manager - I've already turned to Nemo, but would like to return Nautilus to how it was in 13.04). 
Sorry, but you must be a programmer. Nautilus is open source, after all.

---

### Post by OzzyFrank on 2013-12-22
> **vanadium said:**
> Sorry, but you must be a programmer. Nautilus is open source, after all.

So, you're saying I should learn how to code? Yeah, I think I'll just stick with Nemo...

---

### Post by vanadium on 2013-12-23
> **OzzyFrank said:**
> So, you're saying I should learn how to code? Yeah, I think I'll just stick with Nemo...

That is also what I did ...

---

### Post by jjchico on 2014-02-17
What surprises me most is that you do not have an option to control this behaviour even under dconf/gsettings. I am also switching to Nemo because of it.

There is a version of Nemo with its own PPA for Ubuntu 13.10 and 14.04 including Unity integration:

[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

---

### Post by vinx on 2014-05-06
It is really the most annoying thing I've seen in years! It drives me crazy, if not completely pissed off when I accidentally drag a file into a subfolder, again. It is a really bad copy from OSX, where you have a longer delay. 

Bug-report: [https://bugzilla.gnome.org/show_bug.cgi?id=727790](https://bugzilla.gnome.org/show_bug.cgi?id=727790) and [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1301083](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1301083) - please help giving it some attention.

---

