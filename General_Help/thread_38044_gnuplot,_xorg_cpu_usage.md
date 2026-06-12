---
title: "gnuplot, xorg cpu usage"
date: 2005-05-29
forum: General Help
---

### Post by John Lapeyre on 2005-05-29
When I use the x11 driver with gnuplot, the Xorg process takes most of the cpu time for at least several minutes. The percentage varies from 33% to 90% depending on the size of the x11 window. The amount or kind of data being plotted has no effect. Gnuplot renders the plots quickly and takes no cpu time afterward. But as long as the x11 window is open, Xorg takes a lot of cpu time. Nothing is being moved or resized; no  plotting computation is being done.  I am running amd64. The problem occurs both with 64 bit gnuplot as well as  the 32 bit version run from a chroot environment. If I click the x11 window away, cpu usage stops until I make a new plot. If I run gnuplot on the ubuntu amd64 platform and display remotely on another machine (stock debian i386 unstable), there is  no problem on either machine.

I did not post this on an amd64 forum because its not clear that it is specific to this platform. If I knew a simple way to try to xfree86 packages I would try that, but I don't see and recipes for switching. I tried the free and binary only ati drivers with no difference observed. I am running a custom 2.6.11 kernel. No other app shows this problem as far as I know.
Thanks

---

### Post by akellehe on 2007-06-20
Hey, I'm sort of new to ubuntu but I've managed to install gnuplot and have it working.  There is a problem...  Whenever i give it a plot command it plots in the terminal using asteriks and + signs and - signs and actually DRAWS a plot with them.  I would kind of rather have a graphical plot outside the terminal window.  

I think the root of my problem is:  my "terminal type is set to dumb" as it says when I run the gnuplot command.  How do I set the terminal type to x11?

---

### Post by tgalati4 on 2007-06-20
Inside gnuplot:

>set term x11

---

