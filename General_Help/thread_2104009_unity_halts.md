---
title: "unity halts"
date: 2013-01-11
forum: General Help
---

### Post by brusegadi on 2013-01-11
Hello, 

When I open GVIM, it opens a maximized window on the lower left desktop (when the active desktop is the upper left desktop.)  If I attempt to resize this window using the 'circle' button on the upper right corner of the window, my machine comes to a halt.  Strangely, this only happens with GVIM.  Any ideas?  I have an nvidia card and I am using 12.04.  I installed ccsm and activated wobbly windows but I disabled them to try to fix this to no success.  The issue disappears if I used unity2d, but I am certain my machine can handle unity3d per  

```
 /usr/lib/nux/unity_support_test -p    
```Thanks!

---

### Post by brusegadi on 2013-01-12
I figured this out.  Removing:

```
if has("gui_running")
   set lines=999 columns=999
endif
```from the vimrc file fixes the problem.  Now my vim sessions start with a small window, anyone know what to add so that its maximized and it does not break unity?  Thanks!

---

