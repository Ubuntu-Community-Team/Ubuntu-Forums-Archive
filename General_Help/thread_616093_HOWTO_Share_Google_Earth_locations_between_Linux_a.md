---
title: "HOWTO: Share Google Earth locations between Linux and Windows"
date: 2007-11-17
forum: General Help
---

### Post by Endolith on 2007-11-17
I have a dual boot Linux/Windows system.  I had a whole bunch of locations saved in Google Earth, and wanted to use them in Linux.  But I didn't just want to *use* them; I want new places I add in either OS to show up in the other.   You have to have ntfs-3g installed with NTFS access.

1. Open up /media/windows/Documents and Settings/username/Application Data/Google/GoogleEarth
2. Right-click myplaces.kml
3. Click "make link" and it will create a link in this directory.
4. Right-click the link and select "Cut"
5. Open /home/username/.googleearth
6. Paste the link into this directory.
7. Rename "myplaces.kml" to "myplaces backup.kml" or something like that
8. Rename the link to "myplaces.kml"

Now when you open Google Earth, it will open the places from your Windows directory, and when you save, it will save to that partition.  You can then open Google Earth in Windows and see the same places.   If you have places in "myplaces backup.kml", you should be able to open that independently in Google Earth and move them into your main Places menu to save them.

---

