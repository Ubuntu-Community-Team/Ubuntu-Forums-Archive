---
title: "[SOLVED] Help! I can't start nautilus as root :("
date: 2008-06-15
forum: General Help
---

### Post by lennartack on 2008-06-15
Hi,

I just installed hardy, and can't open nautilus as root anymore. I'm using my old home folder of gutsy. Removing my old .nautilus doesn't help.

The problem is very simple: nautilus doesn't open as root whatever I do.
```
lennart@lennart:~$ gksu nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension
lennart@lennart:~$ 
```
```
lennart@lennart:~$ sudo nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension
seahorse nautilus module initialized
Segmentation fault
lennart@lennart:~$ 
```

I just remembered using dbus-launch ("sudo dbus-launch nautilus") could solve things like this. I don't know when I used is before and what it does, but it works! However, I still think I need to be able do it the gksu way. Please help me :P

Thanks,
Lennart

---

### Post by todak on 2008-06-15
The correct command is ```
gksudo nautilus
```
Note the sudo! :)

---

### Post by aysiu on 2008-06-15
It shouldn't make a difference. *gksudo* is just a symlink to *gksu* anyway. They're the same command.

I don't know what "a repair of packages" means exactly, but [this](http://ubuntuforums.org/showpost.php?p=5191881&postcount=40) is the closest I've seen to a solution of the segmentation fault problem.

---

### Post by lennartack on 2008-06-16
> **aysiu said:**
> 
I don't know what "a repair of packages" means exactly, but [this](http://ubuntuforums.org/showpost.php?p=5191881&postcount=40) is the closest I've seen to a solution of the segmentation fault problem.
There are no broken packages, so I don't think a can repair anything ;).

I have segmentation faults quite often btw (especially in games). What does it mean? It's quite irritating..

---

### Post by manfer on 2008-06-16
[Segmention Fault on wikipedia]("http://en.wikipedia.org/wiki/Segmentation_fault")

A segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (for example, attempting to write to a read-only location, or to overwrite part of the operating system).

I had a segmentation fault on the program gyachi when i run it as normal user and it was for wrong config files for a previous installation. It was solved removing the directory .yahoorc/ (directory where gyachi config files are stored) from home directory of user.

Your problem could be the same but i'm not totally sure and it is on root user so you may act with caution. What I would do is make a backup of /root/.nautilus (config for nautilus on root user) then delete that directory /root/.nautilus and try running nautilus as root again. I suppose this would regenerate the /root/.nautilus and maybe would solve the problem.

But i'm not sure and would be nice if someone could confirm this. If the problem persists you should restore the backup you made of /root/.nautilus directory to try some other solution.

---

### Post by lennartack on 2008-06-17
> **manfer said:**
> What I would do is make a backup of /root/.nautilus (config for nautilus on root user) then delete that directory /root/.nautilus and try running nautilus as root again. I suppose this would regenerate the /root/.nautilus and maybe would solve the problem.
Nothing :(. It should not work anyway because the problem was already there JUST after I had installed ubuntu 8.04, and then there is no .nautilus directory yet.

---

### Post by manfer on 2008-06-17
Then it gives you that segmentation fault even the first time you tried to run it as root and no .nautilus directory is made in /root filesystem.

Have you installed any nautilus add-on? (nautilus-image-converter, nautilus-open-terminal...) If so uninstall them and try running nautilus again.

If that is not the case, what about a reinstallation of nautilus?, had you tried it?

From Synaptic package manager:
open Synaptic, make a search for nautilus, mark it for reinstall and aply changes.

Or from terminal:
sudo apt-get --reinstall install nautilus

---

### Post by lennartack on 2008-06-19
> **manfer said:**
> 
If that is not the case, what about a reinstallation of nautilus?, had you tried it?
YEAH IT WORKS :D Thank you!

---

### Post by kennedyjch on 2008-09-30
I tried the remove/install of nautilus and it did not solve my segmentation fault problem. However, I did come across web posting that this can happen with blank CD in the drive. I checked and sure enough I had a blank CD in the drive. Once taken out the segmentation fault goes away.

---

### Post by oldos2er on 2008-09-30
> **kennedyjch said:**
> I tried the remove/install of nautilus and it did not solve my segmentation fault problem. However, I did come across web posting that this can happen with blank CD in the drive. I checked and sure enough I had a blank CD in the drive. Once taken out the segmentation fault goes away.

 That should be reported as a bug.

---

### Post by drs305 on 2008-10-07
> **kennedyjch said:**
> I tried the remove/install of nautilus and it did not solve my segmentation fault problem. However, I did come across web posting that this can happen with blank CD in the drive. I checked and sure enough I had a blank CD in the drive. Once taken out the segmentation fault goes away.

I just tried and was able to duplicate your problem. With a blank CD/DVD inserted, when I ran "gksudo nautilus" I got this error message:
```
seahorse nautilus module initialized
```
and then nothing.

When I removed the blank cd/dvd, the command worked and a nautilus window opened.

---

