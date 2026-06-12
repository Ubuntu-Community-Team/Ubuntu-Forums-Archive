---
title: "OpenOffice.org crashing on startup"
date: 2007-02-15
forum: General Help
---

### Post by wylfing on 2007-02-15
I am not generally a big office suite user, so this problem hasn't been bothering me too much, but I would really like to get it fixed for the rare time that I do need to look at a presentation or some such. What happens is that OpenOffice.org crashes at startup with the following message:
```
WARNING **: Unknown error forking main binary / abnormal early exit
```
I did some Googling on the subject, and there are a number of things out there claiming to have "solved" this problem, but they always amount to voodoo ("Dude, I renamed one of my fonts and the problem went away!"), and they are always different, and none of them seem to have anything to do with my setup.

My own troubleshooting attempts involved the following:
[LIST]
[*]Deleting .openoffice.org2 (didn't help)
[*]Reinstalling java (didn't help)
[*]Making sure Sun's JRE is installed, not GCJ (didn't help)
[*]Checking that java programs work (they do)
[*]Checking that OpenGL works (it does)
[*]Reinstalling Openoffice.org (didn't help)
[/LIST]

This issue started when I upgraded from Dapper to Edgy. Now, presumably there are plenty of people running Edgy with OpenOffice.org running fine. I just wonder if there is anyone who has experienced a similar problem.

Edit:

This thread: [http://ubuntuforums.org/showthread.php?t=293081]("http://ubuntuforums.org/showthread.php?t=293081") did not help either.

---

### Post by Maestro23 on 2007-02-15
Hmm... I'm running the full OpenOffice suite on Xubuntu Edgy 6.10 with no problems.  This is on a fresh install of Edgy.

Perhaps the upgrade was not a smooth one from Dapper to Edgy.  Are you seeing any other problems with the system or other programs?

*Have you checked over at the OpenOffice Setup & Troubleshooting forums searching for that error?  If you already have, disregard.  I did see some over there discussing that error  though.

---

### Post by wylfing on 2007-02-15
I haven't done a fresh install since Warty. The move from Dapper to Edgy was certainly a little more problematic than the other upgrades, but I've been able to solve 99% of the problems by doing logical troubleshooting. I am certainly willing to accept that I need to do a wipe and clean install at some point. If possible I would rather solve the problem rather than throw up my hands and declare the whole thing broken.

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

