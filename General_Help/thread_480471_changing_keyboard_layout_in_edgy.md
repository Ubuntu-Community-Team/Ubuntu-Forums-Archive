---
title: "changing keyboard layout in edgy"
date: 2007-06-21
forum: General Help
---

### Post by teh_luke on 2007-06-21
hi

i cannot change the keyboard layout in edgy eft
neither by using the gnome keyboard properties, nor by setting the wanted layout in xorg.conf
i did dpkg-reconfigure the xserver and selected appropriate settings with no effect
on installation i selected "de" however i'd like to change to "us" now
the only thing that works is setxkbmap us, but the setting is not stored on reboots, so it has to be done every time again

i'm not seeking for a solution which combines setxkbmap with startup scripts
i would like it to work the ordinary way

thanks in advance

---

### Post by Persianelfster on 2007-06-21
I am not sure, but i think you may be able to change it in System Administration Language support, so try that

---

### Post by teh_luke on 2007-06-22
hi
the default language is english

the language i chose at installation was us english
the keyboard layout however was de

where does ubuntu store the system-keyboard-layout
the one that was chosen during installation
because in x the only way i can change the layout is with setxkbmap
however, of course, in the console (ctrl alt f1) it stays german
so this must be the default language which ubuntu falls back at on restart
being able to change the layout globally, not only for x, would be cool
how to do that

---

### Post by teh_luke on 2007-06-26
hi

what about developers
either this is a bug, or there is a possibility to revert the setting made at installation stage (since the system has memorized what i selected it has to be saved somewhere.)
also, i have read much about this, on google, but in all cases there was noone with a solution, except with the hack "just use setxkbmap"

please help
thanks so far

---

### Post by Persianelfster on 2007-07-07
System preferecnces and then keyboard and keyboard layouts tab add, then you will check which one you want default,

---

