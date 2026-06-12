---
title: "Viewing an eFax"
date: 2006-10-17
forum: General Help
---

### Post by wanderingscrybe on 2006-10-17
I'm still fairly new to the Linux experience and have been testing the waters for some time now.  I'm ready to jump in, but so far the only thing holding me back is that I need to be able to view eFax (.efx) documents.  
I've tried searching the net as well as Ubuntu help, but wasn't able to find anything regarding the viewing of these kinds of docs.  
Is it something really simple that I've just totally missed?  What program do I use to view .efx docs?

Thank you!

---

### Post by kuja on 2006-10-17
It's more than likely something closed source (and without a Linux implementation). You may not be able to view them in Linux.

---

### Post by IcemanV9 on 2006-10-17
Try to install eFax with ***[COLOR="Orange"][Wine]("https://help.ubuntu.com/community/Wine")[/COLOR]***. I just checked with ***[COLOR="Orange"][WineHQ]("http://appdb.winehq.org/appview.php?iAppId=667")[/COLOR]*** DB. It seems that it does work.

---

### Post by Scunizi on 2006-10-17
eFax is owned by J2.com who also uses Messenger.  It's the same as eFax messenger.  The way around the problem is to log onto your eFax service and change the default delivery method from an efx file type to a tif file type.  Tif's you'll be able to read in the Document viewer in Ubuntu.  Unfortunatly, I'm still hunting for a messenger like piece of software that will allow signature stamps, editing and text inclusion, flattening of the image and saving agian with the included data to a tif or pdf.  I've found that's indespensable.  My work around had been to load Windows through VMWare and run messenger there.  It also fixes my scanner issues. My scanner is recognized by Ubuntu but there aren't ANY drivers for it anywhere outside of the windows world....... Good Luck!

---

### Post by wanderingscrybe on 2006-10-18
Thanks to all for the advice so far.  I'm not sure if the .tif method can be done in my case since there are several other people in the company using eFax in Windows, and they aren't going to want anything changed around (it's surprising how resistant to change my technology company is).

As for WINE, I'll see if I can get it up and running in Ubuntu.  If anyone has tips/tricks for doing this, it would be much apreciated.

Thanks again!

---

### Post by Scunizi on 2006-10-18
Fortunatly the messenger program can default efx and tiff files at the same time.  However I can see how there would be resistance to the change espicially if your company does any graphics for internal or external use. Tiff is a common graphics format.  I think you'll end up frustrating yourself trying wine with the messenger program.  My solution was with VMWare server (free) and doing a full install of windows under VMWare inside of Ubuntu.  I think Messenger requires some of windows .net features or IE6 stuff that makes it windows propiatory (sp?).  VMWare is pretty easy to set up.

---

### Post by bliffle on 2007-11-23
I tried installed efax 'msgrplus' under 'wine' but it failed because it needs IE preinstalled on the system.

---

