---
title: "Terminal Execute"
date: 2014-02-23
forum: General Help
---

### Post by chrislittle48 on 2014-02-23
Hey everyone, I know this probably is not the right format for this and it may have been asked before but here's what I have to ask. How do I get a text file to execute in terminal. Like say you want to click on a text file and it automatically open up terminal and execute the command. I want to run really basic command (mono Zero-K.exe) but when I click on the file named "Zero-k.sh" it just opens the text window that says...
"#!/bin/sh
mono Zero-K.exe"
I just want this to run in terminal without having to copy and paste. Im new to ubuntu so please dumb your answers WAY down. Thanks

Running Ubuntu 12.04

---

### Post by coldcritter64 on 2014-02-23
You can use the terminal to launch a script of course, but you can also launch some scripts simply by double clicking them if you set a nautilus option correctly. 

Look into this by opening any nautilus window (your home folder for example) and go to Edit > Preferences > Behaviour Tab > "Run executable text files when they are opened". I suspect that behaviour is what you want to open a windows .exe file with mono.

To run it in a terminal (maybe for script testing purposes and faultfinding) change directory (use the cd command) into the folder holding the script, eg for a script on your desktop "cd ~/Desktop". 

Then issuing the command
```
./Zero-k.sh
``` should launch the mono app, or show some output as to what is happening.

---

