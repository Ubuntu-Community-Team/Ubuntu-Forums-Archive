---
title: "I've broken amsn--help please"
date: 2006-12-16
forum: General Help
---

### Post by dorcssa on 2006-12-16
Well, I made a mistake. Downloaded the new autopackage for amsn and I installed it(without removing the other, 0.95 version). Atfer that, I removed the old version. There were no icons, but I managed to start it. But in the manage third party projects, there were nothing, I couldn't remove it. So I removed the libraries manually from /home/use/.local/bin. All of them.(Yeah, it was a stupid thing to do) After that, I installed the 0.95 version with synaptic. Now I'm only able to start from /usr/share/amsn, the starting icon in the application menu doesn't work, and when I start it, it's acting like a 0.96 version, but the version number tells me it's 0.95 of course. Also I removed autopackage. But the thrid party project is still there. And I can't install the amsn autopackage now, it refuses to start the installation. Now what can I do to solve the problem? I don't have the libraries now(it would be easier than), coz I use krusader, and delelete files, not put them in the trash. Help please. :(

---

### Post by dorcssa on 2006-12-16
Somebody? Or I have to live with that?

---

### Post by Eddy Dean on 2006-12-16
Try to remove everything that has to do with amsn from synaptic (or do sudo apt-get remove amsn)

Then manually install the newest version.


Greetz,
Arno

---

### Post by dorcssa on 2006-12-16
I already did that. And removed the libraries manually. But when I install it with synaptic, and start it from the application menu, it tells me, that the childprocess failed (/home/use/.local/bin/amsn) execution(there's no such file or directory). And I can't install autopackage's anymore, i removed everything related, but I can still find mangae third party projects in the application menu. I can only start if from usr/share/amsn/amsn, it's the only way now

---

### Post by dorcssa on 2006-12-16
So, I installed it from source(never did that, good thing that I learned, a positiv thing from all of this), than I realized, I hade to link the execution file to /home/use/.local/bin/amsn, and the problem solved. Now I can start it from the application menu, but how to add an icon to it? And also how to remove that manage third party thing? I mixed something related with the whole autopackage thing, and if I can't fix it, I'll never be able to run one.

---

