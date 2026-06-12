---
title: "backup and restore installed packages"
date: 2015-11-09
forum: General Help
---

### Post by Drenriza on 2015-11-09
Hi all

I am trying to backup and restore installed packages between two Ubuntu 12.04.5 LTS systems.

I have followed this guide [http://askubuntu.com/questions/9135/how-to-backup-settings-and-list-of-installed-packages](http://askubuntu.com/questions/9135/how-to-backup-settings-and-list-of-installed-packages)
that states the following steps

Backup

[LIST]
[*]dpkg --get-selections > ~/Package.list
[*]sudo cp -R /etc/apt/sources.list* ~/
[*]sudo apt-key exportall > ~/Repo.key
[/LIST]

Restore
[LIST]
[*]sudo apt-key add ~/Repo-keys
[*]sudo cp -R ~/sources.list* /etc/apt/
[*]sudo apt-get update
[*]sudo apt-get install dselect
[*]sudo dselect update
[LIST]
[*]apt-cache dumpavail > ~/temp-avail
[*]sudo dpkg --merge-avail ~/temp-avail
[*]rm ~/temp-avail
[/LIST]

[*]sudo dpkg --set-selections < ~/Package.list
[*]sudo apt-get dselect-upgrade -y
[/LIST]

While the system upgrade existing and install new packages i get the error
> E: Internal Error, No file name for libapt-pkg4.12
that than exists the entire upgrade.

When i check the system that i made the package update from i see that it has a older version of the package than the new installed system.
old system
> ii  libapt-pkg4.12                    0.8.16~exp12ubuntu10.22           package managment runtime library

new installed system
> iU  libapt-pkg4.12                    0.8.16~exp12ubuntu10.26           package managment runtime library

I have searched the web for an answer to how one can downgrade **(prefered)** or skip packages that a newer and continue to the next. 
But so far i have not found an answer.

Hope someone can point me in the right direction

Thanks on advance
Kind regards

---

