---
title: "Open Office window problem"
date: 2007-05-21
forum: General Help
---

### Post by dans on 2007-05-21
I somehow created a very odd window situation for OO.org Writer only.

The symptom is a window which is 
   *  full-size (not Full Screen mode, but takes up entire screen including over my panel), but 
   *  does not have a window frame (no blue bar at top or framing) but 
   *  Alt-Space window menu is available, although the needed resize, move and restore are grayed out.

The conditions are
   *  OO Writer only, not spreadsheet, Draw, etc.
   *  Saved in OO settings, happens opening any existing or new document

I can fix it by removing the folder ~/.openoffice.org2 from my home directory.  But that's kind of extreme.

Is this a bug?

If not a bug, how do I get out of this mode?

---

### Post by DoctorMO on 2007-05-21
if removing .openoffice2 works then it will be an option in the writer preferences. for a quick fix you can just remove your settings. unless you had a lot set?

---

### Post by dans on 2007-05-21
I would prefer not to remove all my settings, but so far that is the only fix.  I cannot find anything in the Help, Options dialog or standard menus that creates this mode.  That's what I'd really like to find.

---

### Post by HokeyFry on 2007-10-16
im having this same problem, but it is with presentation and removing the configuration folder doesnt fix it. any ideas?

---

### Post by vanndrage on 2007-12-14
i am having the same issue with spreadsheet on 2 different computers, has anyone found a fix for this yet? i have also tried removed the openoffice folder in my home directory and this did not help.

---

### Post by jimmy the saint on 2007-12-14
try using a different theme.  Many themes seem to be incompatible with the open office gtk integration file.  If you are not using the human theme, enable it, then try again.  If this fixes your problem, you will know that is the proble.

---

### Post by nico100 on 2008-02-10
It is GTK related. I solved the same issue by downloading 'openoffice.org-gtk' in synaptic.

---

