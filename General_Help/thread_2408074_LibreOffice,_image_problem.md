---
title: "LibreOffice, image problem"
date: 2018-12-13
forum: General Help
---

### Post by jtappin on 2018-12-13
Of late (I think since upgrading to Bionic, but I'm not quite sure of the start point), I've been having problems including images into LibreOffice documents.
PDFs are OK, but eps, jpg and png all fail. Text and presentation documents I get an error message "Image filter not found" (for Presentations it has an error message icon, for Text an information icon, but the text is the same) for spreadsheets it just fails silently.
I am running Bionic, with LibreOffice 6.0.7.3 (but it was also present in what ever was the previous package, as it didn't start today).

I do NOT see the problem on a Manjaro box with LO 6.1.3.2.

My gut feeling is that there's probably a package missing, but I can't see any likely candidates. Does anybody have any ideas or is this a bug in either 6.0.x or the Ubuntu package?

---

### Post by ajgreeny on 2018-12-13
I am using LO from the ppa repos, version 6.1.3.2, the same as in your Manjaro system, and do not have any problem inserting images using that.

I assume you are using either the **Insert -> Image** menu item, or possibly the **Insert image from file** toolbar icon, if you've enabled it, and then navigating to the image in the dialogue box that appears, but if not let us know how you are trying to insert images.

---

### Post by jtappin on 2018-12-14
> **ajgreeny said:**
> 
I assume you are using either the **Insert -> Image** menu item, or possibly the **Insert image from file** toolbar icon, if you've enabled it, and then navigating to the image in the dialogue box that appears, but if not let us know how you are trying to insert images.
Either: **Insert -> Image** menu item or clicking on the image icon in a presenter content box.

Which PPA are you using?

---

### Post by ajgreeny on 2018-12-14
This one.
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

I have used it for a few years now and it has never let me down, but of course, you may find things different.
Worth a try, I suggest.

---

### Post by HermanAB on 2018-12-14
I would launch soffice from a terminal and then watch the error messages when trying to insert an image.

---

