---
title: "Workspaces problems..."
date: 2007-12-30
forum: General Help
---

### Post by Moonfrost on 2007-12-30
Well, I have 4 workspaces open and the only one that actually "works" is number 1...what I mean by this is that when I switch to say, workspace 2 I only get a black screen because it seems that my desktop background doesn't transfer to that workspace (it should as far as I know since I use LInux), also when I open a menu or something when it's gone it still leaves like a screenshot of it frozen on the screen...if I move a windows from side to side the same thing happens, I see pieces of the window everywhere if you know what I mean...I tried this with Beryl and Compiz turned off and still the same thing. With Beryl when I rotate the cube (I have a Skydrome background now but didn't have that before and still had the same issue) the other workspaces are transparent take the the cube's background instead of taking whatever background I have on the main workspace...I'm using Ubuntu Ultimate edition 1.6 by the way but always had this issue....I tried this with OpenSUSE 10.3 but that problem wasn't there...

---

### Post by Sef on 2007-12-30
I would check Ultimate Ubuntu's website and see of others have had this problem and what their solution(s) are.

---

### Post by cmost on 2007-12-30
It seems as though you've screwed something up.  Run the following in a gnome-terminal:

gconftool-2 --type int --set /apps/metacity/general/num_workspaces 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

See if that doesn't fix it.

---

### Post by Moonfrost on 2007-12-31
> **cmost said:**
> It seems as though you've screwed something up.  Run the following in a gnome-terminal:

gconftool-2 --type int --set /apps/metacity/general/num_workspaces 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

See if that doesn't fix it.

No, not at all...besides it's the second time I install Ubuntu Ultimate 1.6 and the same thing used to happen but only with Beryl and not Compiz Fusion...

---

### Post by gyffes on 2007-12-31
I have no cool terminal-based debugging commands for you to try, but might this be a lack of RAM/video RAM problem? 

If you turn off funky supergraphics, are you able to switch workspaces? Wait -- you said it works alright in CompizFusion? In which case, it's not really a 'spaces' problem, it's a Beryl/screen-redraw problem, no?

---

### Post by Moonfrost on 2007-12-31
> **gyffes said:**
> I have no cool terminal-based debugging commands for you to try, but might this be a lack of RAM/video RAM problem? 

If you turn off funky supergraphics, are you able to switch workspaces? Wait -- you said it works alright in CompizFusion? In which case, it's not really a 'spaces' problem, it's a Beryl/screen-redraw problem, no?

Probably, I'm not sure but if I was running out of ram/video ram bery and everything else would be incredibly slow...but on the contrary, everything is smooth as butter, I can have more than 5 windows open while rotating the cube and my computer doesn't even slow down at all...I don't know, I'll try uninstalling beryl and reinstalling it and see what happens...

---

### Post by chinsubs on 2008-01-23
Switching off and on the compiz desktop effects seem to have resolved the problem. Only the window previews are not shown when you are on another workspace.

I got my problem solved by the above solution.
It was in the linux mint forum.

---

