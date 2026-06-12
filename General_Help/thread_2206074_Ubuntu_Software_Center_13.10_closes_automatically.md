---
title: "Ubuntu Software Center 13.10 closes automatically"
date: 2014-02-17
forum: General Help
---

### Post by Ilija_Gafur on 2014-02-17
I have problems with Ubuntu Software Center. When I want to open it it closes automatically. I hate it cuz I can't download applications now! I watched other threads like this [http://ubuntuforums.org/showthread.php?t=1714009](http://ubuntuforums.org/showthread.php?t=1714009) and this [http://ubuntuforums.org/showthread.php?t=1651765](http://ubuntuforums.org/showthread.php?t=1651765), I don't really have that list folder, just keyrings, mirrors, periodic, cdroms.list, extended_states. How to fix it? Help me please. When I try apt update it shows E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

---

### Post by Impavidus on 2014-02-17
Can you run the command```
cat -n /etc/apt/sources.list
```and post the output here?

(It will show the contents of your sources.list with line numbers. We want to know what's wrong with line 57.)

---

