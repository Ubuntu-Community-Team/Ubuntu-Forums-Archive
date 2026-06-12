---
title: "How to isolate particles using imagej?"
date: 2013-07-15
forum: General Help
---

### Post by KarinaFerreira on 2013-07-15
[COLOR=#000000][FONT=Verdana]I have established a macro to isolate and characterize some fat crystals. The macro is as follows: [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]_________________________ [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]open("C:\\Users\\Karina\\Desktop\\Pics for Karina\\10HCO 90CO 2000s-1 0-5mm gap 70C to 20C diluted 10X 2 no polarization 2.tif"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Set Scale...", "distance=96 known=100 pixel=1 unit=um global"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rename("original"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("8-bit"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Duplicate...", "title=main"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Find Edges"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Enhance Contrast...", "saturated=0 equalize"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]setThreshold(84, 255); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Convert to Mask"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]//Noise Removal [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Median...", "radius=3"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]//Filter out other noises [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Analyze Particles...", "size=85-Infinity pixel circularity=0.0-1.00 show=Masks"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Watershed"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Analyze Particles...", "size=85-Infinity pixel circularity=0.35-1.00 show=Masks display clear"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rename("particles"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]selectWindow("Mask of main"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]close(); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]selectWindow("particles"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Duplicate...", "title=particles-1"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Analyze Particles...", "size=85-Infinity pixel circularity=0.35-1.00 show=Ellipses display exclude clear"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]selectWindow("Drawing of particles-1"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Fill Holes"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Watershed"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]selectWindow("Drawing of particles-1"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Duplicate...", "title=[Drawing of particles-2]"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]//comparison [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Merge Channels...", "c1=[Drawing of particles-1] c2=[original]"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]selectWindow("Drawing of particles-2"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Make Binary"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Set Measurements...", "  fit redirect=None decimal=3"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]run("Analyze Particles...", "size=85-Infinity pixel circularity=0.35-1.00 show=Nothing display clear"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]___________________________________ [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]After running the macro you get this image: 
[/FONT][/COLOR][ATTACH=CONFIG]244761[/ATTACH]
[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]How could I isolate these particles (ellipses) from this image? In other words, I would like to isolate each particle and save them separately. 

ps: I just want to extract every single particle (ellipse) on its own. I don't want to maintain the particle in the same white image. I want to extract to a new one in order to save every particle in different images. 

Thank you, 

Karina.


[/FONT][/COLOR]

---

### Post by VanillaMozilla on 2013-07-15
Have you tried the ImageJ list?

---

### Post by KarinaFerreira on 2013-07-15
I was looking for it, but didn't find it!

---

### Post by oldos2er on 2013-07-15
> **KarinaFerreira said:**
> [COLOR=#000000][FONT=Verdana]I have established a macro to isolate and characterize some fat crystals. The macro is as follows: [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]_________________________ [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]open("C:\\Users\\Karina\\Desktop\\Pics for Karina\\10HCO 90CO 2000s-1 0-5mm gap 70C to 20C diluted 10X 2 no polarization 2.tif")[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

Are you running Ubuntu?

---

### Post by VanillaMozilla on 2013-07-16
> **KarinaFerreira said:**
> I was looking for it, but didn't find it!
Here it is.
[http://rsbweb.nih.gov/ij/list.html](http://rsbweb.nih.gov/ij/list.html)
You'll get much more info from them than from us.

---

### Post by KarinaFerreira on 2013-07-16
Thank you!

---

