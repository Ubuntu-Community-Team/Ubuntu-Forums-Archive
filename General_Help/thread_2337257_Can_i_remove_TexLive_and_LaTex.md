---
title: "Can i remove TexLive and LaTex?"
date: 2016-09-16
forum: General Help
---

### Post by ele2 on 2016-09-16
Hi,
I noticed that a texlive-doc folder is taking up 500MB of hard disk space. Can i safely remove it? 

Also, i am having a hard time understanding what is TexLive and LaTex, are they required in Linux or can be removed alltogether?

Thanks

---

### Post by claracc on 2016-09-16
Both of them are edition software and environment for producing scientific documentation:

please see: [https://www.latex-project.org/](https://www.latex-project.org/) and [https://www.tug.org/texlive/](https://www.tug.org/texlive/)

For most of people is enough to use libreoffice tools to type documents  but if you are going to write technical and scientific documents with good design, this is other wat to get it different from word processors.

---

### Post by Keith_Helms on 2016-09-16
If it's nothing you remember creating, yes you can remove it.  I do wonder how you managed to get a half gigabyte document folder on your system that you know nothing about.  Are there any files in that folder with names that you recognize?  

Those tools are not required and you can remove them.

---

### Post by Impavidus on 2016-09-16
The texlive-doc directory contains documentation for LaTeX. That is the best typesetting software in the world and I use it for every writing task, not just technical and scientific stuff. But if you don't need it, just uninstall.

Use the package manager. Don't simply remove the directory, as that may confuse the package manager. So open Ubuntu Software or Synaptic or whatever you always use, search for texlive, uninstall and autoremove the dependencies.

---

