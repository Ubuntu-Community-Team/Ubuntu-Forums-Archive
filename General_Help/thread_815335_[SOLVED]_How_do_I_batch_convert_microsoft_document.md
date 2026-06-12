---
title: "[SOLVED] How do I batch convert microsoft documents to open source formats?"
date: 2008-06-01
forum: General Help
---

### Post by Rytron on 2008-06-01
Hi,
How do I batch convert microsoft documents to open source formats?
For example how would I convert a folder of .doc files to .odt?
The same question would go for xls, pps, ppt, mdb(not sure if this is viable), etc to Open Office formats.
Any input much appreciated.
Bye.

---

### Post by OliverW on 2008-06-01
Use File > Wizards > Document Converter
It's an easy wizard that lets you convert whole directories of files.

---

### Post by Rytron on 2008-06-01
> **OliverW said:**
> Use File > Wizards > Document Converter
It's an easy wizard that lets you convert whole directories of files.

Hi OliverW,
I went to terminal, typed in openoffice.
Open Office started. I followed your advice [File > Wizards > Document Converter]

However when I opened the converter (image attached) this is the window I get(it wont allow me to enlarge the window!)

---

### Post by OliverW on 2008-06-01
Mmm from the looks of it, you have probably customized the look of your Ubuntu (and rightfully so :))

Try the following:
Save your current theme and reset everything to Ubuntu defaults (the looks I mean). From what I've witnessed different GTK themes and icons can sometimes mess with the layout of OpenOffice. Another option would be to temporarly move your .openoffice2 (it's in your home dir) directory to let's say .openoffice2_old. Then start OpenOffice again and it'll recreate this directory with the defaults.

This is what your dialogue should look like:

---

### Post by Lord Xeb on 2008-06-01
why are you converting M$ formats to odt formats? OpenOffice reads all of them just fine.

---

### Post by Rytron on 2008-06-03
> **OliverW said:**
> Mmm from the looks of it, you have probably customized the look of your Ubuntu (and rightfully so :))

Try the following:
Save your current theme and reset everything to Ubuntu defaults (the looks I mean). From what I've witnessed different GTK themes and icons can sometimes mess with the layout of OpenOffice. Another option would be to temporarly move your .openoffice2 (it's in your home dir) directory to let's say .openoffice2_old. Then start OpenOffice again and it'll recreate this directory with the defaults.

This is what your dialogue should look like:

Hi OliverW,
I tried both methods you suggested but no luck. Is there a specific method to 'reset everything to Ubuntu defaults'?

---

### Post by geirha on 2008-06-03
I believe it's a problem with compiz, which is the window manager that's used when you have visual effects enabled. Try diabling visual effects temporarily, by either going to System -> Preferences -> Appearance -> Visual Effects tab and selecting None, or typing ```
metacity --replace &
``` in a terminal. The latter will not be "saved" so after you log out and in again, you'll be back in compiz. You can also switch back to compiz from the terminal with ```
compiz --replace &
```

EDIT: It's reported on launchpad [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/149586](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/149586)

---

### Post by Rytron on 2008-06-03
> **geirha said:**
> I believe it's a problem with compiz, which is the window manager that's used when you have visual effects enabled. Try diabling visual effects temporarily, by either going to System -> Preferences -> Appearance -> Visual Effects tab and selecting None, or typing ```
metacity --replace &
``` in a terminal. The latter will not be "saved" so after you log out and in again, you'll be back in compiz. You can also switch back to compiz from the terminal with ```
compiz --replace &
```

EDIT: It's reported on launchpad [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/149586](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/149586)

Thank you so much geirha,
Your solution worked a treat.

:popcorn:

---

### Post by Rytron on 2008-06-03
> **Lord Xeb said:**
> why are you converting M$ formats to odt formats? OpenOffice reads all of them just fine.

I want to convert to Open Source formats as much as I can. This includes using .odt instead of .doc, .ogg instead of .mp3, and so on...

---

