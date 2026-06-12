---
title: "[URGENT]How do I force maintenance shell?"
date: 2008-01-16
forum: General Help
---

### Post by kthxbai2u on 2008-01-16
Im looking for a way to force the maintenance shell to open... You know, this one: 

```
Give root password for maintenance or press control-D to continue.
```

I'm stuck at the "rc-default terminated with status 127" thing that is posted [http://ubuntuforums.org/showthread.php?t=330463 (here)]("http://ubuntuforums.org/showthread.php?t=330463").

The only way I have got this (which i cannot reproduce for some reason) is by pressing ctrl+alt+del . It would then say something about the system reached a state  with no running processes and then request root password for recovery console.

Now, everytime I try to get back to the maintenance shell by pressing ctrl+alt+del, it just reboots O_o

I need this maintenance shell untill I get the rc-default problem solved. From this mainenance shell I WAS able to start the SSH and APACHE2 processes.

I wish to do this again but cant get back to the maintenance shell. HURRY, my site is offline :'(

---

### Post by geirha on 2008-01-16
ctrl+alt+del just reboots the system, but do reboot. When you get to the grub menu, it will wait some seconds before choosing the default option, if the menu is hidden, hit ESC to show it, then select the second (usually) entry, which is the recovery option. This should get you into single-user mode.

---

### Post by kthxbai2u on 2008-01-16
nope... I mentioned either in this thread or the other one that I get the rc-default terminated with status 127 on both regular boot and when using "recovery mode" in the grub menu... Somehow when it was in that state either I triggered it (ctrl+alt+del is all i pressed) or the system triggered it. There must be a way to get into the **maintenance console** manually? this is not the same as recovery mode but if I could get into either, they both would load the services thus putting the web server back online temporarily untill i resolve the status 127 issue (or just reinstall everything - which I dont want to do)

[EDIT] is there a way to boot off the live cd but start the apache2 and ssh processes that would run on my webserver install (hda) ? All I need to do is get my server back online... I dont care if it still shows the status 127 error or if kdm/gdm dont load... [/EDIT]

---

### Post by geirha on 2008-01-16
Yes, you could try booting off the ubuntu cd, then mount your / partition as /media/disk, and any /home or /usr partition you might have as /media/disk/home or /media/disk/usr respectively. Then open a terminal and type ```
sudo chroot /media/disk
``` and try to start ssh and apache2 there. Not sure if that will work as expected, but it's worth a try

EDIT: as for the 127 exit status, 127 usually means the shell is trying to run a command it can't find. Possibly /sbin/telinit. When your ubuntu CD is running, check if that file exists and that it is executable.

---

### Post by kthxbai2u on 2008-01-16
Well, I learned a new command, thank you! ERrm telinit is not there... How do i get it there? Does it have to be there to boot properly? Where can i get a copy of this file?

---

### Post by geirha on 2008-01-16
telinit is installed by the package upstart-compat-sysv

So try to install that package inside the chroot: ```
sudo aptitude install upstart-compat-sysv
```

EDIT: And yes, it must be there in order to boot properly

---

