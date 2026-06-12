---
title: "Trouble with Wine Beta"
date: 2005-10-28
forum: General Help
---

### Post by quazi on 2005-10-28
I previously installed the most recent version of wine in the repositories and had it configured on another user (not mine).  I added the repositores for the new version of wine and did a sudo apt-get install wine, which I believe went well.  I type in "wine" and get this lovely message:
```
chris@serpent:~$ wine
wine: creating configuration directory '/home/chris/.wine'...
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x24
  Serial number of failed request:  130
  Current serial number in output stream:  131
wine: wineprefixcreate failed while creating '/home/chris/.wine'.
chris@serpent:~$ wineserver: could not save registry branch to /home/chris/.wine-ublZO6/system.reg : No such file or directory
wineserver: could not save registry branch to /home/chris/.wine-ublZO6/user.reg : No such file or directory

```

If I create the .wine directory, wine will run but it won't have any configuration files, and winecfg is not working.  I have libsdc++6 or whatever installed already, is there something that I'm doin wrong?

---

### Post by quazi on 2005-10-30
I guess I'll just try uninstalling wine and then reinstalling it to see if that fixes the problem (although I'm fairly confident it won't).

---

### Post by NewbieNik on 2005-10-30
[QUOTE=quazi]I guess I'll just try uninstalling wine and then reinstalling it to see if that fixes the problem (although I'm fairly confident it won't).[/QUOTE]


try running an "apt-get -f install" to fix broken packages. I ran the apt-get install wine on my Breezy and it seems to run fine, so far...Wait until I try a microsoft product!!!

---

