---
title: "Location of configuration settings"
date: 2008-01-15
forum: General Help
---

### Post by davesmith on 2008-01-15
Hallo, i have two questions....i'm trying to find out if there a directory where Ubuntu installs programs, (coz i cant find it)

and could anyone plz tell me where to find the configuration/settings file for Pidgin? 

thanks

---

### Post by sumguy231 on 2008-01-15
Different parts of a program (libraries, executables, images) go to different relevant folders in the filesystem, and the package manager keeps track of where these files were put. 

User configuration files are usually in hidden files in your home directory. Hidden files start with a . and you can tell Nautilus to show them.

I'm pretty sure what you're looking for is in the .purple folder in your home directory.

---

### Post by davesmith on 2008-01-15
well now I thank you most kindy, what ive been looking for was indeed in the .purple folder!

---

