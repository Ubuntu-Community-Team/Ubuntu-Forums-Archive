---
title: "Noob Question: Unattended Upgrades Best Practice - Backup/Recovery"
date: 2017-10-08
forum: General Help
---

### Post by peppy3 on 2017-10-08
Greetings,
 
I do have unix experience with a VPS hosting service, but I am starting my own server for the first time (managing it myself, etc), so I'm very noobish at it. I'm planning on building a LAMP server eventually.

I have unattended-upgrades set up to run, for both Security and Updates. However, I hear that sometimes updates will cause things to break, and I read in a book that the following command is supposed to gather up a list of packages:

```
# dpkg &#8211;get-selections > packages.list
```

I heard that if the update fails, I can recover the system's packages by using deselect:

```
# dselect update
# dpkg --set-selections < packages.list
# apt-get dselect-upgrade

```

[B]Question:

[/B]Does unattended-upgrades have something like this built in? If not, how can I save a list of packages (unique dated names) BEFORE each update begins, so that in the case of the server breaking, I can simply reinstall the old packages back.

Thanks
Kind regards

---

### Post by ian-weisser on 2017-10-08
Unattended-upgrade has nothing to do with backups.
u-u doesn't change any of your package names; it only upgrades that package to a newer version. Your old list of packages will still work.

I find the --get-selections/--set-selections list-of-packages to be unnecessary. You already know which few top-level applications you want to run - let the package manager sort all the low-level dependencies. That's what it is for.
The headache with a --get-selections list is that it includes specific kernel versions that get stale quickly. If you go this route, re-generate your list frequently with the rest of your backups.


As you are learning, you *will* certainly need to reinstall. Learn the recovery skills too: Take notes (a paper notebook is handy), practice reinstalling, and exercise how to restore data from backup. VMs are great for this practice, and these skills will save you much anguish on the first very-bad-day.

---

