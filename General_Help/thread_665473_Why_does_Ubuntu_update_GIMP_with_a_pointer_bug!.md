---
title: "Why does Ubuntu update GIMP with a pointer bug?!"
date: 2008-01-12
forum: General Help
---

### Post by mamadu bwana on 2008-01-12
Ok. now I am getting really frustrated with Ubuntu.

In October of 2007 I upgraded from Feisty Fawn to Gutsy Gibbon and immediately found a bug with GIMP. First, the at bootup the splashscreen identified the version of GIMP only as "release candidate". I checked - turns out that the version is GIMP 2.4.0-rc3. More annoyingly, whenever I moved the cursor over an image I got green paint painted over the image (regardless of the brush or tool I selected). Turns out that this was a known bug: bug #158270 and a duplicate of another known bug: bug #156556. Bottom line: this problem is related to the ati video drivers (that is exactly what I have: VGA controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA]) Subsystem: ATI Technologies Inc Radeon 7000/Radeon VE).

Rather than remove the package and manually reinstall an earlier version of GIMP, I decided to wait until the bug would be fixed through the regular updates. I figured that GIMP+ATI was such a common thing that surely it would be fixed soon.

Now, four months later, I just downloaded an update for GIMP and the bug is still there. No ATI driver updates were offered. Nor I have been unable to find a workaround.

So my questions are:

1) why has Ubuntu not fixed this rather big double-bug?
2) how long might it take until a fix is finally available via the updates system
3) has anyone found a way to fix this in the meantime?

Thanks!

Mamadu

---

### Post by amo-ej1 on 2008-01-12
Well is the bug known ? Have you checked that it is already reported ? Then you can easily follow the progress there. If it isn't reported then you should have reported it and you can follow the status there again.

In essence is there nothing wrong with using an -rc version. It will contain bugs, but the stable version will also contains bugs.

---

### Post by chrisccoulson on 2008-01-12
The OP already references two bug reports on Launchpad.

BTW, have you tried with the version of Gimp on [www.getdeb.net]("www.getdeb.net")? Someone posted a comment on the bug report that Gimp 2.4.1 changes the drawing mode to get around this. GetDeb has 2.4.2 for Gutsy.

Also, bear in mind, this is not a bug in Gimp - it's a bug in the ATI driver

---

### Post by lgambett on 2008-01-12
GIMP release was updated today (2.4.2, no more candidate release) in the Ubuntu repos.

---

### Post by geirha on 2008-01-12
I checked the bugs you mentioned at launchpad. Apparently the bug is not in gimp, but in the radeon driver. The radeon driver is very recent, it was made because amd decided to release the specs for certain ATI chip sets, so the open source community could make drivers themselves. The driver is still very new, so bugs are to be expected. Your best bet for the time being is to try the workarounds mentioned in [#156556]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/156556"), or use the proprietary ATI driver (fglrx) until the radeon driver is fixed.

---

