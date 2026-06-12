---
title: "Package manager broken?"
date: 2007-09-30
forum: General Help
---

### Post by Dave54 on 2007-09-30
I want the "refocus" plugin for Gimp, however it's not in the repositories. Its website has only the source, which I could not get to compile correctly.

Then, I found this page: [http://packages.debian.org/lenny/gimp-refocus/i386/download]("http://packages.debian.org/lenny/gimp-refocus/i386/download")

I went to synaptic and added "deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) lenny main" as a 3rd party repository. Now, when I start Synaptic, it says:```
E: Dynamic MMap ran out of room
E: Error occurred while processing vdr-plugin-skinenigmang (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.de.debian.org_debian_dists_lenny_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

How do I fix Synaptic, and what did I do wrong?

---

### Post by tbroderick on 2007-09-30
Try removing the debian lenny line and run sudo apt-get update.

---

### Post by Seisen on 2007-09-30
I wouldn't recommend using debian repositories in Ubuntu either but you can try just downloading that individual package and installing it using Gdebi (double-click on the file).

---

