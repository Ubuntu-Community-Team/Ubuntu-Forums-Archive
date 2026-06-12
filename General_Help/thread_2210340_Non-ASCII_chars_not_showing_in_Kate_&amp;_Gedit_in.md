---
title: "Non-ASCII chars not showing in Kate &amp; Gedit in 13.10"
date: 2014-03-10
forum: General Help
---

### Post by michael118 on 2014-03-10
I'm trying to edit some files that were originally encoded in something like ISO-8859-15 (I'm not too sure). When the files are opened in Kate (13.8) on my Debian 7 box they display perfectly, with that encoding auto-selected.  But when I open the same files using Kate (13.11.5) on my laptop with Kubuntu 13.10 installed, the non-ascii characters are replaced by an empty box character. This happens if I select the ISO-8859-15 encoding at the File Open dialogue within Kate, or if the encoding is autodetected (i.e when I open the file from Dolphin).  I've converted the files to UTF-8 encoding on my Debian box using the save-as function in Kate (which seemed to work fine), but the non-ascii chars still don't display on my Kubuntu 13.10 either in Kate or in Gedit, which baffles me.

Can anyone help?

---

### Post by michael118 on 2014-03-10
Okay, found a work-around (why does that always happen when you ask for help?). 

I suddenly realised that the actual character encoding would be something special and old for Windows, like CP 1252. The file now displays properly on Kubuntu (and on Debian). 

Also, by opening the original file with CP 1252 encoding, the conversion to UTF-8 works when the file is viewed in Kubuntu. 

So, the question is -- was the Debian version of Kate at fault or the Kubuntu one -- Perhaps something to ask on the Debian forums....

---

