---
title: "How do I uninstall a program?"
date: 2014-07-01
forum: General Help
---

### Post by Supersonicx10 on 2014-07-01
I need to know how to uninstall a program you see him playing a game called AssaultCube and I can't connect to their new servers. I need to know how to uninstall this game then reinstall the game or any other program that I install so can anybody tell me how to do it?

---

### Post by oldos2er on 2014-07-01
If you used the Software Center, or any other APT front-end to install a package, you can also use it to remove a package. Hard to tell though if that will solve your issue of not being able to connect to their servers.

---

### Post by r_avital on 2014-07-01
When a program is installed on your Ubuntu system, the "Software Center" application should show it as installed, and you can uninstall it from there.

A more reliable program, the Synaptic Package Manager, will also show the program as installed, and you could uninstall from there as well.  If the program includes configuration data -- and most do, especially if it involves connecting to servers -- then the Synaptic program will let you use an option called "Completely remove" which will also remove that configuration data.  You probably want to use that option, since the connection info might be there, and if it's kept, reinstalling the game won't help much because it will use the same connection info.  But be aware that all that config info will be gone.

Alternatively, if you know the package name (not always the same name as the application's name), you could enter this in a terminal:

sudo apt-get purge package-name

It will first prompt you for your password, then execute.  Using purge instead of uninstall will guarantee that the configuration info will be removed as well.  

Also, when you use the purge option, if the program has any dependencies, meaning other programs that must be installed to help it run, which are NOT used by any other programs, the output of purge will list them and let you know it is safe to remove them, using "sudo apt-get autoremove" - and since those programs might have their own config data that could be the culprit for your game's problem, you probably should remove them as well.

After that, you can start a fresh installation of your app/game with reasonable confidence that anything that was incorrect in previous config information, is gone.

Hope this helps.

---

