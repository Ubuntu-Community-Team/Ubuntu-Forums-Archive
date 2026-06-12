---
title: "xemacs won't apply dark background at startup"
date: 2008-05-29
forum: General Help
---

### Post by oaul on 2008-05-29
I use white font on black background for xemacs, so i use the dark background mode:

Frame Background Mode: * [Value Menu] dark 
   [State]: this option has been set and saved.
The brightness of the background. *
Set this to the symbol dark if your background color is dark, light if
your background is light, or nil (default) if you want Emacs to
examine the brightness for you.

to make syntax highlighting use readable colors.  So I put this into my custom.el file. 
But when I start emacs and open a file, it uses syntax highlighting for LIGHT backgrounds.  Then, when I open a new window with C-x 5 2 it uses syntax highlighting for DARK backgrounds!  

It seems like I have to open a new window to get this setting to apply...which makes no flippin' sense.  If I set the frame background mode to light it stays light, which is correct.  If I use automatic, I have to open a new window for the dark mode to apply, which is just stupid. 

Can anyone tell me what I'm doing wrong, or duplicate this behavior? 

(btw, I'm using debian sid, but the xemacs has no relevant bug reports)

---

### Post by oaul on 2008-05-29
***bump***

---

