---
title: "Finding programs once I've installed them"
date: 2008-07-09
forum: General Help
---

### Post by herschen on 2008-07-09
This has probably been addressed somewhere else (and feels a little silly), some programs are automatically added to the list of Applications, some automatically to System, and some I cannot find (opensync). Where do these get installed? Is it a command-line program? And what is the basic difference between Add/Remove Programs, the Synaptics Manager and installing packages from the Internet? Is how well a program runs with Ubuntu what dictates where it gets placed?

---

### Post by iaculallad on 2008-07-09
> **herschen said:**
> This has probably been addressed somewhere else (and feels a little silly), some programs are automatically added to the list of Applications, some automatically to System, and some I cannot find (opensync). Where do these get installed? Is it a command-line program?

Some applications that are installed are terminal-based, and some are GUI based. For GUI based applications, you can find them on the Applications menu. For terminal-based applications, try to find their location by using the **locate** terminal command.

i.e: ```
locate nmap
```

> **herschen said:**
> And what is the basic difference between Add/Remove Programs, the Synaptics Manager and installing packages from the Internet? 

Add/Remove option let you install/add applications in general, while Synaptics let you install/add applications in particular.

> **herschen said:**
> Is how well a program runs with Ubuntu what dictates where it gets placed?

For system binaries, they are installed in the /sbin directory, /usr directory for user utilities and applications, /boot for kernels, etc...

---

### Post by Taxman415a on 2008-07-10
Sometimes unfortunately even gui programs do not get added anywhere in the applications menu tree. It happens if the package maintainer doesn't fix the package properly. If it is something you have installed through synaptic, add/remove, or even manually as a .deb package, you can open synaptic, find the package by name then right click it and go to properties then look at the 'Installed files' tab. Look for something in a /bin directory. Some packages install more than one binary, then you can always go to a terminal and run man whatever to get the manual pages and find out what binary you want. Then you can manually add the program to the Applications menu tree by right clicking on Applications and selecting edit menus. Put in the full location of the binary that you found in synaptic.

Yeah, so it's not easy, but it will get you what you're looking for. The other way is to run dpkg -L on the package name, and that may be easier or harder for you depending on your preferences.

---

### Post by Grandma_DOG on 2008-07-16
> **Taxman415a said:**
> Sometimes unfortunately even gui programs do not get added anywhere in the applications menu tree. It happens if the package maintainer doesn't fix the package properly. If it is something you have installed through synaptic, add/remove, or even manually as a .deb package, you can open synaptic, find the package by name then right click it and go to properties then look at the 'Installed files' tab. Look for something in a /bin directory. Some packages install more than one binary, then you can always go to a terminal and run man whatever to get the manual pages and find out what binary you want. Then you can manually add the program to the Applications menu tree by right clicking on Applications and selecting edit menus. Put in the full location of the binary that you found in synaptic.

Yeah, so it's not easy, but it will get you what you're looking for. The other way is to run dpkg -L on the package name, and that may be easier or harder for you depending on your preferences.

I have been struggling with this, too.  As I just moved my office over to UBUNTU, I have 6 machines here and don't know what I've got installed on which so I need to solve this. Now that you have showed me how to put them on the menu, I've found an easier what to locate the bin file.

simple use the 'whereis xxxxx' comand and do a copy and paste.  So if i think i have Quantum GIS installed on a machine, i do a "whereis qgis" and it pulls up:
qgis: /usr/bin/qgis /usr/lib/qgis /usr/share/qgis /usr/share/man/man1/qgis.1.gz

so I copy the 
/usr/bin/qgis  to the menu for quantum.

---

