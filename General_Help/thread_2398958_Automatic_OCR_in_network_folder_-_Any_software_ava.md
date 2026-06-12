---
title: "Automatic OCR in network folder - Any software available?"
date: 2018-08-20
forum: General Help
---

### Post by kaktux on 2018-08-20
hi there,

i got a network scanner where you can set a folder where all scans will be stored.

So my question is: is there any software available for ubuntu/linux that can watch this folder and automatically (or semiautomatically) OCR all new files and documents that are stored there?
Also it would be nice if a tag function is available (like tagging all documents that have "invoice" on them or similar) - but this could also be with a second software solution. 

Is something like that available? I could only find scan programs where you could manually do this while scanning (and not with a network scanner).

---

### Post by Holger_Gehrke on 2018-08-20
I don't know of anything ready-made, but it should be possible to adapt existing software for your use case with a bit of scripting. There's a tool named 'incron' which waits for and reacts to events in the file system. Configure that to watch the folder into which your scans go and have it call some OCR (tesseract, perhaps) to read newly arrived files (and perhaps move them out of the folder and archive them afterwards).

Holger

---

### Post by wyliecoyoteuk on 2018-08-20
This looks like it:

[https://sourceforge.net/projects/lios/](https://sourceforge.net/projects/lios/)

---

