---
title: "Desctop effects are very slow in Hardy"
date: 2008-04-26
forum: General Help
---

### Post by BomjKolyadun on 2008-04-26
After updating to Ubuntu 8.04 desktop effects became very slow. 
I am using laptop Fujitsu-Siemens l1310g with Radeon X200m graphics with fglrx driver and xserver-xgl installed.

---

### Post by Zorael on 2008-04-26
Though I'm not the guy to ask about ATI drivers, do get rid of xserver-xgl. See if it helps.
```
$ sudo aptitude purge xserver-xgl
```

---

### Post by BomjKolyadun on 2008-04-26
White screen :( 
But safe GNOME works well, so I think that problem with xgl. The question is how to remove xserver-xgl and get GNOME work without it.:confused:

---

### Post by Zorael on 2008-04-26
Is that a laptop? I've seen posts about compiz stopping when it notices the system is an ati laptop. Xgl circumvents this, but it's slow as heck.

What is the output of the following entered in a terminal? Of course, with xgl removed. :>
```
$ compiz --replace & sleep 5; metacity --replace &
```

It will disable compiz after five seconds, so even if you lose window control you don't have to restart X. We want the terminal output.

---

### Post by BomjKolyadun on 2008-04-26
I can't login without xserver-xgl into normal GNOME session :(

---

### Post by Zorael on 2008-04-26
Owkay. :>

Try this, then. Install xserver-xgl, disable desktop effects (should disable Compiz), then remove xserver-xgl again and restart X with Ctrl+Alt+Backspace. If Compiz isn't disabled, there are some other things we could do to force it, but try that first.

We really want to get rid of xserver-xgl.

---

### Post by BomjKolyadun on 2008-04-26
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5a62 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
[2] 21759
dmitry@DimaPC:~$ GConf backend: There is an unsupported value at path /apps/compiz/plugins/expo/allscreens/options/expo_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

[1]-  Done                    compiz --replace

---

### Post by Zorael on 2008-04-26
So what works at this point?

Also, if you're not getting window titlebars or borders, try entering the following after having started compiz.
```
$ gtk-window-decorator --replace &
```
Or, if you want to use (and have installed) emerald;
```
$ emerald --replace &
```

---

### Post by BomjKolyadun on 2008-04-26
After starting compiz screen became white, but now when I am working without any desktop effects compiter works much faster and I can launch normal GNOME session :). I think that there's some problem with compiz configuration, so I am going to try to configure gconf or reinstall compiz ...

---

### Post by russo.mic on 2008-04-26
What's happening probably is that you've got the new ati driver installed from the restricted manager, and you don't need xgl anymore.  starting it on top of AIGLX causes huge slowdowns.  

When you remove xgl, and try to start an XGL session, it of course won't start.  You don't need to start an xgl session anymore. 

Start up a normal gnome session, then just run compiz in a terminal or in the run dialog.  Almost bet an eyebrow it works.

Russo

---

### Post by BomjKolyadun on 2008-04-26
I've started normal GNOME session.:)
So I found the solution :)  I've added some options to xorg.conf.

> Section "Device"
	Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
	Option		"VBERestore"	"true"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"XAANoOffscreenPixmaps"	"on"
	Option		"VideoOverlay"	"off"
	Option		"OpenGLOverlay"	"off"
	Option		"TexturedVideo"	"on"
	Option		"Textured2D"	"on"
	Option		"TexturedXrender"	"on"
	Option		"UseFastTLS"	"1"
	Option		"BackingStore"	"on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
	Option		"AIGLX"	"on"
EndSection

Section "DRI"
	Group		"Video"
	Mode	0666
EndSection

Maybe there's some extra options enabled ... But the main thing that it works

---

### Post by strato03 on 2008-09-03
hi,i have the same thing too,effects are very slow after updating.tried to follow the steps but i'm stuck with the white screen....please help! im still a newbie to this,its still my 2nd week in ubuntu. tried to add the options on xorg.conf but i was thinking if its the same for all ATI vcard,i have x1550 pro,and how can i edit it..wahhh..x_x!i was thinking of re installing my gutsy but i just downloaded the update for 8.04 for the whole day because i got a slow connection and its kinda waste of time.if there is any way to sort this out....i would really appreciate it...thanks a lot!

---

