---
title: "apt update not finding archives"
date: 2020-01-20
forum: General Help
---

### Post by cearlp2 on 2020-01-20
Trying to do a sudo apt update fails with several fetch failures.
All state that they couldn't resolve 'us.archive.ubuntu.com' or 'security.ubuntu.com'.
What do I need to do to resolve this situation?

---

### Post by Bashing-om on 2020-01-20
cearlp2; Hello

A lot more info - to help you:)

What release is this ?
Please post the results from terminal commands:
```

lsb_release -a
sudo apt update
sudo apt full-upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Where maybe your install no longer has support ?

[INDENT][INDENT]possible
[/INDENT][/INDENT]

---

### Post by cearlp on 2020-01-20
As requested:
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic

Yikes! Now when I redid the sudo apt update it works!
So I won't do a sudo apt full-upgrade.

I  did have to do a restart since the failures,, that probably did it.

---

### Post by Bashing-om on 2020-01-20
cearlp; Great :D

But do - do the "full-upgrade".
All that command does is deal with "updates" to the system that "apt update"  will not ( think held packages).

[INDENT]no one is happy
[INDENT][INDENT]unless the package manager is happy[/INDENT][/INDENT][/INDENT]

---

### Post by cearlp2 on 2020-01-21
Thanks for the full-upgrade info.

---

### Post by Bashing-om on 2020-01-21
cearlp2; Hey hey :)

If "upgrade" runs with no errors, we can conclude the issue is resolved.
If so:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

