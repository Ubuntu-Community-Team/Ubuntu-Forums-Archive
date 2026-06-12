---
title: "Default applications"
date: 2013-06-23
forum: General Help
---

### Post by bnmoreno on 2013-06-23
Hi there,

I'm having a problem to open PDF files. I found some information but no one could help me. I like to use evince to open PDF files and I use other applications for different purposes, like Adobe Acrobat Reader, Okular and Mendeley. The problem started when I migrated Unity to Gnome and the default application to open PDF files was setted (I dont know why) to Adobe program. First I tried to do the basic: clicking the right button over a PDF file and trying to set the default app, but the first problem was because no of these application were shown in the list. After, I followed the information found in some forums and in summary I basically edited the fileS default.list (one presented in "/etc/gnome" and another one in "/usr/share/applications") by changing the line as follow: "application/pdf=evince.desktop". 

Even doing these changes I could not open using evince and now PDF files are being opened by Mendeley. I dont know what I have to do, I didnt find any information that could help me. Anyone could help me?

And another question: which of these files should I really edit?

Regards,

Bruno Moreno

---

### Post by bnmoreno on 2013-06-27
Hi there, just to let you know that I solved this problem by deleting the file "evince.desktop" from "/.local/share/applications" and restarting my machine.

---

