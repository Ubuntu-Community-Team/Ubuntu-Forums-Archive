---
title: "Resolving broken dependencies (noob question)"
date: 2017-05-27
forum: General Help
---

### Post by rannalla31 on 2017-05-27
Hi I'm kind of a newbie.  I think I tried installing one program or another over the past few weeks (which one I'm not sure) and now have some unresolved dependencies that I would like to resolve -- because there now seems to be a problem updating my system in general.

The problem seems to be broken dependencies in these three packages: 

linux-image-extra-4.8.0-53-generic ,
linux-image-generic-hwe-16.04 , 
and linux-signed-image-4.8.0-53-generic .

Is there a way to use apt-get or Synaptic's package manager (which has options with a right-click to "Mark for reinstallation", "mark for removal" or "mark for complete removal") to redress whatever the problem is and get my computer happily updating in general again -- instead of hitting a roadblock and showing some sort of flag in the top corner of the screen?

Thanks in advance for any suggestions.

[I'm running ubuntu 16.04 LTS with a 64-bit OS]

---

### Post by QIII on 2017-05-27
Moved to General Help for a betted fit.

Installation & Upgrades is for the OS/release.

---

### Post by Bashing-om on 2017-05-27
rannalla31; Hello; Welcome to the form.

Are you running short of disk space in /boot ?
Post back - Between code tags - the output of terminal commands:
```

df -i
df -h

```

And also show us the errors you see:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we see what there is to be done and come up with a plan to cope .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by rannalla31 on 2017-05-27
I think the issue has been resolved... (after typing up a long description in response of what I was encountering) it occurred to me that one of the messages was telling me to run "sudo apt-get upgrade -f"  (with the "f" option) That fuller upgrade finally seems to have resolved the dependency issue.(Another problem I encountered was I left the Synaptic Package Manager gui open and that was conflicting with apt and apt-get because it had a lock in place on the interface file.)

I guess I also want to a deeper dive at some point in figuring out how to uninstall packages that I started looking at but which didn't seem to interface well when I tried incorporating them in the last month or two (when I started using ubuntu).  I guess the "man apt" and "man apt-get" commands  would be the natural places to start. (?)

Thanks so much for the help.

---

### Post by Bashing-om on 2017-05-27
rannalla31; Hey ...

Glad ya got it going your way.

Package management:
If ya learn this:
[https://www.debian.org/doc/manuals/debian-reference/ch02.en.html](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html)
You are well on your way as a systems administrator.

As the issue is t an end:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]docs
[INDENT][INDENT][INDENT]just gimme the docs
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rannalla31 on 2017-05-27
Awesome thanks for the link... I bookmarked it (after glancing at it) to work through it later

---

