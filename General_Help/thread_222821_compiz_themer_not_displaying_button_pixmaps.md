---
title: "compiz themer not displaying button pixmaps"
date: 2006-07-25
forum: General Help
---

### Post by tedwick on 2006-07-25
hey. just installed the new compiz themer and the requisite packages, and it's running. one small problem: the close, min, and max buttons that should be in the top right corner of windows are not being drawn. in the themer, under edit, i can see that the .png's are there that need to be, but they simply aren't being rendered. i'm not really sure on where to even start diagnosing the problem (i'm kinda new to the whole linux thing, and compiz/xgl seems to be tricky to begin with). any ideas on what could be the problem, or how to fix it? the compiz themes look slick, and i don't want to go back to metacity(?)

---

### Post by fragmented_user on 2006-07-25
There seems to be a bug where compiz themer will not automatically assign the pixmaps included in some themes. You need to do this manually. 

1 check what the name of your theme is and write it down.
2 open compiz themer and click on your theme.
3 click the arrow next to Edit, all the way in the bottom left-hand corner
4 Select the tab labeled "Button Pixmaps" 
5 Select the file-selector button next to "Close".
6 Navigate to /usr/share/compiz/themes
7 Select the file that includes both the name of your theme and the word "close" 
in example: if my Theme name is "Vista-Linux" and the Button action is "close" then the file name in most cases will be "Vista-Linux.close.png"

Repeat step 7 for "Restore","Help","Minimize" and "Maximize" if you have pixmaps for "Shade" and "Menu" that's good to, but most themes I've seen don't. 

8 To Save your theme do the following.
a)select the "Theme" tab on top,
b)enter a name for your theme. 
c)press the save button.

Your theme should now include pixmaps.

To Export your theme complete steps 8a - 8b, then press the export button.

---

### Post by tedwick on 2006-07-25
thanks. exporting the theme and reimporting worked well after manually selecting the buttons.

---

