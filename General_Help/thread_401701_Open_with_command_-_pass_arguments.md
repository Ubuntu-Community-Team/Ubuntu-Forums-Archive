---
title: "Open with command - pass arguments?"
date: 2007-04-04
forum: General Help
---

### Post by intel352 on 2007-04-04
Okay, I've downloaded a number of .nrg files, which are Nero CD Image files. I then found a nice application called nrg2iso, which is a command-line app. I would like to be able to right-click on a .nrg file and select the nrg2iso command to have the file autoconverted.

The problem is, I don't know how to pass advanced arguments with the right-click Open With Command context.

What i need, is to be able to specify:

nrg2iso [FILENAME THAT I CLICKED ON].nrg [FILENAME THAT I CLICKED ON, minus the nrg].iso

Is there a way to pass the selected file as a variable? and then to strip the extension to rename to iso?

---

### Post by irwa82 on 2007-04-05
Hi,

First thing that comes to my mind is to create a small shell script for it. This should create filename.nrg.iso file for you in the same place that the file exists.

convertnrg  (the filename for you to create)
--------------------------------
#!/bin/sh
nrg2iso $1 $1.iso
--------------------------------

$ chmod 755 convertnrg
$ sudo cp convertnrg /usr/bin

test the shell script in a command line

$ convertnrg nrgfilename.nrg

if it does what you want you are set.

---

### Post by intel352 on 2007-04-08
thx, that should work  ;-)

---

