---
title: "redirect output fo (gnome) clipboard on command line?"
date: 2007-04-19
forum: General Help
---

### Post by pixelterra on 2007-04-19
I've looked all over  for this answer, but no luck. 

I want to redirect the output of a command to the gnome clipboard, similar to how you redirect to a file:

command > file

I want....

command > clipboard

What is the syntax for this if it's possible? Anyone know?

---

### Post by khedron on 2007-04-19
Google **xclip**. Looks like it could do what you want it to do.

---

### Post by khedron on 2007-04-19
Ok, from what I can see it's pretty easy:

By default, **xclip** uses the "primary" clipboard, which is what you have copied with your mouse. To get it to use the manual copy clipboard, use **xclip -sel clip**
 instead.

You can pipe into the clipboard directly, for example:
```
$ cat /etc/X11/xorg.conf | xclip
$ fglrxinfo | xclip -sel clip
```To get stuff out of the clipboard, use the -o option. E.g.```
$ xclip -o | grep http
$ xclip -o -sel clip > ~/clipboard
```Edit: instructions at [http://people.debian.org/~kims/xclip/]("http://people.debian.org/%7Ekims/xclip/")  
Get the package with **sudo aptitude install xclip**

---

### Post by zeekay on 2007-04-19
Interesting, that's really useful. Thanks for the tip. :)

---

### Post by catherinedevlin on 2008-05-16
> **khedron said:**
> 
By default, **xclip** uses the "primary" clipboard, which is what you have copied with your mouse. To get it to use the manual copy clipboard, use **xclip -sel clip**
 instead.

THANK YOU THANK YOU THANK YOU!  That's the part I didn't get... I'd found a million places on the web that told me to use xclip, but I couldn't tell why my copied text was going to some mysterious "other" box, leaving my mouse-inserts unchanged.

---

### Post by victorbrca on 2008-07-17
Anyone knows if xclip will work with Glipper?

---

