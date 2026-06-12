---
title: "Printer configuration being overridden"
date: 2015-03-19
forum: General Help
---

### Post by steve197 on 2015-03-19
I have created two printers on my system (Ubuntu 14.04). They point to the same physical machine.
One of the printers is set to print in Color, the other is set to print Black&White (grey scale).
On installation I set the configurations and the Default Options in CUPS accordingly.
However, when I tried to print, neither of the printers were using the defaults I had supplied (eg I set single-sided prints as the default on installation, whereas double-sided printing was selected when I actually tried to print).
Furthermore, the settings for Color and Grey Scale were overridden according to the previous print job done (in the case of the first post-installation print it took the most recent installed printer's settings).
In point of fact, none of the settings (eg page size, color, etc) are populated from the defaults, but inherit the previous print job's selection.

Also note: I had the same problem in Ubuntu 10.04 and could only solve it by running Windows with VirtualBox.

How can I get CUPS to honor the default values (per printer) every time I print?

Thanks in advance.

---

### Post by steve197 on 2015-04-03
Perhaps I need to elaborate.

I do a lot of small printing jobs, mostly A4 monochrome, but A3, color and duplex jobs are also common enough.
In order to be efficient as a one-man operation, I had set up Windows XP in a VirtualBox on my Ubuntu 10.04 desktop. One printer driver defaults to color (A4 non-duplex) and another printer driver defaults to monochrome (A4 non-duplex). This makes me efficient as I only need to change settings for A3, duplex and special paper prints.

Now I have upgraded to Ubuntu 14.04.
I had hoped to get rid of the scourge of Windows.
But when I set up two separate printer drivers THEY DO NOT respect their default values. In other words, whatever options I set on the previous print are still set for the next print job.
How is it that Windows XP (a 15 year old distro no less) can get this right out of the box, while a brand spanking new Linux distro doesn't?
Do I have to jump through extra hoops to get Linux to respect the defaults? If so, what?

I have googled this to the best of my ability, but to no avail.

Thank you.

---

