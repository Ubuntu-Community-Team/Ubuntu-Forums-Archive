---
title: "opening exe files in ubuntu"
date: 2007-10-16
forum: General Help
---

### Post by banana split on 2007-10-16
Hi again. I'm trying to load the Robert-Collins bilingual dictionary on CD-Rom and Ubuntu won't open the setup.exe file to load the CD-Rom. Any solutions?
I have Windows on my virtual PC but I can't access the CD-Rom from it.

---

### Post by bodhi.zazen on 2007-10-16
You would need to look into wine ...

Linux does not directly run windows binaries

---

### Post by r-mo on 2007-10-16
I can't by any means guarantee this will work but you could try using wine, you may be better off finding out how to make your cdrom available in virtual pc, i've only ever used virtualbox and parallels so can't help you there :(.  If you 

---

a) The GUI Way

Go System->Administration->Synaptic Package Manager

Click in the list of available apps and type 'wine'

Tick the box to install, and click apply.

b) The terminal way

Applications->Accessories->Terminal

sudo apt-get install wine
y

---

Then

Go into your cdrom, find the setup.exe, right click and 'open with' -> other
Use Custom Command, in the text box type 'wine' then click on open

Good luck...

---

### Post by banana split on 2007-10-17
Unfortunately, when I do a search in the list of applications in the Synaptic Package Manager
I only find winefish or libwine?????

---

### Post by bodhi.zazen on 2007-10-17
you need to enable your repositories : 

[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

