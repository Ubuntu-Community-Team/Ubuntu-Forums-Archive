---
title: "Can't print from inkscape - Where to post bug report?"
date: 2013-11-15
forum: General Help
---

### Post by old.dog on 2013-11-15
I am unable to print from inkscape with my HP C5180 but open office draw and other programs work OK.

I posted a question on the hplip site but have not yet received a solution.
see:  [https://answers.launchpad.net/hplip/+question/237292](https://answers.launchpad.net/hplip/+question/237292)
At the suggestion of Goutam I captured some additional information using hp-logcapture and discovered that pagesize custom causes the word "custom" to be repeated as shown below.

"MediaType=Automatic PageSize=Custom.Custom.612.00x792.00 OutputMode=Normal "

This appears to be the same bug that was corrected on gnome as bug 679883
see:  [https://bugzilla.gnome.org/show_bug.cgi?id=679883](https://bugzilla.gnome.org/show_bug.cgi?id=679883)
This bug was corrected by a patch to the file gtkprintbackendcups.c.  I am using Mint 13 with mate desktop, hplip-gui 3.12.2-1ubuntu3.3 and inkscape 0.48 and subsequently this file is not present on my system.

My problem is that I think I need to file a bug but I don't know where to file it.  Is this an hplip problem or possibly mate?

Thanks 

Dan

---

### Post by Frogs Hair on 2013-11-15
There is an Inskape bug page at the link and searched printing. 

[https://bugs.launchpad.net/inkscape/+bugs?field.searchtext=printing&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/inkscape/+bugs?field.searchtext=printing&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by old.dog on 2013-11-15
I found ubuntu bug 998156 which addresses this issue.  The bug is listed as 'in progress' so, I guess, when it is fixed in ubuntu it will flow down to linuxmint.

I previously searched inkscape bugs but missed it.  Sorry but I am new to the bug tracking world.

---

