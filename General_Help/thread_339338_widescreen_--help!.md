---
title: "widescreen --help!"
date: 2007-01-15
forum: General Help
---

### Post by notepad on 2007-01-15
im using a dell inspiron 6400 with ubuntu 6.10 with kernel 2.6.17-10-generic. this machine has a 1280x800 widescreen but my display is 1024x768. if i go to system > preferences > screen resolution, my only option is 1024x768 even though my xorg.conf contains:

> Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection


etc. the depth goes up to 24 before the section ends.

how do i make the system use 1280x800 resolution?

---

### Post by allwin on 2007-01-15
> **notepad said:**
> im using a dell inspiron 6400 with ubuntu 6.10 with kernel 2.6.17-10-generic. this machine has a 1280x800 widescreen but my display is 1024x768. if i go to system > preferences > screen resolution, my only option is 1024x768 even though my xorg.conf contains:



etc. the depth goes up to 24 before the section ends.

how do i make the system use 1280x800 resolution?
I'm no expert, but for me what I did was like, got rid of everything else in the file referring to modes and depths EXCEPT the one that contained my chosen screen size and color depth!  Thus giving it ONLY the option to display at my chosen color depth and screen size.  I was even successful configuring mine for 1280x768 simply by keying it in when it wasn't there (I have a widescreen HDTV monitor).

X may not start for you after this, so make sure you make a copy of the existing conf file and are sure to know how to do a copy command from the Linux prompt in case X doesn't come up (sudo cp fileold filenew).  HTH

---

### Post by notepad on 2007-01-16
greetz flying out to ohio if thats where you are allwin. im at home now so ill give it a bash tomorrow when im back in the office and ill let you know how it goes.

---

