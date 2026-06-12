---
title: "no package header"
date: 2016-10-25
forum: General Help
---

### Post by duncantickner on 2016-10-25
I'm running 12.04

I am getting the following error message when trying to update, (via update manager, synaptic package manager or apt-get)

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/apt.fuzebox.com_apt_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

I have not used fuzebax for many moons and would be happy to get rid of it, if it would solve the problem, But don't know how to or if doing so would make matters worse.

---

### Post by tuese on 2016-10-28
Just try to uninstall it or better upgrade your ubuntu at least to 14.04 and install new version of fuzebox.

---

### Post by Bashing-om on 2016-10-28
tuese; Hello;

What is most often found in " problem with MergeList" is the system advising of corrupted control files .

Rebuild these control files:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo ap update

```
MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon.
When corrupted, they can be safely deleted. Apt will recreate them during the next apt update.


Removing fuzebox will be viewed as a separate ( though it is a related_ issue) .. once you have the package manager restored, open a new thread on removing it .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by duncantickner on 2016-11-01
Thank you, I would never have worked that out in a million years. Package manager has duly been restored. turns out that i didn't have fuzebox installed. (It is installed in windows on a different partition) So no idea what what going on there. 
Thank you for your help. problem solved

---

### Post by Bashing-om on 2016-11-01
duncantickner; Great !

Glad ya got it sorted out .

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT][INDENT]onward - upward
[INDENT][INDENT][INDENT]bigger and better things
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

