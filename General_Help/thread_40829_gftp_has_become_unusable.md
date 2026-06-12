---
title: "gftp has become unusable"
date: 2005-06-10
forum: General Help
---

### Post by uc50_ic4more on 2005-06-10
I have been using gftp since my installation of Ubuntu (Hoary) a few weeks ago, and just recently it has become unusably unstable. Specifically, every time I attempt to transfer a file from local --> remote (all via GUI), the program simply exits. Sometimes, I am prompted to re-enter my password for a given site when attempting to transfer remote --> local.

What do I need to post here in the way of log files, preferences, etc. so that someone might have enough information that a solution might make itself apparent?

Thank you.

--> EDIT <--
I have also taken note that when trying to connect to ftp servers, behaviors change a bit: On some sites (hosted by doteasy.com) I cannot access any directories *if* that site has PHP/ MySQL installed.

550 /[directory name]: No such file or directory
... where [directory name] is indeed a valid name

For static sites, I can access directories. For my sites hosted by godaddy.com, I can access directories, but in *all* cases the program simply quits the instant a transfer is initiated.

--> ANOTHER EDIT <--
ISSUE RESOLVED - It was a symlink/ directory naming issue. All is well now.
As it turned out, the "mainwebsite_html" directory on my PHP/ MySQL enabled sites was actually a clever disguise for "/var/www/html", and for reasons beyond the scope of my understanding, that gave rise to a myriad of weird behavior -  not the least of which were all of the 550 errors!

---

