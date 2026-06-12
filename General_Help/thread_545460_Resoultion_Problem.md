---
title: "Resoultion Problem"
date: 2007-09-07
forum: General Help
---

### Post by Thordious on 2007-09-07
I've just installed the drivers for my Nvidia 5500 and the res is stuck at 640x480, i don't know whats gone wrong, i need alittle help with this as i am new to Ubuntu.

---

### Post by bogdan_5844 on 2007-09-07
try this:

press Alt+F2,then type in:

gksudo gedit /etc/X11/xorg.conf

at the bottom of the file,there is a section called "Screen" wich has some resolutions written there(something like: 		Depth	24
		Modes		"1280x800"	"1024x768"	"640x480"
	EndSubSection )
search for the "Depth 24" section(just like i wrote up) and replace the first resolution(1280x800 in my case)with what your screen's native resolution is (if not sure try 1024x768,or look in the monitor's manual)save,restart and if the resolution is not changed,go to System->Preferences->Screen Resolution and change it from there
hope this helps ;-)

---

### Post by fragos on 2007-09-07
If you've used the Ubuntu "nvidia-glx" package, "nvidia-settings" was installed.  It's executed from the command line and runs as a GUI.

---

### Post by Thordious on 2007-09-09
I've tried these methods but no joy, i have a feeling it could be my monitor, in the Nvidia settings it registers my monitor as CRT-0, i know it can support higher resoultions because i use it with my SuSE machine too and thats set as 1280x1024.

---

