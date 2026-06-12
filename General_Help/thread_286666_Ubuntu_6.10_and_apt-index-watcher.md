---
title: "Ubuntu 6.10 and apt-index-watcher"
date: 2006-10-28
forum: General Help
---

### Post by Mednafen on 2006-10-28
I'm having problems with apt-index-watcher eating up a significant amount of CPU time every few seconds, which is causing problems for my emulator, Mednafen, such as stuttering and dropped frames, which is very annoying.  I imagine it could cause problems with other emulators(Mednafen is a little more sensitive to this kind of thing from my experience, though), games, and some real-time audio applications.  (killall -9 apt-index-watcher "fixed" the problem, but it's obviously not a real solution)

This problem didn't exist for me in 6.06, and only occurred after upgrading to 6.10.

Looking at the man page, the whole concept of apt-index-watcher seems kind of half-baked, like polling instead of using interrupts. ;)

---

### Post by lqyjzmms on 2006-10-31
The topic had already been covered in this topic before edgy's release:

[http://www.ubuntuforums.org/showthread.php?t=217277](http://www.ubuntuforums.org/showthread.php?t=217277)

The issue seemed to have been resolved, but apparently it is still existing, I can confirm similar problems even with the latest packages.

---

### Post by imagine on 2006-11-08
apt-index-watcher is not part of a default Ubuntu 6.10 installation. So due to its non-existance it cannot cause any CPU spikes : )

It probably got on your system because you upgraded. To get rid of it:
```
sudo apt-get remove --purge apt-index-watcher
```

---

### Post by lqyjzmms on 2006-11-11
But it is part of a Kubuntu 6.10 default installation. If you remove apt-index-watcher, Adept will be removed as well. And Adept is the default package manager in Kubuntu, so beware.

---

### Post by Kosmonaut on 2006-11-22
Hi!

Got the same problem with that nasty "apt-index-watcher". Because the purging of "apt-index-watcher" will deinstall adept and its related packages, I wondering how to stop "apt-index-watcher" while the system boots-up.

What I do now is:  > sudo /etc/init.d/apt-index-watcher stop
But how do I automatise this command at the start of my system, for every user?

Grüsse.

PS: As allway sorry for my english #-o

---

### Post by Kosmonaut on 2006-11-29
Here is the answer to my own question:
> chmod -x /etc/init.d/apt-index-watcher
does the job.

Don't know if this method is sane, but I don't care, as long as my Cpu+fan stop heating my room :rolleyes:

---

### Post by skaboss on 2006-12-29
I had the same problem too, with apt-index-watcher, and definitely disabled it with
```
sudo update-rc.d -f apt-index-watcher remove
```
It did the trick, and it seems saner than your solution, Kosmonaut  ;)

---

### Post by floke on 2007-02-07
I had this nasty little thing too, have just tried the above so hopefully have killed it for good!e
Cheers

---

