---
title: "Ubuntu 7.10 resolution issues with HP dv6000"
date: 2008-01-25
forum: General Help
---

### Post by minulescu on 2008-01-25
I know this is a somewhat common issue, bit I have been searching for more than an hour and havent found a solution.

My screens resolution is 1280x800, but in Ubuntu 7.10 i only have option for 1024x768 or lower.

I used to have 7.04 where my resolution was 1280x800... I don't remember what I did to fix it! :(.

Here's my xorg.conf:

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
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
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection


It's kind of funny that all of those slots say 1280x800 but I don't even have that option.

Thanks in advance!!

---

### Post by minulescu on 2008-01-25
bump

---

### Post by newone757 on 2008-03-07
had the same problem when i installed ubuntu on my laptop today,


on the screen and resolution window (under system>admin) look to the left bottom and check the box that says widescreen and that should fix your problems

---

