---
title: "Help me change my resolution on Kubuntu"
date: 2007-05-11
forum: General Help
---

### Post by StoneySS on 2007-05-11
I don't have the option to change the resolution to what i want. All i have is
640x480
800x600
1024x768
I have a 17'' screen, and i don't know what resolutions are there, but i would like to have a couple of options so i can choose among them.
I'm on 6.10 with KDE (laptop is a HP nx9420) and i've read up and i realized that it would help you allot if i paste my xrog.conf file so here it is: (it's just the part that i _think_ is important)
Please tell me if you need any more info.

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "VMWare Inc [VMware SVGA II] PCI Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


```

---

### Post by heimo on 2007-05-11
You need to add the other resolutions on the lines where you see also those "1024x768" "800x600" and so on. You also may need to change HorizSync and VertRefresh, but that depends on the model and type of your monitor. See this howto:
[HOWTO: Solving resolution/refresh rate problems in Xorg]("http://www.ubuntuforums.org/showthread.php?t=83973")

EDIT: I'd guess you could try to run it at 1280x1024 if it's a good quality 17" CRT, but that'd be too high resolution for me (everything gets tiny).

EDIT2: Oh, it's a laptop. I'd only use it at its native resolution. Check manufacturers website or your paper manual for specifications.

Specs here:
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-3329741-1839153.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-3329741-1839153.html)

It's probably 1440×900 or 1680×1050?
[http://en.wikipedia.org/wiki/WSXGA_Wide_XGA+](http://en.wikipedia.org/wiki/WSXGA_Wide_XGA+)

---

### Post by StoneySS on 2007-05-12
Thanks, i got it done :)
Thank you :>

---

