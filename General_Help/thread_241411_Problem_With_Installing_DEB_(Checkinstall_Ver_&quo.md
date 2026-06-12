---
title: "Problem With Installing DEB (Checkinstall Ver &quot;Looks&quot; Older Then the Repository One)"
date: 2006-08-22
forum: General Help
---

### Post by Christmas on 2006-08-22
I made a deb file from Kopete 0.12.1 using:
```
./configure
make
sudo checkinstall
```
The DEB that resulted is kopete_0.12.1-1-i386.deb and Kopete works now, it's at the last version (0.12.1). The problem is that each time I make an upgrade, it wants to replace my newly installed Kopete with the repositoy version, which is (as "apt-cache show kopete" shows me) 4:3.5.2-0ubuntu6. So each time I upgrade my system, Kopete will be replaced by the old 0.11.1 version and I have to install it manually again. Is there a ways to make this disappear? I think I can change the version to the DEB checkinstall generates to something like 5:0.12.1-1 or whatever is bigger than 4:3.5.2, but this doesn't seem an elegant solution, the DEBs version should be accurate.

---

### Post by Sboulema on 2006-08-22
Same problem here. I always make the deb with a higher version number, something like: 4:3.5.2+ not elegant but it works

---

### Post by patwack on 2006-08-22
there's an option somewhere in synaptic to pin the program at a specific version, that would work i think

---

### Post by Christmas on 2006-08-22
Do you have a shell command for that? (I'm using Kubuntu)

---

