---
title: "Circular reasoning..package install"
date: 2007-04-15
forum: General Help
---

### Post by katanabob on 2007-04-15
I'm installing pacakges (i.e. build-essential and its required associated packages) via USB pen drive. (computer has no working internet connection, no floppy, no CDROM.) I downloaded all applicable items from packages.ubuntu.com and have installed almost all of them in order... but I hit a wall. When trying to install any of the remaining packages, they require the installation one or two of the others as well as themselves. (Hence the circular reasoning)

Packages that remain: 

build-essential (requires the next 3)
g++ (requires g++-4.0 and libstdc++6-4.0-dev)
g++-4.0 (requires libstdc++6-4.0-dev and itself)
libstdc++6-4.0-dev (requires g++-4.0 and itself)

I verified that the files were downloaded from the proper repository (dapper) and that they were downloaded in entirety. Rebooted and tried again.. same result. 

Any suggestions would be greatly appreciated.

---

### Post by engla on 2007-04-15
Are you using the simple package installer that comes up when you double-click a .deb file? That program might not be able to handle this.

Can you use the command line (also called cli, terminal). You have to do that to "force" install these.

In the terminal, 'cd' to the directory where the packages are. Then 'sudo dpkg -i LIST' where LIST are all the deb files separated by space. Put in your admin password. After that run 'sudo dpkg -a' if needed.

---

### Post by katanabob on 2007-04-15
I can't believe I didn't even try the terminal before.. I made the stupid assumption that clicking would work the same. It worked; thank you very much-

---

