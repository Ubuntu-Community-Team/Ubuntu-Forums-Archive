---
title: "Application window bigger than screen size"
date: 2008-06-23
forum: General Help
---

### Post by mmasroorali on 2008-06-23
Dear All,
My screen resolution is set at 1024X768. This is fine with me which optimizes to my taste. However, a few applications like dvd::rip, Ksubtitle go beyond the lower boundary. So I miss some essential buttons or bars which are placed at the very bottom. 

I tried maximizing/minimizing the window without any avail. Even moving the panel to the right does not help. Setting resolutions higher solves the problem, but I do not like it.

Could you please tell how I can make the windows fit to the viewing area of my screen?

I am using hardy.

---

### Post by Forlong on 2008-06-24
I'm afraid there's not much you can do but filing a bugreport against those applications that depend on high resolutions.

You can grab those windows with [Alt]+[Left Mousebutton] to move them so you can access the lower parts, though.

---

### Post by 130s on 2011-02-07
I'm in the same situation having an issue with Document Properties on File Browser or some other programs.

Thanks Forlong. [Alt]+[Left Mousebutton] provides a work around so far (I've been forced to use the external monitor every time I face the problem).

Ubuntu 10.04 Netbook Edition

Isaac

---

### Post by Zill on 2011-02-07
> **mmasroorali said:**
> ...Could you please tell how I can make the windows fit to the viewing area of my screen?...
Normally you just resize an application window by "grabbing" a corner and dragging it in to make the window smaller, then moving the window to its desired location by dragging the title bar.

However, [Bug #160311]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311") identifies this as difficult with some Maverick themes.  It will hopefully be resolved in Natty :-)

---

### Post by mcduck on 2011-02-07
> **130s said:**
> I'm in the same situation having an issue with Document Properties on File Browser or some other programs.

Thanks Forlong. [Alt]+[Left Mousebutton] provides a work around so far (I've been forced to use the external monitor every time I face the problem).

Ubuntu 10.04 Netbook Edition

Isaac

Also, Alt+Middle button allows resizing a window from any point inside it.

Although the application itself may have a limit for the minimum size you can resize it into, (usually the limit would come from the simple fact that with the current font size & GTK theme the widgets in the application window simply require a certain amount of space)

---

