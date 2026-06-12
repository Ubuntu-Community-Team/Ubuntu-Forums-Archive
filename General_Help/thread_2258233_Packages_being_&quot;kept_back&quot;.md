---
title: "Packages being &quot;kept back&quot;"
date: 2014-12-25
forum: General Help
---

### Post by emanmcdow on 2014-12-25
For as long as I've had  Ubuntu(about a year), I've ignored the message that "the following packages have been kept back" when I upgrade. I didn't really think it mattered. Recently however, I have been trying to "tune up" my system, upgrading things, removing things that need to be removed, and in general optimizing my Ubuntu installation. This message stuck out to me. I looked into it, and I felt like an idiot for never checking it out. I understand the whole dist-upgrade as opposed to upgrade thing now. So I run sudo apt-get update and sudo apt-get dist-upgrade and several of the packages leave the list that have been "kept back". I run sudo apt-get dist-upgrade again and it tells me that a single package is being kept back.  What's happening here? I thought dist-upgrade is supposed to fix this?

```

emmett@jarvis:~$ sudo apt-get dist-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  indicator-synapse
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by Bashing-om on 2014-12-25
emanmcdow; hummm ...

3rd party software - indicator-synapse - ??
As:
> 
Ubuntu » Packages » Package Search Results
You have searched for packages that names contain indicator-synapse in suite(s) precise-updates, all sections, and all architectures.

Sorry, your search gave no results
&&
You have searched for packages that names contain indicator-synapse in suite(s) trusty, all sections, and all architectures.

Sorry, your search gave no results
&&

sysop@1404mini:~$ apt-cache show indicator-synapse
N: Unable to locate package indicator-synapse
E: No packages found


Maybe a PPA that is not maintained ?

[INDENT][INDENT]eliminated, and what remains
[INDENT][INDENT][INDENT][INDENT]must be the truth
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by emanmcdow on 2014-12-25
So it appears that I didn't have a ppa for indicator-synapse, and since I don't use it anymore, I just uninstalled it. Fixed it. Thanks Bashing-om! Btw I like what you did with that quote, I see what you did there.

---

### Post by Bashing-om on 2014-12-25
emanmcdow; Great !

All's well that end well. Pleased all worked out.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[if ya hang around the forum long 'nuff, we teach ya lots of neat tricks]

[INDENT][INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

