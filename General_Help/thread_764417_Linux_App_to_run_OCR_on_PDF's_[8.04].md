---
title: "Linux App to run OCR on PDF's? [8.04]"
date: 2008-04-23
forum: General Help
---

### Post by shmoe010 on 2008-04-23
I'm trying to take a number of academic texts that I only have available as PDF's and run OCR software on them to make the text searchable. So far I haven't found an application, but it seems like a pretty common task so I'm sure there's a way to do it, I've just never done it in Linux before.

I could always borrow an winblows box and use acrobat professional... lol not

I have these apps installed already but haven't been able to do what I need to with them, so if you know how to do it in one of these please let me know:

KPDF
Kooka
XSane

Otherwise, if there's another app I can get that would be great. 

any ideas are appreciated :)

---

### Post by Vadi on 2008-04-23
There is adobe reader avialable for linux. But would you just like to make the pdf searchable? Because I believe the tracker tool can already index them.

It's disable by default though (since indexing everything does put load on the system), but you can enable it by going to system - preferences - search and indexing and "enable indexing".

Give it a bit of time and then try searching by doing alt+f2 and typing in "tracker" (and select the first app that comes up).

---

### Post by ryanhaigh on 2008-04-24
What you want is [gocr](apt://gocr) which is a commandline optical recognition program, there are also GUI frontends which you can find by searching for ocr or gocr in synaptic (system>admin>synaptic)

This thread, and the script that is in there may be useful to you, depending on how the pdfs have been done you may not need to convert them to jpgs first. If you have any issues post back and I will try to help.

---

