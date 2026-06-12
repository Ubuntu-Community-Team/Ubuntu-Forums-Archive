---
title: "&quot;Serious error&quot; message on trying to update packages"
date: 2014-03-09
forum: General Help
---

### Post by dakarpaul on 2014-03-09
Hello

In, Ubuntu 12.04, in attempting to install or check for updates I have an error signal (red circle with white horizontal line)
in the top right corner of my window and an error message: (noting this is a "serious problem") of 
"E:Encountered a section with no Package: header, E problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_
precise-security_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened. 

On trying sudo apt-get update I get the following:

E:Encountered a section with no Package: header, E: problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise
-security_universe_i18n_Translation-en, E: The package lists or status file could not be parsed or opened.

I would be very grateful for any advice.

Paul

---

### Post by Bashing-om on 2014-03-09
dakarpaul; Hi ! Welcome to the forum.

That error condition is indicative of a corrupted control file.
What results when that file is removed, and rebuilt ?
Apply these terminal commands:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
"apt-get update" rebuilds the index files that were "removed" and "apt-get upgrade" updates the installed packages to what is now current.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by dakarpaul on 2014-03-10
Many thanks Bashing-om!

I applied the code you provided, all works fine and I have marked the thread as solved.
Paul

---

