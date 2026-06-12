---
title: "What folders to back up?"
date: 2013-07-10
forum: General Help
---

### Post by cforput on 2013-07-10
I've done some searching on the forums but don't see to see an answer to what I think is an easy question.

I need to rebuild my system with the same version so I want / need to back up my data and configuration to an external drive. If I backup only my home folder, is that all I need? I want to reinstall the apps in a controlled manner so I don't want to back them up. Just my data, Firefox bookmarks, and other stuff that might not readily be found where I store my data files. If it matters, I also use Cinnamon. 

As a second question, is there a way to get a list of all extra programs I installed over the base 13.10 which I'm on now?

---

### Post by buzzingrobot on 2013-07-10
Logically, you'd want to back up any directory you have changed.  The most obvious is your /home directory. If you have added or edited files in /etc, then those need backing up. If, for instance, you've tweaked grub's configuration, then those files ought to be backed up in case you forget what you did or how you did it. 

You may have installed software that populated the /opt or /usr/local directory trees.

Executing this in a terminal -- "sudo dpkg --get-selections | grep -v deinstall > SomeFile" -- will get you a list of everything on your machine that was installed with apt or dpkg.  It won't include anything you've built and/or installed independent of those tools.

---

### Post by oldfred on 2013-07-10
I posted here some info, and it still is what I do for backups. My backups are to let me do a new clean reinstall and restore my data.

 Oldfred's list of stuff to backup May 2011:
[URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541

[/URL] Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)


 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by Habitual on 2013-07-10
I use 
```
cd ~
rsync -avz --no-perms . /run/media/jj/Keepers --exclude "/home/jj.gvfs" --exclude ".cache/" --exclude "VirtualBox VMs/"  --delete
```

in a script myself.

---

### Post by BBQdave on 2013-07-10
I back up data monthly to a home server, and weekly - or more often, depending on the projects I am working on - to an external hard drive.

I have a list of applications I use. So fresh install, check applications of new install with my list - and add applications. Copy data to new install from my external hard drive.

And cruise on until the LTS reaches EOL :D

---

