---
title: "Compiz problem"
date: 2008-02-24
forum: General Help
---

### Post by robinsonspitz on 2008-02-24
I installed compizconfig-settings-manager for the cube and other visual effects. Everything was going fine until around the time when I installed flash player. The cube stopped working and when I went to Appearance Preferences/Visual Effects and selected "Custom", the window would turn grey and a minute later would automatically switch back to "None".

So, I reinstalled compizconfig-settings-manager and rebooted. Then my top panel and every title bar was gone. I reinstalled again and got those back, but when I click "Custom" in Visual Effects, it does the same thing.

Please help.

---

### Post by imoatama on 2008-02-24
What hardware are you runnning on? Also, can you tell me what the output is when you run 'compiz --replace' from a terminal?

---

### Post by robinsonspitz on 2008-02-25
Gateway GT5220:
AMD Athlon 64 X2 3800+ Dual Core Processor
Integrated GeForce 6150 Graphics with 128MB Shared Memory

Here's what it says when I run 'compiz --replace'
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0241 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Not a JPEG file: starts with 0x3c 0x21

---

### Post by imoatama on 2008-02-26
Does compiz acutally run? Just looking at the output you posted it seems like it is actually running.

What video drivers are you using to run the Geforce?

---

### Post by battlesound on 2008-02-26
I just solved my problem... very similar.  You need to open up synaptic and search for and install Xgl to make compiz work!

The package to install is called "xserver-xgl".  Then fiddle with everything as usual, you shouldn't have a problem.

---

### Post by NAdams81 on 2008-02-28
I'm having a problem like this as well.  I installed the xserver-xgl package from synaptic but I still don't have my window title bars.

When I try to change my windows preferences It says I need a compiz windows manager

---

### Post by robinsonspitz on 2008-03-01
I installed xserver-xgl and it hasn't made a difference.

The Extra appearance preferences seem to work fine.

I noticed that the layout of the Workspace Switcher Preferences window changed from when everything was working.

---

