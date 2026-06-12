---
title: "Print preview of PDF document in Evince"
date: 2021-09-30
forum: General Help
---

### Post by paulbenz on 2021-09-30
When I do a print preview of a PDF document in "Evince" all I see is a blank sheet and therefore can not print the document. What do I need to do in order to see the document in print preview mode?? I am currently using Ubuntu 20.03 latest long term support desktop software.

---

### Post by guiverc on 2021-09-30
Ubuntu 20.03???

You've also put this in a *flavor* area & *tagged* Lubuntu (which uses LXQt & comes with `qpdfview` as the PDF viewer)  

There were some issues with the Qt5 that came with 20.04 LTS that impact printing; thus impact Lubuntu 20.04 LTS, but shouldn't impact `evince` as that doesn't use Qt5 libs (Ubuntu's GNOME uses GTK3, and only Kubuntu & Lubuntu used the impacted Qt5).

---

