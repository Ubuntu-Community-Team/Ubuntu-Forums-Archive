---
title: "Getting my installed apps since reinstalling"
date: 2007-11-29
forum: General Help
---

### Post by enchance on 2007-11-29
I'm planning on reinstalling ubuntu. Is there any way I could find out the full list of programs I've installed myself, meaning  I'm just looking for the ones I've installed on my own either through the terminal, synaptic, or add/remove.. That way I can delete out the ones which I won't install anymore.

Does this work?
```
dpkg --get-selections > ~/Desktop/installed\ applications
```

---

### Post by mpierce on 2007-11-29
Here's a script I wrote to do that every time I upgrade (change locate to what you need and make sure file is executable chmod +x (permission 755) and in path, i.e., /usr/local/bin

mpierce@mother:~$ cat /home/mpierce/Scripts/debian-installed.sh
#!/bin/sh
#Backs up the debian package list
#Currently installed packages
echo "Backing up debian package list for apt-get installed"
dpkg --list > /home/mpierce/CriticalFiles/Mother_debianlists.installed-packages.txt

You can use dpkg to reinstall the packages you have from the list.

Hope this helps...

---

