---
title: "Apt not detecting flashplugin on system"
date: 2016-08-08
forum: General Help
---

### Post by courtney2 on 2016-08-08
I have flashplugin on my computer and want it gone. I see it on my system as "flashplugin-installer" and doing an apt-get remove or apt-get purge of that produces no results. This used to work but even specifying "flashplugin*" when removing does nothing. What's the best way to purge this from my system if I can't do it with apt?

---

### Post by CantankRus on 2016-08-08
What does this tell you?
```
dpkg --get-selections | grep -iE flash
```

How are you determining flash is installed?

---

### Post by grahammechanical on 2016-08-08
The flashplugin-installer is just the program that in stalls Flash. You most likely have removed the flash plugin installer. As for the flash software itself, that is another matter.

Regards

---

### Post by ajgreeny on 2016-08-08
Run commands ```
sudo updatedb #to update filesystem database
```
```
locate flashplugin #to find all files with flashplugin in the name in the system
```
That should give us some more clues about what is really currently installed.

Removing flashplugin-installer removes the actual flashplugin as well, but you may need to reboot and/or restart your browser to see the change.

---

### Post by courtney2 on 2016-08-08
Well I don't know how to answer this, but I tried to install flashplugin-installer and it installed it, and then purging it actually removed it from my system. I don't understand why apt wouldn't recognize it even with it installed, then let it install again but at least it's off now!

Edit to make my English suck a bit less

---

### Post by ajgreeny on 2016-08-09
Great! Please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by courtney2 on 2016-08-09
> **ajgreeny said:**
> Great! Please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to users searching the forum.

Done! Thank you for reminding me to do that :)

---

