---
title: "execute wine"
date: 2005-10-28
forum: General Help
---

### Post by alvin nepo on 2005-10-28
I already installed wine via synaptic package manager and checked it and it was already installed. How do I start the wine in my computer... please help...:confused:

---

### Post by aysiu on 2005-10-28
By double-clicking on a .exe file.
It won't work for all .exe files, but it'll work on a lot of them.

---

### Post by eyebrowman92 on 2005-10-28
how did you use synaptic to install wine because if you could tell me how to use synaptic that would be great. i cant figure out how to use it.

---

### Post by alvin nepo on 2005-10-28
ok ill try clicking some of my exe file previously stored in my external hard disk... thanks aysiu

for eyebrownman92 go to system click synaptic download manager, click search icon and type wine... please check if this will work to you...

---

### Post by alvin nepo on 2005-10-28
aysiu, ive tried and a popup menu appears saying could not dicplay  .exe file... is there any other way to use wine...

---

### Post by aysiu on 2005-10-28
[QUOTE=alvin nepo]aysiu, ive tried and a popup menu appears saying could not dicplay  .exe file... is there any other way to use wine...[/QUOTE] No, that's the way to use Wine. As I said before, it doesn't work on everything.

---

### Post by alvin nepo on 2005-10-28
ok thanks for the help...

---

### Post by Cyril on 2005-10-28
I have to disagree with aysiu.
Wine can be run from a terminal.
Try entering "wine filename.exe".
But before you do that, you probably wanna run winecfg in a terminal.

---

### Post by woopud on 2005-11-04
I installed wine using Automatix but when I type wincfg in a terminal is says
wine: creating configuration directory '/home/woopud/.wine'...
and it just hangs there forever with a blinking cursor on the next line
what's up with that ?

Bert

---

### Post by BoyOfDestiny on 2005-11-04
[QUOTE=alvin nepo]aysiu, ive tried and a popup menu appears saying could not dicplay  .exe file... is there any other way to use wine...[/QUOTE]

I don't think that way works right off the bat at all...

Try right clicking your exe, and choose open with and then under custom command type wine (or select it from the list if it's there).

If it works, make sure you right click on your file again and choose preferences, and it should always open with wine.

---

### Post by detyabozhye on 2005-11-04
First run winecfg or wine from the terminal, then right click an exe, and tell it to open with wine, after that, it should start up every time you double click it (if that exe works, of coarse).

---

### Post by aev on 2005-11-08
does anyone know a way to open .hlp (help) files in linux?  Or convert them may be in .html at least? Because I have some documents in HLP format with an EXE file opening it under windows, but WINE does not open neither this EXE, not the HLP file.
thanks.

---

### Post by detyabozhye on 2005-11-09
Try copying winhlp32.exe from the System32 folder on a Windows installation and try to run that. That might help, but I haven't tried it and can't really do it right now.

---

