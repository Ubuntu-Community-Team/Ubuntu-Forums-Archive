---
title: "Just upgraded to 17.10 -- PDF image processing broken, somehow?"
date: 2017-10-25
forum: General Help
---

### Post by alex254 on 2017-10-25
I'm having a problem where I can't copy images out of PDFs. I need to copy large numbers of images out of PDFs as part of building virtual tabletops on services like Roll20.

Unfortunately for me, I just upgraded to 17.10, and possibly as part of that upgrade I'm now seeing PDF images being corrupted when I attempt to copy and paste them out into GIMP. I've found two applications so far that will actually let me copy the raw image data (not a screenshot): Evince and LibreOffice. Both exhibit a problem where the first portion of the image comes through but the remainder (usually at least 80%) of the image has been replaced with a gray box.

It doesn't appear to be something solely with the clipboard, however. I can copy images out of browsers without issue. (Hilariously, I cannot easily get to the images by loading the PDFs in the browser, though.)

This also happens when I paste into image editors that aren't gimp--for example Pinta.

I have a few workarounds. I can get at the files eventually by telling Evince or LibreOffice to save the files separately. I'd really prefer not to have to change a process that is well within the expected basic functionality.

Any ideas?

---

### Post by alex254 on 2017-11-02
Discovered something else interesting about this. It only happens in GNOME--working in Unity, there's no problem.

Hmmm.

---

