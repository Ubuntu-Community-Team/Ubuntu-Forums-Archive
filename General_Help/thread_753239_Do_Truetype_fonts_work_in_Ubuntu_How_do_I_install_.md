---
title: "Do Truetype fonts work in Ubuntu? How do I install fonts?"
date: 2008-04-12
forum: General Help
---

### Post by Redrazor39 on 2008-04-12
I came across this site
[www.fontstruct.fontshop.com](www.fontstruct.fontshop.com)

where I can make custom fonts. This sounded pretty cool, but it says you download them as truetype fonts that work in any mac or windows environment. Will these work in Ubuntu? Also, how do I install fonts? I need to know how I can make them work in OpenOffice, Font customization, etc.

Thank you for any help.

---

### Post by KeyserSoze93 on 2008-04-12
Put the .ttf files in a folder in your home folder called .fonts (hidden folder, starts with a dot) and they should appear in the font list...

---

### Post by conscious on 2008-04-12
Yes, ttf fonts do work. There's another method (found with [a quick google search]("http://www.google.ru/search?q=install+fonts+in+linux")):

[http://www.linuxforums.org/forum/installation/38154-how-install-fonts.html](http://www.linuxforums.org/forum/installation/38154-how-install-fonts.html)

---

### Post by fragos on 2008-04-12
> **KeyserSoze93 said:**
> Put the .ttf files in a folder in your home folder called .fonts (hidden folder, starts with a dot) and they should appear in the font list...

You'll also need to run "sudo fc-cache -fv" in a terminal window so that applications like OpenOffice can see thw fonts and use them. Chances are the fonts you want are the common Microsoft ones. Those can be easily added by installing the package msttcorefonts. It's included in the Ubuntu repositories.

---

### Post by Redrazor39 on 2008-04-18
What does that last command do? I want to be able to see them in OOo

---

### Post by fragos on 2008-04-19
> **Redrazor39 said:**
> What does that last command do? I want to be able to see them in OOo

Fonts are stored in a number of different folders. The command creates links to all the fonts in a single place which applications like OpenOffice use to access fonts.

---

### Post by Redrazor39 on 2008-04-25
There is no .fonts folder in my home folder (yes, I ctrl-H'd)

just .fontconfg or something which is a bunch of numbers.

---

### Post by SunnyRabbiera on 2008-04-25
yeh well the thing is there seems to be no more fonts:/// directory which used to be the easiest way to install fonts in gnome...
why is it gone???
I dont know

---

### Post by Redrazor39 on 2008-04-25
So how do you install otf and ttf fonts now?

---

### Post by fragos on 2008-04-25
Create the .fonts folder in your home folder. Run "sudo fc-cache -fv" and the fonts will be located and included in the font list used by applications.

---

### Post by MentalNotes on 2008-04-26
I think the fonts:/// option in Nautilus was one of the casualties from moving to GVFS in Hardy unfortunately.

Hopefully when GVFS has had a little bit more work done to it this feature will show up again.

---

### Post by Redrazor39 on 2008-04-29
Wait, what happened in hardy?

---

### Post by beadtexas on 2008-05-08
> **KeyserSoze93 said:**
> Put the .ttf files in a folder in your home folder called .fonts (hidden folder, starts with a dot) and they should appear in the font list...

I can't copy the .ttf files. 

1.  I can't find home/.fonts when showing the hidden files. did that change with 8.04? 

2.  Also found nots to put them in usr/share/fonts/truetype folder.  When I drag and drop, I get "permission denied" error message. 

Help please! thx

---

### Post by inportb on 2008-05-08
can't you create a ~/.fonts directory?

---

### Post by fragos on 2008-05-09
.fonts directory will need to be created. It doesn't go in /home, it goes in a subdirectory labeled with your user name. My user name is "fragos" and I put my .fonts file into /home/fragos/. You won't have permission problems copying ttf files to that directory because you are the owner. There are other places where fonts are stored but they all belong to root and are as you found out the process to copy into them is more involved. After you have placed ttf files in ~/.fonts they won't be available to applications until you open a terminal window and run "sudo fc-cache -fv"

---

