---
title: "Upgrade Breezy Error"
date: 2007-04-13
forum: General Help
---

### Post by JimS on 2007-04-13
...
Finally getting tired of the problems using Breezy
and have decided to upgrade, maybe all the way to Feisty, at least to Dapper.
I'm a bit edgy about Edgy.
So I did the following and got the following message:

$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) breezy/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

$  apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

What now?

The box is a 6 year old Dell 4100
running at 1GHz, w/ 512 RAM
Duel boot w/ Breezy on 2nd drive, ME on first.
Got a XP box and Dapper notebook on uncompleted network
(they see the world, but not each other)

Thanks

JimS
Old Dawg slowly learning new tricks
[email]workfromhome@pobox.com[/email]
....

---

### Post by zvacet on 2007-04-13
[https://help.ubuntu.com/community/DapperUpgrades]("https://help.ubuntu.com/community/DapperUpgrades")

---

### Post by JimS on 2007-04-14
...
Issue Resolved.
I made a seperate Home partition following Psychocats directions.
God Bless Psychocats.
Couldn't log in, so I successfully installed Edgy.
No more error msgs.
All I need to do now is find and install my old bookmarks and
address book (I switched from Thunderbird to Evolution - needed PIM),
and maybe a few other things.
... 
Thanks,
JimS
[email]workfromhome@pobox.com[/email]
...

---

