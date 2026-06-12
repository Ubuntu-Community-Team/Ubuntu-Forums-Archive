---
title: "Convert .png to .svg?"
date: 2007-10-04
forum: General Help
---

### Post by Ub1476 on 2007-10-04
Hi, I'm just adding a new app to the applications menu, but it looks like the icon I need must be in .svg format. The icon I have is in .png format. So, I tried to use inkscape to save it as a .svg file, but it doesn't work very well, seeing there's no image anymore then.. Is there any way I can use a .png image as an icon? I'll upload the icon if you want try.

It's for the musicplayer Songbird if you are curious.:popcorn:

---

### Post by rsambuca on 2007-10-04
You will have to trace the png image to paths, which can then be saved as an svg file.  To do this in inkscape, you would have to import the image, then select Path -> Trace Bitmap.  Fiddle with the settings until you get what you want.

I still think you should be able to use a png in the menu, though.

---

### Post by Lord Illidan on 2007-10-04
You should be able to use a png in the menu. Perhaps you are using a wrong approach?

---

### Post by Ub1476 on 2007-10-04
I'm just clicking "edit menus", new item and then on the picture to the left. Is it possible to do it another way? If not I'll try the trace stuff.

---

### Post by jfluhmann on 2008-02-14
To use your PNG image, right-click the launcher (if it's already there) and choose _P_roperties.  Click on the icon button, which brings up the 'Browse icons'.  Type the path of your PNG image in the drop-down box.  This should then show your icon in the browse area.

---

### Post by wireddad on 2008-02-23
Ub1476, did you get this to work with png?

---

### Post by odysseusjak on 2008-02-25
What I have done is install Inkscape and then open a *.png with that.  Once it opens select File > Save as... and then CHANGE the extension to PLAIN SVG down in the filename extension section (close to the save button).  Then select save.  I would recommending removing the .png from the file first (no reason, just looks).  That works for me.  I have done this with an icon set that I like and it works well for that.

---

### Post by wireddad on 2008-02-25
> **odysseusjak said:**
> What I have done is install Inkscape and then open a *.png with that.  Once it opens select File > Save as... and then CHANGE the extension to PLAIN SVG down in the filename extension section (close to the save button).  Then select save.  I would recommending removing the .png from the file first (no reason, just looks).  That works for me.  I have done this with an icon set that I like and it works well for that.

Will have to try it.  Thanks.

---

### Post by dezine on 2008-02-28
All I had to do, to get the png to work with the menu editor, is manually type the location rather then browse. It shows up just fine for me.

---

### Post by odysseusjak on 2008-06-03
I'm not sure if this is still an issue, but I have found that the way I described above doesn't work.  I have since 'discovered' how to do it.

First, open a Terminal and paste

> sudo apt-get install python-lxml

Press Enter and supply your password.

Once that's finished, open up the png in Inkscape.  From the 'Effects' menu, select 'Images' > 'Imbed all images'

A pop up will ask what you want to do, click 'Apply'.

Now, you can select 'Save As...' from the file menu and save your images as a SVG.

---

### Post by Dragunov on 2008-06-10
No need to save it to other format with any programs. Just change > button_headphones.png to button_headphones.svg and that's it.

---

### Post by all2ez on 2008-06-23
> **odysseusjak said:**
> 
Once that's finished, open up the png in Inkscape.  From the 'Effects' menu, select 'Images' > 'Imbed all images'

A pop up will ask what you want to do, click 'Apply'.

Now, you can select 'Save As...' from the file menu and save your images as a SVG.

Thanks, that worked for me! (although i didn't have to install the python thing either it is already installed or not really needed)

---

