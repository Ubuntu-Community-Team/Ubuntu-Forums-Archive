---
title: "ubuntu tweak wont launch, uninstall or reinstall getting frustrated"
date: 2013-11-12
forum: General Help
---

### Post by crazymonkey05 on 2013-11-12
well ive tried everything guys and my ubuntu tweak app is just broken. when it starts i get the splash logo then it closes.
when i go to uninstall i get this ```
E: ubuntu-tweak: unable to securely remove '/usr/lib/python2.7/dist-packages/ubuntutweak/settings/compizsettings.py': Not a directory
``` and when i reinstall i get this ```
Removing ubuntu-tweak ...dpkg: error processing ubuntu-tweak (--remove):
 unable to securely remove '/usr/lib/python2.7/dist-packages/ubuntutweak/settings/compizsettings.py': Not a directory
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 ubuntu-tweak
Error in function: 



``` any help is appriciated, thanks

---

### Post by fantab on 2013-11-12
Try

```
sudo -i
dpkg --purge ubuntu-tweak
apt-get remove --purge ubuntu-tweak
apt-get clean
apt-get autoremove
apt-get update
apt-get upgrade
apt-get install ubuntu-tweak
exit
```

Make sure 'ubuntu-tweak' is the correct name, if its not then use the correct name.

---

### Post by crazymonkey05 on 2013-11-13
ok so i did as you said and it got to the second command ```
[COLOR=#000000][FONT=Ubuntu Mono]dpkg --purge ubuntu-tweak[/FONT][/COLOR]
``` and the return output was this: 
```
root@ricky-945G-M3:~# dpkg --purge ubuntu-tweak
(Reading database ... 212313 files and directories currently installed.)
Removing ubuntu-tweak ...
dpkg: error processing ubuntu-tweak (--purge):
 unable to securely remove '/usr/lib/python2.7/dist-packages/ubuntutweak/settings/compizsettings.py': Not a directory
Errors were encountered while processing:
 ubuntu-tweak



```

---

### Post by fantab on 2013-11-13
> No apport report written because MaxReports is reached already

You may not have enough disk space, post the output of:
```
df -h
```

I suspect you may have accumulated unused and older kernels. If that is the case, then remove unused kernels with Synaptic Package manager, if you have it installed or:
```
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

EDIT: Before you run the above command make sure you are booting with the latest kernel. 
Check with:
```
uname -r
```


> dpkg: error processing ubuntu-tweak (--purge):
 unable to securely remove '/usr/lib/python2.7/dist-packages/ubuntutweak/settings/compizsettings.py': Not a directory

Remove it manually:
Open Nautilus as root, navigate yourslef to '/usr/lib/python2.7/dist-packages' find an delete 'ubuntutweak'.

---

### Post by crazymonkey05 on 2013-11-15
thanks so much i removed the files manually and then removed all links with Synapse now i have it re-installed and fully functional, thanks again ill mark it as solved

---

