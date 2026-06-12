---
title: "Firefox PDF viewer broken"
date: 2016-11-20
forum: General Help
---

### Post by John Jason Jordan on 2016-11-20
I have Xubuntu 14.04 up to date, including Firefox 50.0. When I click on a link to a PDF file on a web page Firefox will only download it. I went to Preferences > Applications and Adobe Acrobat Document is at the top of the list. The options are:
```
Always ask
Save file
Use (default)
Use evince
Use acroread
Use other ...
```
Regardless of which I set it to Firefox always pops up a window to specify the location and file name to save it to. 

There is supposed to be an option to open the file in a Firefox tab (using the built in Firefox PDF viewer), but that option is missing. I used to have it set to open the file in evince but that option has been broken for some time now. All I can do is download the file to disk and then open it from Thunar with evince (my default viewer). 

I hope someone can help because this is driving me nuts. :)

---

### Post by ajgreeny on 2016-11-20
Search for **pdf** in the Applications dialogue box of firefox preferences and see if that offers you the option.

I do not have **Adobe Acrobat Document** in my list of items to be opened, only pdf shows in the list and on my systems, both 14.04 and 16.04, I have a **Preview in firefox** option available and enabled.

---

### Post by John Jason Jordan on 2016-11-20
> **ajgreeny said:**
> Search for **pdf** in the Applications dialogue box of firefox preferences and see if that offers you the option.

Thanks. That solved the problem. The weird thing is that in Edit > Preferences > Applications "Adobe Acrobat Reader" is at the top of the list and setting it to evince does nothing. But if I search in that window for PDF (as you suggested) delivers a different list, and setting it to evince in that list works. Here are screenshots:

---

### Post by ajgreeny on 2016-11-21
Yes, strange I agree.

Have you by chance ever in the past installed the Adobe Acroread package which I believe was available in the past and may even still be, though I have never bothered to look for it.  Or do you have a shared FF profile between Windows and Ubuntu?

---

### Post by John Jason Jordan on 2016-11-21
> **ajgreeny said:**
> Have you by chance ever in the past installed the Adobe Acroread package which I believe was available in the past and may even still be, though I have never bothered to look for it.  Or do you have a shared FF profile between Windows and Ubuntu?

I do not have any Windows computers at all, although I do have XP in Virtualbox, which I practically never use. I have Firefox synced with my desktop computer (also running Xubuntu 14.04), but only for bookmarks. 

As for Acroread, I have always had it installed (current version 9.5.5 04/26/2013), but I seldom use it. I do a lot of desktop publishing, so I also have Foxit Reader 2.2, Okular (formerly kpdf), and a lot of PDF command line tools. Evince is my default PDF viewer.

---

