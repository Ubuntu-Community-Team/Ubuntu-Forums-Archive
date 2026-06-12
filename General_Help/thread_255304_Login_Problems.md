---
title: "Login Problems"
date: 2006-09-11
forum: General Help
---

### Post by madsurfer on 2006-09-11
Hi 
Have just installed Ubuntu 6 which seems great, all worked and my login to gnome was fine. As I have a better monitor I thought I would change the screen resolution. I used ctrl alt F1 to switch X11 off and then used sudo dpkg -reconfigure -phigh xserver-xorg to increase the res (selected a res that wasn't in the gnome display configuration). Every thing was OK and I went back into X11/gnome. The res was OK but I could not login on my username (but others I could). I stopped X/gnome and went back to a cmd line. I could login no prob. So my problem is that if you change the res at the cmd line you can no longer login in the graphical mode!!
This has caused me loads of time re-installing to get my login back please help because I really would like to work in a higher screen res. Also does anyone know how to change xconf.org to change the screen refresh rate from 60 hz (standard) without hand editing the xorg.conf file with vi!?

Thanks
Adrian

---

### Post by David Corrales on 2006-09-11
Just a tip, use **nano** to edit files. MUCH more user friendly :)

---

### Post by BerkeleyDude on 2006-09-11
Well... I'd say, you should edit /etc/X11/xorg.conf yourself, and not rely on any programs.

For the refresh rate, find a section like this:
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

```
And change VertRefresh. It can be just a number, if you know your monitor supports it - e.g., 75.

For resolution, find the "Screen" section. It will contain a bunch of subsections like this:
```

        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection

```
You probably care only about depth 24 (unless your default is different - specified at the beginning of "Screen"). You can simply add more resolutions. E.g.:
```

        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768"
        EndSubSection

```

---

### Post by madsurfer on 2006-09-11
Thanks for replying so fast, I will edit the xorg.conf by hand next time, does anyone know how to get the original user password back? Anyway using the tool to change to change the resolution has also mucked up my keyboard making it USA type. Guess I will have to re-install again and edit the xorg.conf file by hand!

---

