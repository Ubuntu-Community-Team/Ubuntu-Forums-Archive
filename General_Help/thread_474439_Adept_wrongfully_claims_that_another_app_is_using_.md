---
title: "Adept wrongfully claims that another app is using the packaging system database..."
date: 2007-06-15
forum: General Help
---

### Post by runoverbobby on 2007-06-15
either that or i'm just blind ;)

Pretty self-explanatory. I'm not running a terminal and/or using apt-get, Syaptic, etc. I keep checking my processes and cannot find one that could possibly be messing around with packaging. Does anyone know a way to find out what program is causing the problem? Or am I gonna have to type up all my processes for someone smarter than me to have a look at :(

EDIT: I tried rebooting. Several times.

---

### Post by Carlos The Cactus on 2007-07-22
I had the same problem, it was after some problem had caused a package installation (with a number of packages in it) to fail.

I solved it using the method described in this thread 
[http://ubuntuforums.org/archive/index.php/t-169068.html](http://ubuntuforums.org/archive/index.php/t-169068.html)

but to save you looking...

I opened a terminal window and entered "sudo apt-get install tetex-base"
(the actual package isnt important, just make it one you actually want! ;) )

the command failed, and i was prompted to run the command "sudo dpkg --configure -a"
this command also reported an error after installing some of the packages, but the important thing is that after running it the apparent lock on the packaging system database was lifted and adept_manager works ok again.

---

