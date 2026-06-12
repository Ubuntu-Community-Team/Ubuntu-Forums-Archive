---
title: "Heellllllppppp"
date: 2008-04-29
forum: General Help
---

### Post by banzeuk on 2008-04-29
hi everyone, ive been trying to install AWN to my Linux 7.10 OS and something went wrong, now every time i try to go to the upgrade or add remove program/ or software sources etc... i get the following error message when trying to open them!

[B]An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/B]

 PLEASE HELP ME I NEED TO UPDATE MY OS. 


PLEASE PLEASE PLEASE

---

### Post by banzeuk on 2008-04-29
hi everyone, ive been trying to install AWN to my Linux 7.10 OS and something went wrong, now every time i try to go to the upgrade or add remove program/ or software sources etc... i get the following error message when trying to open them!

[B]An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/B]

 PLEASE HELP ME I NEED TO UPDATE MY OS. 


PLEASE PLEASE PLEASE

---

### Post by banzeuk on 2008-04-29
hi everyone, ive been trying to install AWN to my Linux 7.10 OS and something went wrong, now every time i try to go to the upgrade or add remove program/ or software sources etc... i get the following error message when trying to open them!

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

PLEASE HELP ME I NEED TO UPDATE MY OS.


PLEASE PLEASE PLEASE

---

### Post by steveneddy on 2008-04-29
Maybe this should be moved to the Desktop and Effects section.

Sorry - I can't help you.

---

### Post by estaticd on 2008-04-29
Backup the contents of this folder before trying this fix:
```
sudo rm /var/lib/apt/lists/* -vf
```

---

### Post by banzeuk on 2008-04-30
what do i do after i back it up ?

---

### Post by thomasaaron on 2008-04-30
You might want to try using simdock instead. It comes with Ubuntu.
Just go to Applications > Add/Remove Software and search for "simdock".
Once you install it, it can be turned on via Applications > Accessories > Simdock. Or you can make it a startup program in System > Preferences > Sessions.

---

### Post by ctsdownloads on 2008-04-30
> **banzeuk said:**
> hi everyone, ive been trying to install AWN to my Linux 7.10 OS and something went wrong, now every time i try to go to the upgrade or add remove program/ or software sources etc... i get the following error message when trying to open them!

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

PLEASE HELP ME I NEED TO UPDATE MY OS.


PLEASE PLEASE PLEASE


Never had a problem with AWN on Heron, but have not tested it on Gutsy.  If the error is preventing apt-get from working at all, you might try this.
[I]
**I promise nothing and I would suggest backing up any files you change - use at your own risk.[/I]

Okay, with that out of the way. I might try 

> gksudo nautilus /var/lib/dpkg

Locate the status file, rename it to status-save

Then do an ap-get update to see if things are still broken.

Then rename status-old to status. My rational comes from [this report]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/199363") as it seemed to work for them. 


Again, if apt-get is working otherwise, take Tom's advice and leave AWN at the door as clearly, it is not jiving well on Gutsy.

---

### Post by banzeuk on 2008-05-04
IT DOESNT WORK.. HOW DO I REMOVE AWN COMPLETELY? ******* hell this is driving me nuts!

---

### Post by banzeuk on 2008-05-04
hi everyone, ive been trying to install AWN to my Linux 7.10 OS and something went wrong, now every time i try to go to the upgrade or add remove program/ or software sources etc... i get the following error message when trying to open them!

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

PLEASE HELP ME I NEED TO UPDATE MY OS.


PLEASE PLEASE PLEASE

---

### Post by ctsdownloads on 2008-05-04
Two things you can do. First it to disable it, by removing it from Sessions.

System, Preferences, Sessions, locate it and choose to delete it.

Then to actually take AWN off of the system completely, in a terminal,

> sudo apt-get remove awn-core-applets-bzr awn-manager-bzr

---

### Post by banzeuk on 2008-05-05
hi everyone, ive been trying to install AWN to my Linux 7.10 OS and something went wrong, now every time i try to go to the upgrade or add remove program/ or software sources etc... i get the following error message when trying to open them!

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

PLEASE HELP ME I NEED TO UPDATE MY OS.


PLEASE PLEASE PLEASE

---

### Post by tamoneya on 2008-05-05
go into terminal and type the following commands.```
sudo apt-get remove avant-window-manager
sudo apt-get update
sudo apt-get check
sudo apt-get clean
sudo apt-get install avant-window-manager
```

---

### Post by banzeuk on 2008-05-06
hello there, when i type 

[I]"sudo apt-get remove avant-window-manager
sudo apt-get update
sudo apt-get check
sudo apt-get clean
sudo apt-get install avant-window-manager"[/I]

i get the following message.

**"E: The package lists or status file could not be parsed or opened".**

The problem still the same! any idea how to fix it? id be really grateful of you can help me! cheers

---

### Post by tamoneya on 2008-05-06
at which command do you get this problem.  Is there anything else outputted.  It is best if you copy and paste out of terminal with ctrl-shift-c.

---

### Post by banzeuk on 2008-05-06
i retyped the code and it worked!

it Worked! 
nice work!

---

### Post by banzeuk on 2008-05-06
to solve this problem simply go into terminal and type the following commands.
Code:

[I]"sudo apt-get remove avant-window-manager
sudo apt-get update
sudo apt-get check
sudo apt-get clean
sudo apt-get install avant-window-manager"[/I]

Thanks to tamoneya!

---

### Post by banzeuk on 2008-05-06
to solve this problem simply go into terminal and type the following commands.
Code:

"sudo apt-get remove avant-window-manager
sudo apt-get update
sudo apt-get check
sudo apt-get clean
sudo apt-get install avant-window-manager"

Thanks to tamoneya!

---

