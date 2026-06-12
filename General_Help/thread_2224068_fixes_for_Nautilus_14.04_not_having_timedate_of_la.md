---
title: "fixes for Nautilus 14.04 not having time/date of last modification?"
date: 2014-05-14
forum: General Help
---

### Post by genejohnson55 on 2014-05-14
I'm finding the Nautilus provided in 14.04 next to useless for dealing with files. It does not give enough detail on when files were modified. It no longer has an ISO format for date/time. I can't believe the developers approved removing this essential feature of a file browser.

Are there any plugins or any solutions to get this feature back into 14.04 Nautilus? I need to know not only the date of last modificiation but also the time that the modification occured.

Thanks for any help you can provide guys.

---

### Post by gifford on 2014-05-14
Have you tried setting your Nautilus preferences to list view instead of icon?
Using list view you can also modify what the list displays.

---

### Post by Vaphell on 2014-05-14
nautilus is supervised by the gnome team and for whatever retarded reason they removed the customization. Afaik you'd have to either recompile nautilus with the patch restoring the functionality on your own or install another file browser not tainted with gnome's hardcore minimalism.

---

### Post by genejohnson55 on 2014-05-14
> **gifford said:**
> Have you tried setting your Nautilus preferences to list view instead of icon?
Using list view you can also modify what the list displays.

I meant to mention in OP that I have List View set as default view. All I see is List View.

---

### Post by genejohnson55 on 2014-05-14
> **Vaphell said:**
> nautilus is supervised by the gnome team and for whatever retarded reason they removed the customization. Afaik you'd have to either recompile nautilus with the patch restoring the functionality on your own or install another file browser not tainted with gnome's hardcore minimalism.

This goes beyond minimalism though. Users need to be able to differentiate (for example) between a file modified at 4:34 and another modified at 4:35. There's no way to tell this in the new Nautilus. do GNOME devs not use their file browser like the rest of the world does?

---

### Post by Vaphell on 2014-05-15
this is pure gold:
[Use a better date format by default instead of making the user guess]("https://bugzilla.gnome.org/show_bug.cgi?id=676898")

> "We have a number of date formats currently. There are even user settings
for it. None of them are very good and worse we choose the longest and
most distracting one rather than the most compact one."

"Use a better date format by default instead of making the user guess"


and then bam, a patch that rips the whole customization out. I think they were hell bent on minimizing the amount of space taken by the timestamp (for whatever reason columns cannot be compressed below their minimum width imposed by the content), use cases be damned.


users complaining about the loss of functionality
[https://bugzilla.gnome.org/show_bug.cgi?id=721084](https://bugzilla.gnome.org/show_bug.cgi?id=721084)  **Status: RESOLVED, Resolution: NOTABUG **  rofl
[https://bugzilla.gnome.org/show_bug.cgi?id=699055](https://bugzilla.gnome.org/show_bug.cgi?id=699055)

---

### Post by mc4man on 2014-05-16
Here is a test build of nautilus for trusty where 'time/date of last modification' can be exposed in * listview* thru > view > visible columns.. > Modified (full)
[https://launchpad.net/~mc3man/+archive/nauty-mods](https://launchpad.net/~mc3man/+archive/nauty-mods)

nautilus source is from trusty-proposed, also inc. [a bug fix from utopic]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1184720")
A couple of the generic additional patches from the  set I use are also included - 
open with on folders
real file  owner name displayed
File Manager as name of launcher

The time-date patch isn't throughly tested by me, any found issues or suggestions can be mentioned here or thru launchpad email.
Read the ppa page for some info & how to easily revert if desired.
(If useful will then keep up if need be.

---

### Post by genejohnson55 on 2014-05-16
> **mc4man said:**
> Here is a test build of nautilus for trusty where 'time/date of last modification' can be exposed in * listview* thru > view > visible columns.. > Modified (full)
[https://launchpad.net/~mc3man/+archive/nauty-mods](https://launchpad.net/~mc3man/+archive/nauty-mods)

nautilus source is from trusty-proposed, also inc. [a bug fix from utopic]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1184720")
A couple of the generic additional patches from the  set I use are also included - 
open with on folders
real file  owner name displayed
File Manager as name of launcher

The time-date patch isn't throughly tested by me, any found issues or suggestions can be mentioned here or thru launchpad email.
Read the ppa page for some info & how to easily revert if desired.
(If useful will then keep up if need be.

Is this something Canonical can add to official updates so everyone gets it? IMHO Canonical never should have allowed the release of a file browser that doesn't have option to view date/time of file modification. This is an absolutely essential feature for any file-browser to have.

---

### Post by Vaphell on 2014-05-16
that's why they are planning to roll their own file browser to cut dependencies on gnome.

[http://news.softpedia.com/news/Ubuntu-to-Drop-Nautilus-Soon-and-Replace-It-with-Their-Own-File-Manager-423015.shtml](http://news.softpedia.com/news/Ubuntu-to-Drop-Nautilus-Soon-and-Replace-It-with-Their-Own-File-Manager-423015.shtml)

---

### Post by genejohnson55 on 2014-05-17
> **Vaphell said:**
> that's why they are planning to roll their own file browser to cut dependencies on gnome.

[http://news.softpedia.com/news/Ubuntu-to-Drop-Nautilus-Soon-and-Replace-It-with-Their-Own-File-Manager-423015.shtml](http://news.softpedia.com/news/Ubuntu-to-Drop-Nautilus-Soon-and-Replace-It-with-Their-Own-File-Manager-423015.shtml)

sure. it's not hard to figure why Canonical feels compelled to do this. But why did they release an LTS with a broken file-browser? Canonical should fix this with a . release. But does anyone know if they have plans to do this?

---

### Post by philinux on 2014-05-17
[http://m.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html?m=1](http://m.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html?m=1)

You could give Nemo a whirl.

---

### Post by philinux on 2014-05-17
[http://m.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html?m=1](http://m.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html?m=1)

You could give Nemo a whirl.

---

