---
title: "Wine: Only first word on each line appears in menus, dialogues"
date: 2007-06-06
forum: General Help
---

### Post by beow on 2007-06-06
Installed wine 0.9.38 from winehq ubuntu 7.04 repository. When running any windows application (including winecfg) only the first word, until a space character, shows up on a line. Note, that this happens only in menus, dialouges, buttons etc, not in the applications themselves. Sometimes an underscore appears where the space should be and then nothing until next line. I have msttcorefonts installed from the ubuntu repos.

It is very hard to use a menu or dialouge with only one word appearing on each line... Any ideas?

---

### Post by mättu on 2007-06-06
same problem here..
wine-0.9.37
on different machine works perfectly.
perhaps a bug in wine?
I've found some bug reports, but no solution.

cheers anyway
:m)

---

### Post by Lord Illidan on 2007-06-06
What are your specifications?

---

### Post by beow on 2007-06-07
How do you mean: specifications? 

wine 0.9.38, fresh install from winehq
feisty 7.04

Only installed ies4linux from the tatanka web site so far, using the script. One thing though, i have crossover office 6.00 installed on the same box, perhaps they interfere?

---

### Post by Enverex on 2007-06-07
Do you have FontForge and MS Core Fonts installed in Linux?

---

### Post by beow on 2007-06-08
Have msttcorefonts package:

```
$ dpkg -l | grep msttcore
ii  msttcorefonts     1.8ubuntu1    Installer for Microsoft TrueType core fonts

```

What is FontForge and howto install?

---

### Post by beow on 2007-06-08
Found and installed package "fontforge". No difference. I was wrong about applications above. IE6 also shows pages corrupted in the same way. There is an extra oddity also, text on a line is resumed when an "umlaut" character as (åäö) is present on the web page line. Also, lines that are formatted (bold, under-lined etc.) are shown correctly. However writing/saving a file in notepad and then open/reading it works fine with all lines rendered.

Any other ideas?

---

