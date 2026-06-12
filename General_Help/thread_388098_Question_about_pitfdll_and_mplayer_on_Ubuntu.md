---
title: "Question about pitfdll and mplayer on Ubuntu"
date: 2007-03-19
forum: General Help
---

### Post by moot on 2007-03-19
It seems that you can no longer install pitfdll by merely entering "sudo apt-get install gstreamer0.10-pitfdll" into the terminal and it doesn't show up in SPM.  What happened to it, and is it OK or even necessary to install it from here:

[http://sourceforge.net/project/showfiles.php?group_id=137113&package_id=150683&release_id=370855](http://sourceforge.net/project/showfiles.php?group_id=137113&package_id=150683&release_id=370855)

Also, I can't find mplayer in SPM, only kmplayer, which I installed and it seems to run fine except for certain .wmv files.  Is it ok to use kmplayer in Ubuntu, or do I have to install mplayer directly from the source?

---

### Post by unebaguettesvp on 2007-03-19
in SPM, in Settings->Repositories, did you check off multiverse and universe?

---

### Post by moot on 2007-03-19
> **unebaguettesvp said:**
> in SPM, in Settings->Repositories, did you check off multiverse and universe?

Yes, I checked off everything including multiverse and universe.

---

### Post by unebaguettesvp on 2007-03-19
You know what, you're right. I don't see pitfdll in SPM either. I do, however, see mplayer and mplayer32 (I'm on 64 bit). I don't think I need pitfdll cause I'm not using gstreamer library in totem. I'm using xine. Sorry!

---

### Post by moot on 2007-03-19
Ok, does anyone else know about the status of these two packages?  I can also see the Firefox plugin for mplayer, so I tried to queue that up, figuring that it would install mplayer itself because it was dependent on mplayer, but it didn't let me :(

---

### Post by moot on 2007-03-19
BTW, I had this same problem with the mstcore fonts package, it mysteriously disappeared even though tutorials written this year mentioned it and I had to take all of my *.ttf fonts from my XP partition.  And while I'm on the subject of fonts, does anyone know what the default font settings are for Windows XP?  I want the text in Ubuntu to look just like it did in XP.  So far I've narrowed down the choices to:

Ariel
Courier New
fixedsys
Microsoft Serif
System
Tahoma
Times New Roman
Trebuchet

---

### Post by moot on 2007-03-21
Bump, are pitfdll and mplayer really MIA?

---

### Post by zvacet on 2007-03-21
If you are still interested you can find it in FF search engine>Ubuntu packages>pitfdll

---

