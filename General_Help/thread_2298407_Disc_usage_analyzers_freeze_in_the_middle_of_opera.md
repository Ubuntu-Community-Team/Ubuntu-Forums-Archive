---
title: "Disc usage analyzers freeze in the middle of operation"
date: 2015-10-10
forum: General Help
---

### Post by Fiksdal on 2015-10-10
[COLOR=#111111][FONT=Ubuntu]14.04
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've been trying not just Baobab that came bundled, but also K4dirstat, Filelight and JDiskReport. [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I have even tried running Windirstat under Wine![/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] They all start working, then freeze about halfway through the process.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Any advice?[/FONT][/COLOR]

---

### Post by v3.xx on 2015-10-10
> Only issue I have had is when it first finishes scanning a directory tree [and this can take a good amount of time ESPECIALLY IF YOU DON'T GKSU it takes longer to get around the errors it gets when trying to read directories your user does not have permissions for, so be patient and don't just exit it after a few seconds]

[https://help.ubuntu.com/community/Baobab#Using_Baobab_.28Disk_Usage_Analyzer.29-1](https://help.ubuntu.com/community/Baobab#Using_Baobab_.28Disk_Usage_Analyzer.29-1)

Maybe you have a older (slower) machine

---

### Post by Fiksdal on 2015-10-11
I bought my machine last year. It's a Dell Vostro 3345. Not the fastest, but not too slow either.

But yeah, maybe I should start the scan and let it be for a few hours, even if it appears to freeze.

---

### Post by Fiksdal on 2015-10-11
I booted into Windows and did a check and repair of the disks. After that, some of the tools, like Filelight and GD Map, work.

---

### Post by Fiksdal on 2015-10-11
Baobab works too. Even if they went gray and unresponsive for a long time, I just waited through it, and then the scan continued. Maybe all of them would have worked from the very start, if I had been more patient and letting them wait through the gray frozen state for a while. The only one that still doesn't work is K4dirstat, but it doesn't freeze, it just gives wrong results. All the other ones work though.

---

