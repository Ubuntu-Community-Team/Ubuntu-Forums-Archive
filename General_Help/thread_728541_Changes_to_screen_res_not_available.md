---
title: "Changes to screen res not available"
date: 2008-03-18
forum: General Help
---

### Post by hgiahjd on 2008-03-18
[I]The X Server does not support the XRandR extension. Runtime resolution
changes to the display size are not available[/I].
My recent experience (Ubuntu 7.10) of not being able to change screen res from 
*System/Preferences/Screen Resolution* was imho because I had chosen a screen res not supported by my video card. I have read a few forums and the type of card and type of monitor and the version of LINUX does not seem to matter

Resolution - boot into linux in  safe mode
Startx at the prompt
Now you should be able to access via *System/Administration/Screen and Graphics* an new window title "Screen and Graphics Preferences"
In Model drop down the list and choose the "Detect" button and I unchecked "Widescreen Monitor"   OK out and all should be resolved -- at least my problem was.

Good Luck
David

---

