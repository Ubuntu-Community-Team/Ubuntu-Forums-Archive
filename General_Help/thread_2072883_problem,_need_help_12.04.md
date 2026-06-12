---
title: "problem, need help 12.04"
date: 2012-10-18
forum: General Help
---

### Post by kevinorourke2008 on 2012-10-18
Hello everybody,
Today a notice came up in my bar at the top of my screen, it is a no entry sign when i clicked it it said an error occured please run package manager.
When I run package manager I get this message.

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.

Anybody guide me to the problem or know a fix ?

Cheers Kev

---

### Post by grahammechanical on 2012-10-18
That should not happen but it does sometimes. I have had it happen to me. Open a terminal and run these two commands:

```
sudo rm /var/lib/apt/lists/* -rf
```

followed by

```
sudo apt-get update
```

You will need to put in your password. The first command removes the scripts that are called package lists and are in the /var/lib/apt/lists/ folder or directory.

The second command will replace those package lists and hopefully fix the problem.

The utility that does the updating looks through those lists and compares them with lists in the repositories. That way it knows what packages have been updated and need to be downloaded.

Update Manager looks for a package header at the top of the file. If by some error there is a blank line at the top, then Update Manager trips up.

Regards.

---

