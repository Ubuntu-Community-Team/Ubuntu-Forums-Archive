---
title: "learning sane from xsane"
date: 2008-04-17
forum: General Help
---

### Post by spipe on 2008-04-17
I've been using xsane with some good success on a new Epson 4490 scanner and would like to automate some of the same work unattended calling scanimage from scripts.

As I understand it the 4490 is not directly supported, but both xsane and scanimage do work on it after I installed iscan from the Epson japan website.

What I'm finding is that scanimage's available command line options don't help me duplicate some of the image adjustments that xsane allows. Specifically, when scanning black and white negatives using the transparency unit, xsane presents a single gamma adjustment slider (as opposed to the three, RGB, when in color mode), and it works properly.  But working from the command line, there is no available gamma command (it's mentioned in the manpage but not recognized), just separate RGB ones that don't behave nicely in gray mode (touching any of them simply washes out the scan).

Also,'--film-type="Negative Film"', although it is recognized without an error, seems not to work in scanimage; scans from negatives always come out looking like negatives, and what I'm doing for now is following the scanimage call with one to "mogrify -negate foo.pnm".

So two questions from anyone who might know:

1. Is iscan-based scanimage on Epsons different somehow than the canned scan-epson backend, needing different parameters documented elsewhere or something like that?  (I don't know if the question makes a lot of sense, since iscan's role here isn't clear to me.)

2., More to the point, is there a way to make xsane show what it is saying to the backend?  That way maybe I could compare those commands after making the adjustments in the GUI, and suddenly understand. :)

---

### Post by geraldm on 2008-04-17
See the manpage for the sane backend that you are using -- sane-epson ?  If you use scanimage, set  the environment variable for debugging SANE_DEBUG_EPSON=128 as stated in the manpage before issuing the command.

A graphical front-end as xsane should display a choice for the options that a backend offers.
the front-end communicates with the backend to detect what options are supported.

Gerald

---

