---
title: "Help! Can't seem to recover Samba shell scripts"
date: 2006-11-21
forum: General Help
---

### Post by AndRom6 on 2006-11-21
Hello,

Let me preface by saying I am running Ubuntu 6.10 Edgy and that prior to this incident my samba client and server daemons were running just fine:

I was attempting to modify my /etc/init.d/samba shell script, primarily because for reasons I don't understand after doing some smb.conf tweaking a sudo /etc/init.d/samba start would fail. I did this using gedit, and upon saving with gedit I was presented with a mysterious libgnomevfs2 error and my system refused to acknowledge it as shell script anymore (saying "samba is not a command"), also my samba shell script was in black on an ls in console when all others were green. I tried and I struggled, but I eventually resolved to remove it and attempt to reinstall all the samba, smbclient, etc. stuff from the repositories in the hopes that it would replace the shell script. No dice.

For reasons I further won't get into my shell scripts in /etc/rc2.d and /etc/rc3.d are also gone.

Please help, how do I replace these precious scripts and get my Samba back to action?

---

### Post by Ensnared on 2006-11-21
Seems like the permissions were reset on the script for some reason (might be gedit's fault, I wouldn't know).

If that's the case, you can just fix it by doing:```
sudo chmod +x /etc/init.d/samba
```...followed by the usual...```
sudo /etc/init.d/samba start
```

If you've deleted the script, it should be replaced by reinstalling the package it's in. I'm not sure which one that is, but you can try to find out by creating a new dummy file with the proper name, and then do this:```
dpkg -S /etc/init.d/samba
```...which should tell you which package owns the file. You can then remove the dummy file and reinstall the package:```
sudo apt-get install --reinstall <package>
```

---

### Post by AndRom6 on 2006-11-21
dpkg -S /etc/init.d/samba said Samba

sudo apt-get install --reinstall Samba failed to replace shell scripts.

I am now more confused than ever.

---

### Post by GXP on 2007-02-10
AndRom6 - Did you ever get Samba scripts back? I had a similar problem, right from the start on a fresh install of Edgy and Samba. I was able to get the scripts back by executing the following:

sudo dpkg -P samba samba-common

This removed the configuration files allowing the reinstall to replace the files.

---

