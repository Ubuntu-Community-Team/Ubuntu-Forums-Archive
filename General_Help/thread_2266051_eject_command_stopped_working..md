---
title: "eject command stopped working."
date: 2015-02-19
forum: General Help
---

### Post by northwestern on 2015-02-19
At the moment I am running ubuntu 14.04 on a Samsung laptop (sole os). Whenever I first install Ubuntu (or Mint) the eject command and disc drive recognition both work, however as soon as I update or install new software I seem to lose the ability to eject the disc using the "eject" command in the terminal, also if I open my disk drive manually and insert a disc nothing happens so I am unable to play dvds or cds. I have googled the problem but nothing seems to cure it.

Regard.
Northwestern

---

### Post by ajgreeny on 2015-02-19
There is thread I have replied to at [http://ubuntuforums.org/showthread.php?t=2265555](http://ubuntuforums.org/showthread.php?t=2265555) which sounds a bit similar to your problem.
Have a look there and try some of my suggestions to see if it really is the same problem.

---

### Post by northwestern on 2015-02-21
Thank you for your reply.
I have looked at the threads that you suggested, but I am still at a loss in getting the reject command to work and a disc to be accepted.

Regard.
Northwestern

---

### Post by HermanAB on 2015-02-21
Howdy,

It is hard to tell why a process on another machine on the other side of the world, that you cannot see or touch is not working.

Some things to explore:

Does it sometimes work, or never work?
Is there a CD/DVD in the drive, or is it empty now?
If you power down and back up (without a CD in the drive) does it then work when you insert one?

The mount command can tell you whether the cdrom is mounted or not.
The umount command is equivalent to the eject command.
If a process is using the mount, then it won't unmount until that process is stopped.
You can tell which files are open and possibly holding the CD with lsof.

---

