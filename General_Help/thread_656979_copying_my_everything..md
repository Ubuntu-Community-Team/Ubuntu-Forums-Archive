---
title: "copying my everything."
date: 2008-01-03
forum: General Help
---

### Post by The AlGorenator on 2008-01-03
If i copy the contents of '/ ' onto a fresh install of ubuntu over it's shiny new copy of '/ ' will i get a pc in the exact same state as my current one?

did that make sense?

---

### Post by kpkeerthi on 2008-01-03
Yes. But your new pc won't work if its hardware specs does not "exactly" match the one you copied the files from. You would have to reconfigure or edit atleast xorg.conf, fstab and menu.lst to get the new PC working.

---

### Post by niethslim on 2008-01-03
Your private data is stored in your /home folder.
 I'm not sure if copying / will copy /home as well, especially if it is stored on a separate partition.

---

### Post by erfahren on 2008-01-03
here's some forum threads on different ways to back up
[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)
[http://ubuntuforums.org/showthread.php?t=80790](http://ubuntuforums.org/showthread.php?t=80790)
[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)
[http://ubuntuforums.org/showthread.php?t=511471](http://ubuntuforums.org/showthread.php?t=511471)

[http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

actually, copying / would copy /home whether it's on a seperate partition or not. You'd copy any mounted partition. you can make a compressed archive of your entire filesystem as well (the first link covers that). You have to set it to ignore the achive your creating though, because otherwise you'd be archiving the archive you're creating!

Actually, one thing you can do to make reinstalling faster is copy the packages you've downloaded through Synaptic, Add/Remove, or apt. Unless you clear the cache, they are kept in /var/cache/apt/archives.

you can just copy the packages as a regular user and put them somewhere, then after reinstalling use "sudo nautilus" to open the file browser as root (be careful!) and put them back in that directory. Then when you go to reinstall the programs, apt will get them from there unless there are updated versions availabe.

Another trick is to make a list of the *package names* of the programs you typically install. Then in the terminal just do "sudo aptitude install" and paste in your list. (Read up on [aptitude](https://help.ubuntu.com/community/AptitudeSurvivalGuide), it's a little different then [apt](https://help.ubuntu.com/community/AptGetHowto). )

You only need to list the packages that are main ones and let aptitude pull in the dependencies (like you just need to list "sun-java6-plugin" to get the browser plugin and everthing else comes with it.

( [Synaptic Package Manager](https://help.ubuntu.com/community/SynapticHowto) is a frontend for apt, and Add/Remove is just basically a simplified version of Synaptic.)

- Much more info than you asked for, but I thought I'd share those.

---

### Post by megamania on 2008-01-03
> **The AlGorenator said:**
> If i copy the contents of '/ ' onto a fresh install of ubuntu over it's shiny new copy of '/ ' will i get a pc in the exact same state as my current one?

did that make sense?
Assuming you're using the same computer, in my opinion you would end up with a working system, but with more files than your back-up install. For example, if in your back-up copy you had uninstalled the program Gedit, after copying over you would have that program on your hard disk (i.e. taking up space), but not installed. Hope that's clear...

To have an exaxt copy, you should delete the files that are not needed anymore.

Rsync would do the job fairly easily.

---

