---
title: "xmgrace in edgy eft"
date: 2007-01-09
forum: General Help
---

### Post by Extr3me on 2007-01-09
Hello all,

I have been using Grace since I first installed Ubuntu last July and have had no problems with the package whatsoever. I prefer to use Grace 5.1.20 over the newer 5.99.1 (Grace6 in repository list) as it the same version I used to use on my old Sun workstation.

Things had been going splendidly and I was enjoying using 64-bit Edgy Eft on my new Dual Opteron workstation, thankfully retiring my SunBlade workstation to a fancy footstool under the desk.

Unfortunately in the update of the last couple of days, Grace seems to have broken and dumps the following message in the terminal:

ewan@pantani:~/Monte_Carlo_code/working_code/DATA$ xmgrace Plasmon_scattering_rate_abs.dat Plasmon_scattering_rate_emi.dat &
[2] 21226
ewan@pantani:~/Monte_Carlo_code/working_code/DATA$
Oops! Got SIGSYS

Please use "Help/Comments" to report the bug.
NB. This version of Grace was compiled with LessTif.
Make sure to read the FAQ carefully prior to
reporting the bug, ESPECIALLY is the problem might
be related to the graphical interface.

[2]- Aborted (core dumped) xmgrace Plasmon_scattering_rate_abs.dat Plasmon_scattering_rate_emi.dat
ewan@pantani:~/Monte_Carlo_code/working_code/DATA$

It bombs as soon as you try to open one of the drop-down menus, which is probably what it refers to as a bug related to the graphical interface.

Unfortunately, I never record what updates I have installed but I do remember there being a security update to glibc which may have caused this to occur. If anyone knows how to find out what updates have been installed and unroll them so I can get this program to work again in the meantime, please let me know.

Any suggestions or requests for more info are welcome...

---

### Post by Extr3me on 2007-01-09
You will all be pleased to know that I have found the solution which had already been solved by another one of our forum members at:

[http://www.ubuntuforums.org/showthread.php?t=295725&highlight=LessTif](http://www.ubuntuforums.org/showthread.php?t=295725&highlight=LessTif)

Should've seen this bug coming as I had noticed that the font looked pretty terrible in grace and emacs.  Turns out that the xorg.conf file in the ./etc/X11 folder is wrongly specifying the location of the folder containing the fonts.

That was a bit of luck, I use Grace regularly and would be quite stuffed without it!

Good Luck!

---

