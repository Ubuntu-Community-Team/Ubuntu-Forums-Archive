---
title: "Primus Broken after update"
date: 2013-04-25
forum: General Help
---

### Post by bonzodog on 2013-04-25
I have an Acer V5 571G with Optimus.

I added the bumblebee PPA as advised, then installed Bumblebee and Primus.

It was all working fine until an update yesterday.

My games will run with Optirun, but not with Primusrun.

When I run primusrun, I get the following error:

```

[10:14]-[pts/2]-[/home/bonzodog/regnum]
:primusrun ./rolauncher      
primus: fatal: failed to load any of the libraries: /usr/lib/nvidia-current/libGL.so.1:/usr/lib32/nvidia-current/libGL.so.1
libnvidia-tls.so.304.88: cannot open shared object file: No such file or directory
/usr/lib32/nvidia-current/libGL.so.1: wrong ELF class: ELFCLASS32
[1]    3283 exit 1     primusrun ./rolauncher

```

Now, i am fairly good with linux and ubuntu, and have researched this error on the web. It seems to suggest that a line needs editing in /usr/bin/primusrun, but I am not sure which one.

I have the nvidia-current drivers installed.

---

### Post by panthertehcat on 2013-04-25
Same problem here, any luck?

Ubuntu/Kubuntu: 12:10
Nvidia 610m
ASUS K53S

```
primusrun glxspheresprimus: fatal: failed to load any of the libraries: /usr/lib/nvidia-current/libGL.so.1:/usr/lib32/nvidia-current/libGL.so.1
libnvidia-tls.so.304.88: cannot open shared object file: No such file or directory
/usr/lib32/nvidia-current/libGL.so.1: wrong ELF class: ELFCLASS32



```

---

### Post by dcu on 2013-04-25
Same problem - tried linking some (more or less random) files to the missing file but was not able to get it running yet.
First appeared yesterday after updating primus via Bumblebee repository. Did not find anything related until now.
Optirun still works though.

TP-E530 with Nvidia630M running Xubuntu

---

### Post by panthertehcat on 2013-04-25
The strange thing is optirun -b primus works, which makes me agree with Bonzodog it is the script. However I have no idea what to edit. I require the Primusrun command for steam.

---

### Post by bonzodog on 2013-04-26
Ok, not sure whether to mark this as solved, but it appears that there is breakage in the package, and the Primus devs have confirmed it on IRC.

[http://askubuntu.com/questions/285885/primus-failed-to-load-libraries-in-raring](http://askubuntu.com/questions/285885/primus-failed-to-load-libraries-in-raring)

So, this applies to 12.10 AND 13.04.

---

### Post by panthertehcat on 2013-04-27
Checked for updates today and there was a Optirun and Primus update that seems to have resolved the issues. Hopefully they fix yours as well.

---

### Post by bonzodog on 2013-04-28
Yes, can confirm fixed with update.

---

### Post by Rexhunter99 on 2013-05-26
> **bonzodog said:**
> Yes, can confirm fixed with update.
I'm here to disconfirm that, the update broke my primus, I can't even run with the bridge command via optirun.  Tried removing+purging then installing fresh, still no go.  Not happy with 13.04 as a whole, so many issues with drivers on hybrid systems or systems with dual graphics such as my gaming desktop.  Can't go back to 12.x though because that's broken to hell.

Using an ACER V3-571G
Intel i5 3210M
NVIDIA GT 630M with Intel HD 4000 IGD

Initially what happened was I got the new update for primus via the software package updater, since its in the Ubuntu updates... I thought why not? After hitting install, all hell broke loose, package system broke and I was forced to rectify the issue manually by removing the broken package in question "primus"
Attempting to reinstall the update after the broken package was removed resulted in all the primus libs being installed A-Okay but no Primus binaries or interface.
This frustration is enough to drive me back to Windows, seriously and the only time I boot into Windows is for working on a Windows Domain, testing windows specific code or to play AAA games on Steam on my desktop.  Most of my development and leisure is in Ubuntu.

---

