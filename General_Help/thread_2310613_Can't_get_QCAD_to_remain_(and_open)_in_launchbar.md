---
title: "Can't get QCAD to remain (and open) in launchbar"
date: 2016-01-20
forum: General Help
---

### Post by RayArdia on 2016-01-20
Using Ubuntu 14.04 on an Acer Aspire 4GB Ram 320GB HDD with 2x 2TB Seagate Expansion Drives.
I use QCAD for drawings (/qcad-3.6.4-pro-linux-x86_32) and can open it OK from Terminal, and it appears as a symbol in the Launchbar line-up.
Although I select 'Lock to Launcher' the symbol disappears as soon as I  close the program.
Terminal output:-
ray@ray-Aspire-5735:~/ray$ cd qcad-3.6.4-pro-linux-x86_32
ray@ray-Aspire-5735:~/ray/qcad-3.6.4-pro-linux-x86_32$ ./qcad
Program opens and is usable.
Terminal process continues with various 'Debug: ' lines such as:-
Debug:    creating QApplication 
Debug:    RDwgPlugin::init 
Debug:    RDxfPlugin::init 
Debug:    RHelpPlugin::init 
Debug:    RProScriptsPlugin::init 
Debug:    TIMER:  107 ms -  "loading add-ons" 
Debug:    registering svg file importer 
Debug:    TIMER:  920 ms -  "initializing add-ons" 
Debug:    RPluginBase: postInit:  "DWG" 
Debug:    RPluginBase: postInit:  "Pro Tools" 
.and more, but they take a long time to get through.
How do I get QCAD to 'stick' to Launchbar?

---

### Post by ajgreeny on 2016-01-20
I was confused by your use of the word launchpad which means something entirely different to most of us on the forum so I have changed the title and the instances of the word in the post to launchbar, which is what you actually meant.

Sorry but I can not answer your query personally; I use Xubuntu not Ubuntu.

---

### Post by RayArdia on 2016-01-21
> **ajgreeny said:**
> I was confused by your use of the word launchpad which means something entirely different to most of us on the forum so I have changed the title and the instances of the word in the post to launchbar, which is what you actually meant.

Sorry but I can not answer your query personally; I use Xubuntu not Ubuntu.

Many thanks for your reply, sorry I confused the issue by using Launchpad instead of Launchbar.
Sorry too that you couldn't help me - here's hoping someone else can!

---

### Post by monkeybrain20122 on 2016-01-21
It does here, though it is the free version (3.9.3) and 64 bit and on Ubuntu 15.04. The latest for qcad free versionis 3.12.5, not sure if the same version in pro, if so just upgrade it.

---

### Post by RayArdia on 2016-01-25
> **monkeybrain20122 said:**
> It does here, though it is the free version (3.9.3) and 64 bit and on Ubuntu 15.04. The latest for qcad free versionis 3.12.5, not sure if the same version in pro, if so just upgrade it.
Downloaded free version (which is QCAD 3.12.5 btw),reinstalled and everything is back to normal.
Many thanks for everyone's help.

---

