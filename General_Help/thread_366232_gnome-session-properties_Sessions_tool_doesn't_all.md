---
title: "gnome-session-properties /Sessions tool/ doesn't allow to autostart programs"
date: 2007-02-20
forum: General Help
---

### Post by rafciu123 on 2007-02-20
Hi,

gnome-session-properties is a program which is accessible through System->Preferences->Sessions.

I try to autostart Firestarter and skype through this tool. I add paths to "Startup Programs" and I see them listed there. Then I close gnome-session-properties by clicking close button in the lower right corner and start it again and skype and firestarter are not there - they disapeared. 
I tried starting the tool through System->Preferences->Sessions and by typing sudo gnome-session-properties and the effect was the same. Firestarter and skype don't autostart and they don't appear in the tool after I restart it.

I would really appreciate your help.

Thanks!

---

### Post by mwolfe on 2007-03-08
I have this same problem.. everytime i add something to the startup programs it is gone when i open the program up again. Its really drivign me nuts. If anyone has any info please help, thanks

---

### Post by GadgetsGuy on 2007-04-27
I too have this problem, and it is DRIVING ME NUTS!!!

I add the programs to sessions, only to have them pull a HOUDINI on restart

HELP!

---

### Post by mwolfe on 2007-04-28
I believe the problem here has to do with permissions..
you might do something like

sudo chown -r  [yourusername] ./*

and that will set everything in your home directory, (all files, directories, and subdirectories)
to your username. I can't remember the specific folder that the session properties are in..
Note that if you for some odd reason you have other owners stuff in your home directory this isnt a good idea.. you really should be the owner of everything in your home directory though anyways.

---

### Post by GadgetsGuy on 2007-05-19
> **mwolfe said:**
> I believe the problem here has to do with permissions..
you might do something like

sudo chown -r  [yourusername] ./*

and that will set everything in your home directory, (all files, directories, and subdirectories)
to your username. I can't remember the specific folder that the session properties are in..
Note that if you for some odd reason you have other owners stuff in your home directory this isnt a good idea.. you really should be the owner of everything in your home directory though anyways.

chown: invalid option -- r  :(

---

### Post by seamless on 2007-05-19
The correct command is:

sudo chown -R +rw ./*

---

### Post by mwolfe on 2007-05-20
i dont think you want to do +rw on there.. although that might work..

The main thing i did wrong was the -r which was supposed to be -R

Always check the man pages for a command if something isn't working

you can check the man pages by typing
```
man [program]
```

in this example, do 
```
man chown
```

---

