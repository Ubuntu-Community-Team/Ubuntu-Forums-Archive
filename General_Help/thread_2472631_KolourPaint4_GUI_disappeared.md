---
title: "KolourPaint4 GUI disappeared?"
date: 2022-03-06
forum: General Help
---

### Post by wyattwhiteeagle on 2022-03-06
Something ate my KolourPaint4 GUI.
dpkg says it is still installed...
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                       Version                               Architecture Description
+++-==========================================-=====================================-============-===============================================================================
.
.
...
ii  kolourpaint                                4:19.12.3-0ubuntu1                    amd64        simple image editor and drawing application
ii  kolourpaint4                               4:19.12.3-0ubuntu1                    all          transitional package for kolourpaint



```

When I try to open an image using KolourPaint...KolourPaint isn't in the list.
I then look in my installed packages...you know...the 9 dots at the corner...KolourPaint isn't there...
So, I type kolourpaint at the top...it returns "no results"

Purging and re-installing didn't make any difference.

What is goin on here?

---

### Post by Impavidus on 2022-03-07
This suggests that the .desktop file for kolourpaint cannot be found, isn't readable, is damaged or not there at all. Purging and reinstalling kolourpaint would normally restore the .desktop file, as it is in the main kolourpaint package (at /usr/share/applications/org.kde.kolourpaint.desktop). See if the file is there, readable and without errors. You can compare it to other .desktop files in the same directory.

Or the tools displaying the menus etc. are broken, but I would expect that to affect other applications too. Is this problem limited to kolourpaint?

---

### Post by wyattwhiteeagle on 2022-03-08
> **Impavidus said:**
> This suggests that the .desktop file for kolourpaint cannot be found, isn't readable, is damaged or not there at all. Purging and reinstalling kolourpaint would normally restore the .desktop file, as it is in the main kolourpaint package (at /usr/share/applications/org.kde.kolourpaint.desktop). See if the file is there, readable and without errors. You can compare it to other .desktop files in the same directory.

Or the tools displaying the menus etc. are broken, but I would expect that to affect other applications too. Is this problem limited to kolourpaint?

It was limited to kolourpaint until I completely reinstalled Ubuntu.
That seemed to clear the problem...at least for a little while until it messes up again.

---

