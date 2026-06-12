---
title: "How to install &quot;Apple Macintosh LC&quot; in Virtualbox under Linux?"
date: 2008-05-25
forum: General Help
---

### Post by frenchn00b on 2008-05-25
How to install "Apple Macintosh LC" in Virtualbox under Linux?
Wanna play my old games, and run my old mac floppies. [http://histoire.info.online.fr/images/col-lc475.jpeg](http://histoire.info.online.fr/images/col-lc475.jpeg)

---

### Post by shifty_powers on 2008-05-25
heh sim city ;)

is apple macintosh lc an operating system?

---

### Post by danwood76 on 2008-05-25
I dont think you can on virtualbox as the Old MacOS runs on the PowerPC architechture.
You probably can run it under qemu which I think emulates PowerPC

---

### Post by frenchn00b on 2008-05-25
> **danwood76 said:**
> I dont think you can on virtualbox as the Old MacOS runs on the PowerPC architechture.
You probably can run it under qemu which I think emulates PowerPC

I think some released some dd image stuffs of the OS, no? Can it be right. Dont know, I am n00b in that Linux/virtualbox/qemu stuffs ...

:guitar: 
edit:
a guy on irc told me about this : [www.osx86project.org](www.osx86project.org)
but that could maybe emulate this Mac LC with virtualbox: [http://vectronicsappleworld.com/appleii/articlepics/internet/desktop4.jpg](http://vectronicsappleworld.com/appleii/articlepics/internet/desktop4.jpg)

---

### Post by danwood76 on 2008-05-25
Not sure, most mac games are available for the PC so you may be able to obtain them in x86 format which will be easier to run.

Otherwise you will need a Mac install CD (Or disks in case of an older mac ~OS 7) and use qemu to emulate the PowerPC CPU then install Mac OS on the virtual machine.
I have no experiance with using qemu to emulate PowerPC, I have only used it to emulate MIPS so I cant help much further.

---

### Post by frenchn00b on 2008-05-25
Isnt the program called basilisk, [http://basilisk.cebix.net/#download](http://basilisk.cebix.net/#download)
to emulate the mac ?

from: [http://forums.macosxhints.com/showthread.php?t=41900](http://forums.macosxhints.com/showthread.php?t=41900)

the bin/discs of the OS system 7 and so on are on the apple site: [http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/](http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/)

---

### Post by danwood76 on 2008-05-25
I was just reading another post referring to sheapshaver.
It looks like it does MacOS (PowerPC, OS 7.5 > OS 9.0) basilisk does the really old 680 Mac Processor, before PowerPC (OS 0.x > OS 7.5)

[http://gwenole.beauchesne.info/en/projects/sheepshaver](http://gwenole.beauchesne.info/en/projects/sheepshaver)

Essentially it depends which Mac OS version you want to run.

---

### Post by frenchn00b on 2008-05-25
> **danwood76 said:**
> I was just reading another post referring to sheapshaver.
It looks like it does MacOS (PowerPC, OS 7.5 > OS 9.0) basilisk does the really old 680 Mac Processor, before PowerPC (OS 0.x > OS 7.5)

[http://gwenole.beauchesne.info/en/projects/sheepshaver](http://gwenole.beauchesne.info/en/projects/sheepshaver)

Essentially it depends which Mac OS version you want to run.

Dont you think that basilik since 2001, is it not out of date. Could virtualbox maybe do the job btw, since it is more up to date?

some disks: [http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.5_Version_7.5.3/](http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.5_Version_7.5.3/)

---

### Post by danwood76 on 2008-05-25
Basilisk2 is 2006:
[http://gwenole.beauchesne.info/en/projects/basilisk2](http://gwenole.beauchesne.info/en/projects/basilisk2)

But as I said in my last post if you want to run anything > 7.5 (which I would have thought you would) then you need sheepshaver.
Basilisk2 for anything lower than that.

Those images are update images only to go from 7.5 to 7.5.3, the actual install CD image will be more like 300 MB - 500 MB.
There are some OS 8.6 Sheepshaver images around on bittorrent (just searched TPB) but you obviously need to own a Mac of this age to have the license to run the OS legally.

---

### Post by frenchn00b on 2008-05-25
I found all emulators here : [http://www.simon.mooli.org.uk/LXF/AppleMacs/AppleMacs.html](http://www.simon.mooli.org.uk/LXF/AppleMacs/AppleMacs.html)
 
Maconlinux is for the version X, as I may see. 
Executor runs out of the bulk.
  
Pitty that emulating whatever (in linux or other) is tricky, always, somehow... never easy

---

### Post by shifty_powers on 2008-05-25
think you kind of misunderstand what virtualbox is for.

it is not an emulator. it is a program that lets you install a full, working copy of an operating system within another.

so for example, you could have ubuntu running, use virtualbox and the have windows xp installed and running within a window within ubuntu ;)

to do what you want wirth virtualbox, you would need the installation material for the os that your games ranon...

---

### Post by frenchn00b on 2008-05-25
> **shifty_powers said:**
> think you kind of misunderstand what virtualbox is for.

it is not an emulator. it is a program that lets you install a full, working copy of an operating system within another.

so for example, you could have ubuntu running, use virtualbox and the have windows xp installed and running within a window within ubuntu ;)

to do what you want wirth virtualbox, you would need the installation material for the os that your games ranon...

Bah when one think ... why not, that the projects could merge together ?
then you have an universal program that does all kind of emulations & running OS's Intel/Mac/...  
(oup's sorry)

---

### Post by danwood76 on 2008-05-25
There is a differnce between virtualisation and emulation.
Thats why there are different programs.

Sheepshaver is a PowerPC (Mac OS 7.5 - 9) emulator which runs fine under linux from what I have read.
That page you referenced to is outdated.

---

### Post by dagnabit dang doohickey on 2008-05-25
If you decide to install sheepshaver, you may have to modify the keycode file. The keycode file that comes with sheepshaver is a little old and the *vendor string* is set up for use with xfree86. The slight modification that needs to be done is to change the *vendor string* for use with xorg. To use the new keycode file, select it in the sheepshaver preference pane.

The following is my keycode file. As far as I can remember, the only modification I made was changing the *vendor string* to "The X.Org Foundation" from whatever the xfree86 string was. I keep it in ~/.sheepshaver (along with my rom and my OS9 image.)
```
# /usr/share/BasiliskII/keycodes
#
# Basilisk II (C) 1997-2005 Christian Bauer
#
# This file is used to translate the (server-specific) X11 keycodes to Mac
# keycodes depending on the X11 server being used.
#
# The format of this file is as follows:
#
# <vendor string>
# <X11 keycode> <Mac keycode>
# <X11 keycode> <Mac keycode>
# <X11 keycode> <Mac keycode>
# ...
# <vendor string>
# <X11 keycode> <Mac keycode>
# <X11 keycode> <Mac keycode>
# ...
#
# The "vendor string" must match the first part of the X11 server vendor
# description as reported by ServerVendor(). If a match is found, the keycode
# translation table is constructed from the following lines. Each line
# contains an X11 keycode followed by its associated Mac keycode. Both
# keycodes have to be given in decimal. Lines beginning with "#" or ";" are
# treated as comments and ignored.
#

#
# X.Org
#
The X.Org Foundation
9	53	# Esc
67	122	# F1
68	120	# F2
69	99	# F3
70	118	# F4
71	96	# F5
72	97	# F6
73	98	# F7
74	100	# F8
75	101	# F9
76	109	# F10
95	103	# F11
96	111	# F12
111	105	# PrintScrn
78	107	# Scroll Lock
110	113	# Pause
49	10	# `
10	18	# 1
11	19	# 2
12	20	# 3
13	21	# 4
14	23	# 5
15	22	# 6
16	26	# 7
17	28	# 8
18	25	# 9
19	29	# 0
20	27	# -
21	24	# =
22	51	# Backspace
106	114	# Insert
97	115	# Home
99	116	# Page Up
77	71	# Num Lock
112	75	# KP /
63	67	# KP *
82	78	# KP -
23	48	# Tab
24	12	# Q
25	13	# W
26	14	# E
27	15	# R
28	17	# T
29	16	# Y
30	32	# U
31	34	# I
32	31	# O
33	35	# P
34	33	# [
35	30	# ]
36	36	# Return
107	117	# Delete
103	119	# End
105	121	# Page Down
79	89	# KP 7
80	91	# KP 8
81	92	# KP 9
86	69	# KP +
66	57	# Caps Lock
38	0	# A
39	1	# S
40	2	# D
41	3	# F
42	5	# G
43	4	# H
44	38	# J
45	40	# K
46	37	# L
47	41	# ;
48	39	# '
83	86	# KP 4
84	87	# KP 5
85	88	# KP 6
50	56	# Shift Left
94	50	# International
52	6	# Z
53	7	# X
54	8	# C
55	9	# V
56	11	# B
57	45	# N
58	46	# M
59	43	# ,
60	47	# .
61	44	# /
62	56	# Shift Right
51	42	# \
98	62	# Cursor Up
87	83	# KP 1
88	84	# KP 2
89	85	# KP 3
108	76	# KP Enter
37	54	# Ctrl Left
115	58	# Logo Left (-> Option)
64	55	# Alt Left (-> Command)
65	49	# Space
113	55	# Alt Right (-> Command)
116	58	# Logo Right (-> Option)
117	50	# Menu (-> International)
109	54	# Ctrl Right
100	59	# Cursor Left
104	61	# Cursor Down
102	60	# Cursor Right
90	82	# KP 0
91	65	# KP .

```

---

### Post by frenchn00b on 2008-05-25
> **danwood76 said:**
> Basilisk2 is 2006:
[http://gwenole.beauchesne.info/en/projects/basilisk2](http://gwenole.beauchesne.info/en/projects/basilisk2)

But as I said in my last post if you want to run anything > 7.5 (which I would have thought you would) then you need sheepshaver.
Basilisk2 for anything lower than that.

Those images are update images only to go from 7.5 to 7.5.3, the actual install CD image will be more like 300 MB - 500 MB.
There are some OS 8.6 Sheepshaver images around on bittorrent (just searched TPB) but you obviously need to own a Mac of this age to have the license to run the OS legally.
 
Hallo,
I compiled Sheepshaver, then installed all so that it works. I am stuck now how simply to configure it. And once you get this, and it you put the DSK type file into add, like this : [http://img338.imageshack.us/img338/2824/sheepshaverconfiguratiown2.jpg](http://img338.imageshack.us/img338/2824/sheepshaverconfiguratiown2.jpg)
It gives an error ... I have no idea how to make it works;...

---

### Post by danwood76 on 2008-05-26
I got mine working with OS9 last night.
It runs OS9 about as fast as my Starmax did, faster than my performa not too bad really.

You need to tell it where the ROM file is in the Misc options as well as the disk image, though the disk image should just load up and show a path in that first window.
What error are you getting?

---

### Post by brunolabs on 2009-08-22
> **frenchn00b said:**
> How to install "Apple Macintosh LC" in Virtualbox under Linux?

Just wondering, is it possible to install any Linux distro in a Mac LC? I own one since 1990, my first desktop computer, still works :).
It only has a floppy disk drive. No CD reader or USB drive.

System specs here: (model LC)
[http://en.wikipedia.org/wiki/Macintosh_LC]("http://en.wikipedia.org/wiki/Macintosh_LC")
except RAM which is 10 MB.:lolflag:

Has anyone here installed (or knows how to install) Linux on such old computers?

---

### Post by brunolabs on 2009-11-03
Curious bump :)

---

### Post by frenchn00b on 2009-12-07
here a great howto for ubuntu : [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7941077](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7941077)

---

### Post by pmooney78 on 2010-05-29
> **brunolabs said:**
> Just wondering, is it possible to install any Linux distro in a Mac LC? I own one since 1990, my first desktop computer, still works :).
It only has a floppy disk drive. No CD reader or USB drive.

System specs here: (model LC)
[http://en.wikipedia.org/wiki/Macintosh_LC]("http://en.wikipedia.org/wiki/Macintosh_LC")
except RAM which is 10 MB.:lolflag:

Has anyone here installed (or knows how to install) Linux on such old computers?

Personally, I doubt it ... initial Linux development didn't start 'til 3 years after the LC came out, and there are no modern distributions that run on hardware based on Motorola's 68k series of microchips, as far as I know. Wikipedia doesn't list anything on their extensive list, either: [http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions). There are Linux distros that run on PowerPC-based hardware, but not 680x0.

If you want to run a Unix-like system on the Mac, Apple used to sell something called A/UX which did exactly that. It may be available as abandonware on their site, or you might try poking around the Internet for it. :)

---

