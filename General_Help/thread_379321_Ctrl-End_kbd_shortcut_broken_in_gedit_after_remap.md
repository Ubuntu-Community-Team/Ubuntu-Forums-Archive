---
title: "Ctrl-End kbd shortcut broken in gedit after remap"
date: 2007-03-08
forum: General Help
---

### Post by zeus77 on 2007-03-08
My Lenovo laptop keyboard stupidly doesn't have Home/End keys (unless you press the awkward Fn key first), so I used xmodmap to redefine the rarely used PrtSc and Pause keys to be Home and End.  The newly mapped Home/End keys work like a charm in all applications, except for one problem:

The Ctrl-End shortcut (i.e. go to the end of the document) does not work in gedit.  This keyboard shortcut works fine, for example, in OpenOffice... and the Ctrl-Home shortcut (i.e. go to beginning of document) works fine in gedit.  Furthermore, 'xev' correctly reports that Ctrl-End is being pressed. 

Any ideas what could cause this bizarre behavior that only appears in gedit?

---

