---
title: "Need instructions on how to run Wine"
date: 2023-11-09
forum: General Help
---

### Post by markelfertig on 2023-11-09
It use to be, one could right click on an .exe file and wine was an option to open it - I'm not seeing that now.

Anyways, how do I tell wine, in terminal, to launch a file called Altirra64.exe  that is in my home folder in a folder called "Emulators"

Update:  I don't even think Wine installed - see attachment

I tried installing Synaptic package manager from Ubuntu Software center, and get the same error

---

### Post by deadflowr on 2023-11-09
Open a terminal and run the command it suggests.
```
sudo dpkg --configure -a
```

---

### Post by markelfertig on 2023-11-09
> **deadflowr said:**
> Open a terminal and run the command it suggests.
```
sudo dpkg --configure -a
```


Thanks you!

---

### Post by markelfertig on 2023-11-09
> **deadflowr said:**
> Open a terminal and run the command it suggests.
```
sudo dpkg --configure -a
```

ok, that worked to install wine - thanks.  It's still not showing up in "Show applications" on bottom left.

So it's installed.  What do I type into terminal, please, to run the .exe file I posted in my original post please.

---

### Post by yaminb on 2023-11-10
Another thing you can do is just use steam. 
You can actually add any .exe file to steam and use its launcher and proton to run 'windows' apps/games. 

I've found it just easier to work with.

---

### Post by markelfertig on 2023-11-10
bump.  I just want to know how to use wine in terminal to [COLOR=#000000]to launch a file called Altirra64.exe that is in my home folder in a folder called "Emulators"[/COLOR]

---

### Post by markelfertig on 2023-11-10
I figured it out.  I just changed director (cd) in terminal to my Emulators directory and the typed "wine Altirra.exe" into terminal

---

### Post by jimmyrus on 2023-11-10
> **markelfertig said:**
> I figured it out.  I just changed director (cd) in terminal to my Emulators directory and the typed "wine Altirra.exe" into terminal
Not surprised you got it since you been asking about wine for a long time. How many ids have you made so far?

---

### Post by jimmyrus on 2023-11-10
> **markelfertig said:**
> I figured it out.  I just changed director (cd) in terminal to my Emulators directory and the typed "wine Altirra.exe" into terminal
Not surprised you got it since you been asking about wine for a long time. How many ids have you made so far?

heres one [https://ubuntuforums.org/showthread.php?t=2266111&highlight=wine](https://ubuntuforums.org/showthread.php?t=2266111&highlight=wine)

---

