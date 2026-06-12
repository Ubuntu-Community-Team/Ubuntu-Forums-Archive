---
title: "gnomesword /usr/share/sword wont accept modules"
date: 2008-01-22
forum: General Help
---

### Post by notepad on 2008-01-22
i am trying to install modules in gnomesword, however the option to install modules to /usr/share/sword is not available. my only option is to install modules into ~/.sword.
this means that i have to install modules for my user account and then do it all again in my wifes user account.
in edit > module manager > configure > install destination, i wish to make the /usr/share/sword option available. why is it greyed out? how do i make that directory available in gnomesword for installing modules into?

---

### Post by Irihapeti on 2008-01-22
It will be because you don't have write access to the directory.
```
sudo chown -R (your user name) /usr/share/sword
``` 
should do it, or
```
sudo chmod -R 777 /usr/share/sword
```

The first won't give your wife write access to the directory, the second may but I'm not sure. She should be able to read them, though.

---

### Post by notepad on 2008-01-22
as simple as that! thanks man youve nailed it.

---

### Post by SanskritFritz on 2008-01-22
> **notepad said:**
> i am trying to install modules in gnomesword, however the option to install modules to /usr/share/sword is not available. my only option is to install modules into ~/.sword.
this means that i have to install modules for my user account and then do it all again in my wifes user account.
in edit > module manager > configure > install destination, i wish to make the /usr/share/sword option available. why is it greyed out? how do i make that directory available in gnomesword for installing modules into?Start Gnomesword just for the install like this:
 
gksudo gnomesword
 
or similar (you have to find out the program name and location if necessary, I'm at work now, no ubuntu here)
and then it will not be greyed out. Just install the modules for /usr/share/sword and dont forget to restart Gnomesword. It is because Gnomesword detects being started als root.

---

### Post by notepad on 2008-01-22
thanks sanskritfritz. thats an elegant way of achieving the same result when i want to install modules.

---

