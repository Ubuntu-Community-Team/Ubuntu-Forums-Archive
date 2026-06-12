---
title: "No barre on my windows!!"
date: 2007-10-10
forum: General Help
---

### Post by gilligan on 2007-10-10
Hi,

I have a problem with all the windows I open in Ubuntu. The only way I can sloe them is with Alt+F4! The 3 buttons on the upper right corner are gone!! How can I get them back?

Thanks for your help.

---

### Post by #Reistlehr- on 2007-10-10
you are using beryl, arent you?

---

### Post by gilligan on 2007-10-10
Nope, I'm using Compiz Fusion

---

### Post by #Reistlehr- on 2007-10-10
is it an nvidia video card?

(compiiiz and beryl are merged now, so it's the same thing)

---

### Post by gilligan on 2007-10-10
no, it's not a NVIDIA. It is integrated into chipset.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07577&lc=en&cc=us&dlc=en&product=83455&lang=en#N534](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07577&lc=en&cc=us&dlc=en&product=83455&lang=en#N534)

---

### Post by #Reistlehr- on 2007-10-10
2 things that i can suggest is:


in the 

/etc/X11/xorg.conf file

Scroll down to where it says
```
Section "Screen"
```

look for:
```
DefaultDepth    24
```

If it is not set to 24, which it's probably at 16, set it to 24. 

Then, right benieth where you make the last change, add the line

```
    Option         "AddARGBGLXVisuals" "True"
```

Hopefully that does the trick.

---

### Post by gilligan on 2007-10-10
Just tried that and it didn't even give me the option "SAVE". Only "Save As" and it didn't work.

---

### Post by Martje_001 on 2007-10-10
> **gilligan said:**
> Just tried that and it didn't even give me the option "SAVE". Only "Save As" and it didn't work.

You have to open it as root. So in a terminal:
```

gksudo gedit /etc/X11/xorg.conf file
```

---

### Post by gilligan on 2007-10-10
Unfortunately it didn't work. I had those buttons when I restarted, but when I typed "compiz --replace", they've gone!!

---

### Post by Martje_001 on 2007-10-10
Have you installed emerald? If not, do this in a terminal:
```
sudo apt-get install emerald
```

if so:
```
emerald --replace &
```

---

### Post by gilligan on 2007-10-11
Hi,

I just did the emerald thing, I got this message:
"emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

What if I just uninstall compiz and reinstall it back? Will it work?

---

### Post by #Reistlehr- on 2007-10-11
i use beryl, and not compiz, so im not sure. but worth a try.

---

