---
title: "konqueror PDF crash"
date: 2005-10-20
forum: General Help
---

### Post by scokar on 2005-10-20
Does this page:

[http://www.londondrugs.com/msib20/Flyer/oct_18_05/pdf/p01.pdf](http://www.londondrugs.com/msib20/Flyer/oct_18_05/pdf/p01.pdf)

cause konqueror to crash for anyone else running a freshly installed breezy kubuntu?

Thanks.

---

### Post by aysiu on 2005-10-20
I don't know because I'm using Gnome right now, but does the PDF work if you save it to your desktop, then open it (apart from Konqueror)? And does Konqueror work with other PDFs?

**Edit**: Okay. I tried it in Konqueror, and it crashed. Konqueror didn't crash with other PDFs, and that link you gave worked fine in Firefox. I don't know what's up with that.

---

### Post by penguinman007 on 2005-12-01
Default PDF reader has no hand, and cant resize left hand window.

Could not find acroread in packages.

Am downloading linux PDF reader in .gz format.

Will click on the gz file.

If adobe reader doesn't automatically install and work, I will not use ubuntu.

---

### Post by claydoh on 2005-12-01
That link caused kpdf to crash for me (using firefox) and it caused konqueror to do the same when I tried it there.

You can try to install acroreader if you want, which is in multiverse (that will have to be enabled itn your sources.list)

I got that pdf file to open by downloading the file, right-clicking on it and selecting Preview in ..Ghostview

penguinman007, the default view mode is the "hand" way, it just shows as a cursor until you grab a spot and move the page. And i am able to resize my left pane just fine, here. If you want the adobe acrobat reader (much slower imo) it is available as I mentioned above. But since you are trying to click on a .gz file to install it, and you will leave if it doesn't install, well then you aren't here to respond to this anyway :p

(Is it just me, or is the quality of trolls out there over the past few years gotten pretty low?)

---

### Post by casoe on 2005-12-12
I updated KDE 3.5 today and a new version of KPDF was installed. From there on kpdf and konqueror crashed on trying to open a pdf.

I reinstalled konqueror and kpdf. Now konqueror opens the pdf, but it shows only crosses on the pages. On pushing the back button konqueror crashes again.

What gives?

Starting kpdf from the console gives a "Bogus memory allocation size" error.

---

### Post by ERam123 on 2005-12-12
I am getting the same results.  Seems to be a new bug.  I got some updated packages today through the repositories, now either kpdf or one of the libraries or packages it depends on doesn't work.

Someone fix this?  I guess it ought to be submitted to bugzilla or something of the like?

EDIT: This seems to happen with all my PDFs.  I'll have to use KGhostView or acroread for now.  It's a pity though, kpdf is faster to render than either of those.

---

### Post by jeremy on 2005-12-13
I am getting the same, since todays update I cannot open any pdf file with kpdf in konq.
I can open kpdf from the menu, but it crashes when I try to open a file.

---

### Post by arska on 2005-12-13
Hi,
Same here after upgrading today get this error when trying to open a pdf:
"Bogus memory allocation size" followed by an immediate crach.

---

### Post by magnusbb on 2005-12-13
I am getting the same error. I hope this will be fixed soon. It happened after yesterday's updates. The kpdf that originally came with the KDE 3.5 Breezy packages worked great as expected.

---

### Post by jeremy on 2005-12-13
I have opened a bug report at [http://bugzilla.ubuntulinux.org/show_bug.cgi?id=20945](http://bugzilla.ubuntulinux.org/show_bug.cgi?id=20945)
Please add you comments.

---

### Post by vicks on 2005-12-13
(Just tried the pdf in windows with firefox w/ adobe acrobat and it crashed, so this bug must be quite deeply rooted within firefox (gecko?) or acrobat.)

Edit. Now it works. Strange, i almost never get crashes i windows while reading acrobats.

---

### Post by piquadrat on 2005-12-14
A temporary workaround is to downgrade kpdf to 4:3.5.0-0ubuntu0breezy1.1. But don't forget that it's affected by [this security vulnerability]("http://www.ubuntuforums.org/showthread.php?t=102554"), so pay attention to what files you open with it.

---

### Post by magnusbb on 2005-12-14
[QUOTE=piquadrat]A temporary workaround is to downgrade kpdf to 4:3.5.0-0ubuntu0breezy1.1. But don't forget that it's affected by [this security vulnerability]("http://www.ubuntuforums.org/showthread.php?t=102554"), so pay attention to what files you open with it.[/QUOTE]

A very efficient security fix, indeed - just to quit when opening every PDF I can think of. Why use the computer, after all? It can be dangerous. :D

Seriously, I hope this will be resolved before Christmas is over us. KPDF is really such a good application.

---

### Post by magnusbb on 2005-12-15
There is now a new version in the repositories which fixes this problem. Nicely done, developers! It's 4:3.5.0-0ubuntu0breezy1.3.

---

### Post by noigeaR on 2005-12-15
I've upgraded kpdf (and some other packages) using synaptic and I can confirm that the problem is now fixed. A big thank you to the kubuntu developers for fixing this so quickly! :D

---

