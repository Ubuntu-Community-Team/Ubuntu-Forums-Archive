---
title: "Why do large PDFs take so long to load in Linux PDF viewers, but not in Foxit (Wine)?"
date: 2013-09-03
forum: General Help
---

### Post by blackbird34 on 2013-09-03
Hi everyone, 

I'm a student, i've been doing a master's thesis recently and so accumulated a lot of PDFs. Evince (the default under Ubuntu Unity or Cinnamon) can't really do much, so I hunted around, installed Foxit Reader 5 and 6 under Wine with Playonlinux (it did a perfect job! :D ) and then settled on Okular (the KDE viewer) because it had the benefit of being native, faster than Evince, had more features (annotations!) and was even very hackable: I even found out how to tweak an XML file ( ~/.kde/share/apps/okular/tools.xml ), and made myself a bunch of extra highlighters in lots of different colours :D ([link]("http://superuser.com/questions/584017/customise-okular-to-modify-highlight-tool-properties"))

BUT although it is still a lot faster than Evince, especially since I got myself some more RAM, Okular still struggled a lot on large, complex PDFs such as [this]("http://www.ratp.fr/informer/pdf/orienter/f_plan.php?nompdf=metro_geo&loc=secteur&fm=pdf") one (a detailed map of the paris metro system). So I switched back to Foxit (5 and 6 under Wine) to have a look, and lo and behold, it loaded in about 2 seconds instead of 20 or 30?!! 

Why is it like this? It's disappointing, really...

EDIT: [SumatraPDF]("http://blog.kowalczyk.info/software/sumatrapdf/free-pdf-reader.html") under Wine blows them all out of the water, even Foxit. It intrigues me.

---

### Post by mastablasta on 2013-09-03
Sumatra is Good. I wish they had one for linux. 

it's interesting since it's really fast and is opensource, yet no one ported it to linux yet.

---

### Post by blackbird34 on 2013-09-03
I found out [why]("http://code.google.com/p/sumatrapdf/wiki/WhyOnlyWindows") the author didn't...

> 
    People sometimes suggest that Sumatra should be available for some other operating system: Linux, Mac, Android etc. 
This won't happen. 
The first reason is that current developers don't know how to write software for those other platforms. 
Second  reason is that it would essentially mean writing the whole program from  scratch for a new platform. Sumatra is tightly integrated with and  optimized for Windows. Making a version for another operating system is  not a matter of making a few changes here and there but pretty much  writing everything from scratch i.e. redoing years of development that  went into Sumatra. 
SumatraPDF is an open-source project so anyone  is free to take our source code and use as much of it as they want to  create equivalent for some other operating system, but we're unlikely to  do it ourselves. 
  
  



---

### Post by vasa1 on 2013-09-03
> **blackbird34 said:**
> ...
 large, complex PDFs such as [this]("http://www.ratp.fr/informer/pdf/orienter/f_plan.php?nompdf=metro_geo&loc=secteur&fm=pdf") one (a detailed map of the paris metro system). So I switched back to Foxit (5 and 6 under Wine) to have a look, and lo and behold, it loaded in about 2 seconds instead of 20 or 30?!! 
....
Hi, just thought I'd mention that Google Chrome's built-in PDF Viewer does a relatively quick job of displaying the PDF. (Of course, it's only a viewer and doesn't have any facility for annotating/editing/highlighting, etc). The PDF Viewer in Firefox really struggled.

---

### Post by cmcanulty on 2013-09-03
I am running 12.04 classic and Okular opens a very large pdf in <1 sec but so does evince

---

### Post by sbnwl on 2013-09-03
[**@**]("http://ubuntuforums.org/member.php?u=1290768")[**[COLOR=#000000]blackbird34[/COLOR]**]("http://ubuntuforums.org/member.php?u=1290768")
The pdf you mentioned is a special. It probably contains a scalable graphic image. You can do one experiment:
Install  xournal from software center or synaptic. Then try to open the pdf in  xournal. It will initially take time, (but certainly less than evince)  then use the 'set zoom' button to set a zoom level of 400. Do the same  (nearly 400%) by opening in sumatra pdf reader also. Now drag the image  by holding the mouse button in both applications. You will notice that  sumatra pdf is rendering the image's area related to viewport in  on-the-fly manner, but xournal has already rendered the whole image (so  it took initially some time to zoom/render to 400%) and dragging is  really faster and smoother than sumatra.
Regarding evince, there is  some support in evince to filter out layered images stacked over one  another, which may be present in a given pdf file. May be due to which  the pdf file you provided is taking a long time to render in evince,  making evince eventually a failure in this case.

---

### Post by Impavidus on 2013-09-04
It really depends on the type of pdf. If it's mostly raster graphics, the file size is large, but the pdf reader can uncompress the data and send it linea recta to the graphics memory, whereafter the dedicated graphics hardware will map it to the frame buffer. If it's only raster graphics, like the Paris métro map, the information can be stored more efficiently leading to smaller files, but rendering becomes computationally far more intensive. Pdf readers can optise loading in different ways, like only rendering what's inside the viewport and clever clipping algorithms to not render things that will be covered by something else. As sbnwl noted, it loads faster but scrolls slower, in which case I prefer fast scrolling and slow loading. Another difference is that some pdf readers display the image progressively, that is, render all elements that the image comprises after another and show all intermediate results on screen. It may be somewhat slower, but give you nice feedback showing that something is happening and gives you some information before rendering is complete, so you can scroll to the right part of the image already, or decide you need a different zoom level.

Evince really struggles with that map, but gv, which needs a lot of time to render the map at high magnifications, remains responsive and gets the job always done.

---

