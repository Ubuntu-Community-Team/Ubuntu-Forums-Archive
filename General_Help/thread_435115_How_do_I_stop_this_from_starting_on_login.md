---
title: "How do I stop this from starting on login?"
date: 2007-05-06
forum: General Help
---

### Post by ardchoille42 on 2007-05-06
Running Kubuntu Feisty. How do I stop kbluetoothd from starting when I log into KDE?
I have no bluetooth devices so this daemon is not necessary.
Is there a file I can edit or something?

---

### Post by nsleiman on 2007-05-06
go to Kmenu-System Settings--> Advanced-->System Services
and disable the startup from there, its the easiest way :)

---

### Post by RaZer0r on 2007-05-06
hmmz 2 options althoug i allways used gnome, but i assume it should be more or less the same on the kde environment.
go to your home directory, show the hidden files and look for a folder named: .config
there should be a folder in .config witch says: autostart, open that one and there are the executables that startup the other programs, just delete the one that you want not to startup :)

---

### Post by nsleiman on 2007-05-06
> hmmz 2 options althoug i allways used gnome, but i assume it should be more or less the same on the kde environment.
Guess under kde its .kde/Autostart/ 
:)

---

### Post by ardchoille42 on 2007-05-06
> **nsleiman said:**
> go to Kmenu-System Settings--> Advanced-->System Services
and disable the startup from there, its the easiest way :)

systemsettings always gives me an error, it won't start due to not being able to find a module. This won't work for me.
This is why I hate using gui's for something that can otherwise be edited manually by tweaking a text file.

---

### Post by ardchoille42 on 2007-05-06
> **RaZer0r said:**
> hmmz 2 options althoug i allways used gnome, but i assume it should be more or less the same on the kde environment.
go to your home directory, show the hidden files and look for a folder named: .config
there should be a folder in .config witch says: autostart, open that one and there are the executables that startup the other programs, just delete the one that you want not to startup :)

There is nothing in kde autostart (~.kde/Autostart).

---

### Post by ardchoille42 on 2007-05-06
Where are the file(s) that are parsed when kde launches (kde session reads a file and starts various apps to produce kde session)? I bet it's in there somewhere.

---

### Post by ardchoille42 on 2007-05-06
Ok, after some investigation, I figured it out.

```

sed -i 's/true/false/g' ~/.kde/share/config/kbluetoothdrc

```

GUI's are ok, but **I feel** that every user should learn how to configure the system via editing text files as a backup resource.. it may come in handy if X, or something else, refuses to start or is broken someday. And today was a perfect example, since the gui nsleiman mentioned doesn't work on my machine (it has never worked, even after a fresh install).

YAY for knowing how to maintain the system via command line :)

---

