---
title: "Is there a Eye Dropper app for Ubuntu/Linux"
date: 2018-11-10
forum: General Help
---

### Post by sonyboyj on 2018-11-10
I want a tool that i can click on the changes the cursor to an eye dropper and then i can select a color and get the hex code for that color. Save me from opening the image in gimp and using its eyedropper to find the hex code.

---

### Post by Dennis N on 2018-11-10
Install **gpick**. reads hex code for color where cursor is (uses left pointer, not eye dropper). you can press space bar to add to colors. Or, there is a toggle button in lower right that gives you a cross cursor that reads the color code under the cross independent of the main window.

---

### Post by SeijiSensei on 2018-11-11
KDE's Kcolorpicker app is excellent for this, but you need to install some other packages to support it on a vanilla Ubuntu machine. They will be installed automatically if you use "sudo apt install kcolorpicker".

---

### Post by slickymaster on 2018-11-11
*Thread moved to **General Help**.*

---

### Post by sonyboyj on 2018-11-12
> **SeijiSensei said:**
> KDE's Kcolorpicker app is excellent for this, but you need to install some other packages to support it on a vanilla Ubuntu machine. They will be installed automatically if you use "sudo apt install kcolorpicker".

Says kcolorpicker can't be found.

---

### Post by sonyboyj on 2018-11-12
> **Dennis N said:**
> Install **gpick**. reads hex code for color where cursor is (uses left pointer, not eye dropper). you can press space bar to add to colors.

Thanks. :D

---

### Post by oldos2er on 2018-11-13
> **sonyboyj said:**
> Says kcolorpicker can't be found.

Try kcolorchooser instead.

---

### Post by SeijiSensei on 2018-11-13
> **oldos2er said:**
> Try kcolorchooser instead.

Sorry! My bad.

---

### Post by again? on 2018-11-13
For anyone interested and likes the simple gtk2 picker dialog, you can install pycolorsel using git
(or download the zip file from [https://github.com/Eclipse000/pycolorsel](https://github.com/Eclipse000/pycolorsel))
```
git clone https://github.com/Eclipse000/pycolorsel.git
```
 or 
using pip...
```
pip install --user pycolorsel
```
Requires the package **python-gtk2**.
```
sudo apt install python-gtk2
```

Then run with ...
```
python [COLOR="#696969"]/path/to/pycolorsel.py[/COLOR]
```

---

