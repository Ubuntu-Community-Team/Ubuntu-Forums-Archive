---
title: "Error updating, no header."
date: 2015-04-16
forum: General Help
---

### Post by yote2 on 2015-04-16
Hello everyone, I am new to the forum.

I have been using Ubuntu variants for about a year now.  What a wonderful Linux flavor to bring old computers back to life.

I am currently dealing with a problem with my Kubuntu laptop.
Recently I tried to get iTunes to work on this machine using play-on-linux.

Ever since then I have had issues.
Now my computer does not want to update.

Uninstalling (purge) worked but it did not help.

Running a "sudo apt-get autoremove", then a re-update fixed the problem at first but again I am not able to update completely.

Here is my issue.
At the end of the update list in term I get this:

Reading package lists... Error!                                                
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/deb.playonlinux.com_dists_precise_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Any help?
Explanation would be nice too!  I'd love to learn more!

---

### Post by ian-weisser on 2015-04-16
MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon.
When corrupted, they can be safely deleted. Apt will recreate them during the next apt-get update.

```
sudo rm /var/lib/apt/lists/deb.playonlinux.com_dists_precise_main_i18n_Translation-en
sudo apt-get update
```

---

