---
title: "brand newbie - how to install applications?"
date: 2005-10-20
forum: General Help
---

### Post by nelox on 2005-10-20
I am a complete novice when it comes to linux but I have extensive Windows experience.

I've just completed a dual boot installation of breezy 5.10 and it seems to be working well.

How do I install applications?

I dowloaded a file which is in tar.gz format, and it is now sitting on my desktop. If I double click it, Extension Manager shows me its contents. There are no setup files (like in Windows) I can see. The readme states I need to compile first. How do I compile? Do I need to extact all the files from the archive first before I compile?

I'm lost and would greatly appreciate any help and/or links to sites which may provide it.

---

### Post by JimmyBEng on 2005-10-20
first go into Synaptic (system->administration->Synaptic Package Manager) and search for the program there.  If it in there installing is just a matter of right clicking and marking the package for install.  however if not usually the readme files tell you what commands to use to install.  hope this helps a bit.

---

### Post by professor_chaos on 2005-10-20
You can find a bunch of help by googling.

But, I'll try and help as best as I can.

First off, always check synaptic to see if it exists. This is the easiest and safest. Try adding repositories to get more software. I won't discuss that here. 

A tar.gz file is like a zip file. You need to uncompress/unpackage it first. type tar -xvzf something.tar.gz from the command line. This will uncompress the file and from there you will ususally find instructions/Readme that will guide you throught the rest.

---

### Post by aysiu on 2005-10-20
To use Synaptic, by far easier than installing in Windows, follow the instructions in my sig (step-by-step, with screenshots).

To add more repositories (i.e., more available software), follow these instructions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

