---
title: "Put a graphic watermark on the console (TTY)"
date: 2008-05-22
forum: General Help
---

### Post by wootah on 2008-05-22
This is slightly an odd question, but how does one configure their terminal to have a graphic on it (much like a watermark). I've seen this done with Suse consoles displaying a penguin in the top left hand corner and along with another distribution (can't recall which) that had the picture span the entire background of console.

This is not inside a DE using a terminal (such as konsole), but on a TTY such as CTRL-ALT-F1.

Thanks for any insights! :popcorn:

---

### Post by krauser530 on 2008-11-17
I've been looking to do this too. Haven't had any luck finding a solution though.

---

### Post by krauser530 on 2008-11-17
here's an example of somewhere ive seen this before 
[IMG]http://www.paulspoerry.com/wp-content/uploads/remote-exploit.org/images/screens/terminal_small.jpg[/IMG]

---

### Post by bodhi.zazen on 2008-11-17
You need to look at framebuffer

[http://docs.blackfin.uclinux.org/doku.php?id=the_framebuffer_console](http://docs.blackfin.uclinux.org/doku.php?id=the_framebuffer_console)

Or SVGAib

[http://linux.about.com/od/gmr_howto/a/hwtgmr04t11.htm](http://linux.about.com/od/gmr_howto/a/hwtgmr04t11.htm)

[http://db.glug-bom.org/wiki/index.php/Trivial_Graphics_Programming_with_GCC_and_Svgalib](http://db.glug-bom.org/wiki/index.php/Trivial_Graphics_Programming_with_GCC_and_Svgalib)

---

### Post by krauser530 on 2008-11-18
those websites were helpful in explaining the fb and svga but they didn't shed any light on this particular problem. After enabling the framebuffer how would one introduce the background image? And on a side note in a default ubuntu install is the fb enabled or will i need to do some kernel compiling? Is there a way to check this?

---

