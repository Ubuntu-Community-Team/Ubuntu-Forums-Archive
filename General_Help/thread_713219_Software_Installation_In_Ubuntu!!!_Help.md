---
title: "Software Installation In Ubuntu!!! Help"
date: 2008-03-02
forum: General Help
---

### Post by vinlinux on 2008-03-02
How to install software in ubuntu?

i cannot install flash plugin from firefox???

how to install files from offline installtion, like realplayer linux


HELP

---

### Post by Nzer24 on 2008-03-02
Well, to install most programs, you can use the Add/Remove Programs in your main menu. That should be pretty straightforward. Installing other applications is a bit trickier. 

If they come in a .tar.bz2 or .tar.gz form, they are called tarballs. They contain source code for the application you want. To install them, use file-roller to extract them to your desktop. Then type these commands in a terminal:

cd ~/Desktop
cd (the name of the folder you extracted the files to)
./configure && make && sudo make install && make clean

This should compile and install any type of program.

Proprietary programs will not let you compile from source, so the tarballs will instead contain simple installer programs. If so, type this:

cd ~/Desktop
cd (the name of the folder you extracted the files to)
ls

Then you will have to identify the installer. Usually it will be called install, or something similar. Then type this:

./install

or type this:

./(whatever the name of the installer is)

Sorry if that is a bit tricky, but the package manager makes most things easy.

---

