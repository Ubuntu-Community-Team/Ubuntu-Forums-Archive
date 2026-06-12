---
title: "Iso Mount script for a noob"
date: 2006-12-17
forum: General Help
---

### Post by HawaiinShirts4Life on 2006-12-17
Ok so i want to mount iso images of games (some to be used in wine, some normally) i know its possible to make the sctipt that will let me just right click an iso and mount it that way the problem is, some of the most basic things im not getting to work

[http://doc.gwos.org/index.php/Mount_ISO_script](http://doc.gwos.org/index.php/Mount_ISO_script)
ive tried what this has said but i dont know how to save under ~/.gnome2/nautilus-scripts/ or what it should be saved as or how (it wont let me do anything in root dir), nobody seems to explain that i guess its just common knoledge unless your new to linux like myself 
also ive tried some of the scripts out there and it always leaves it as a
<
and then doesnt do anything
please if someone could help me learn how to do this i would be gratefull
-HawaiinShirts4Life

---

### Post by po0f on 2006-12-17
HawaiinShirts4Life,

Open up Gedit (Applications->Accessories->Text Editor).  Copy and paste the script you want to use into a new file.  Click on Save.  When it asks for the filename, navigate to your home folder and then click on "Browse for other folders".  Right click in the filelist box and choose Show Hidden Files.  ".gnome2" should be one of the folders now revealed.  Double click on it.  If there isn't a "nautilus-scripts" folder in .gnome2, create it.  Now, save your script.  If you want pictures, post back.

Also, make sure you have [nautilus-actions](http://packages.ubuntu.com/edgy/gnome/nautilus-actions) installed.

---

### Post by neilrizo on 2007-02-14
> **po0f said:**
> HawaiinShirts4Life,

Open up Gedit (Applications->Accessories->Text Editor).  Copy and paste the script you want to use into a new file.  Click on Save.  When it asks for the filename, navigate to your home folder and then click on "Browse for other folders".  Right click in the filelist box and choose Show Hidden Files.  ".gnome2" should be one of the folders now revealed.  Double click on it.  If there isn't a "nautilus-scripts" folder in .gnome2, create it.  Now, save your script.  If you want pictures, post back.

Also, make sure you have [nautilus-actions](http://packages.ubuntu.com/edgy/gnome/nautilus-actions) installed.

Hi! I did everything you said but the "scripts -> mount" option isn't there when I right-click the ISO file.

Any idea why?

---

### Post by dyceman on 2007-08-26
You probably still need to make the script files executable.

[LIST=1]
[*]right click the file and go into Properties
[*]click the Permissions tab
[*]enable the box next to Execute
[/LIST]

---

