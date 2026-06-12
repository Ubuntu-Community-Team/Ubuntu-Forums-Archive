---
title: "Ubuntu fails to log in after laptop accidentally ran out of power"
date: 2018-03-08
forum: General Help
---

### Post by lightice1 on 2018-03-08
Basically, I wanted to test various security software on my laptop. I left sfill running and went out, but accidentally forgot to plug the laptop in. Now, after restarting, I find that I can no longer log in to either of my main users. When I enter my password, the screen just goes black and then returns back to the login screen. I can enter as a Guest, but I naturally can't do anything about the situation. I think that this might have something to do with the hard drive being now completely full of junk data, due to unfinished sfill run, but I'm not sure, nor do I know how to do anything about it.

EDIT: 
For additional problems, my user folder is encrypted, so accessing it from outside the operating system doesn't seem to be possible; I would be interested if it would be possible to at least access its bash via Windows 10, somehow, since I have it installed on the same computer. And would it solve the problem or ruin the partition if I expanded it by a gigabyte via Windows?

---

### Post by dragonfly41 on 2018-03-08
I have dual boot Windows 10 + 16.04 which I assume you have,
> [COLOR=#000000]since I have it installed on the same computer[/COLOR]

Encryption is an added complication. I do not encrypt.

On occasions I have installed R-Linux on Windows and used that to access the Ubuntu ext4 partition.
You could try that to jettison any Ubuntu junk files if you cannot use a Ubuntu LiveUSB (the preferred choice).
You might consider cloning your screwed up Ubuntu onto another drive as a backup.

P.S. I would not try any resizing of partition at this stage.

---

### Post by lightice1 on 2018-03-09
I have tried eliminating junk files, but the one partition on which the users are seems to be impervious; it remains filled to the brim. and it seems that I can't access it in any manner.

---

### Post by lightice1 on 2018-03-09
OK, I was able to solve the problem, albeit in  very crude manner. I went into recovery mode and used command line as the root user, and used the command "mount -a" to make modifications possible. Then I simply deleted a less important secondary user that I fortunately had on the drive, along with its home folder, which released enough space from the right partition to make logging in possible. 

So, I guess the solution is "always keep a backup user that you're willing to sacrifice". Not what I'd consider a good solution, but it was fortunately one that worked.

---

