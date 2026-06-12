---
title: "Not able to install softwares using apt-get command"
date: 2016-01-05
forum: General Help
---

### Post by prashanthharidas on 2016-01-05
I am trying to install openshot video editor. I'm not alble to install any softwares using apt-get command. Below is the command entered

 sudo apt-get install openshot 

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en%5fIN
E: The package lists or status file could not be parsed or opened.

Can someone help me resolve the issue? I couldn't find any threads on this issue and I'd be very happy if you could point me to a solved thread


Thanks,
Prashanth

---

### Post by Bashing-om on 2016-01-05
prashanthharidas; Hello; Welcome to the forum.

We have this advisory:
> 
E: The package lists or status file could not be parsed or opened.

that is one indication of corrupted control files. The first thing to attempt is just to delete the package lists: and rebuild these control files .
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon.
When corrupted, they can be safely deleted. Apt will recreate them during the next apt-get update.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

