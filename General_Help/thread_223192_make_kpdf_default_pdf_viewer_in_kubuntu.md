---
title: "make kpdf default pdf viewer in kubuntu?"
date: 2006-07-26
forum: General Help
---

### Post by bakinsoda on 2006-07-26
Hi all,

I would like to make kpdf the default pdf viewer (again) in Kubuntu 6.06.  When I installed Adobe Reader, it became default.  Then I tried making kpdf default by right-clicking, selecting "open with" "other" then selecting kpdf in kmenu (command: kpdf %U %i %m -caption "%c").  However, when double clicking a pdf file, i get a kinit error.

When i right click, open with, choosing regular KPDF (not the open with), the file opens fine.

I just can't get it to default.  Any ideas how i can do this?

Thanks

---

### Post by Jucato on 2006-07-26
Try this:
In Konqueror, go to Settings > Configure Konqueror > File Assocations. In the search bar, type in "pdf" and look for the pdf entry (you have to expand the application entry). Once you have pdf selected, in the General Tab, make sure that KPDF is on the top of the list. (There are Move Up/Down buttons at the side)

Hope that helps.

---

