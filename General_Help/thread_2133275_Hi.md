---
title: "Hi"
date: 2013-04-07
forum: General Help
---

### Post by Ali paco on 2013-04-07
Greedings...
Guys I am new in linux ubuntu world and i have a problem and i need a quick solution....

When i want to update my software i receive this error message: The following packages have unmet dependencies:
```

ubuntu-desktop: Depends: printer-driver-pnm2ppa but it is not installed
Depends: xdiagnose but it is not installed
```

And when i oped ubuntu software centre I receive a message: Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now? I press repair and it downloads until half of the download i receive an error message: package operation failed, the installation or removal of a software package failed. details: 
```
installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
dpkg: error: parsing file '/var/lib/dpkg/status' near line 24730 package 'ubuntu-desktop': 
 `Depends' field, invalid package name `xdi!gnose': character `!' not allowed (only letters, digits and characters `-+._') 
Error in function:  

```
Please i need a quick solution

---

### Post by Iowan on 2013-04-07
Perhaps a more descriptive title will draw more responses...

> dpkg: error: parsing file '/var/lib/dpkg/status' near line 24730 package 'ubuntu-desktop':
`Depends' field, invalid package name `xdi!gnose': character `!' not allowed (only letters, digits and characters `-+._')
I'm not familiar w/ the process, but looks like a typo has sneaked in. You can look in */var/lib/dpkg/status* near line 24730 to see if 'xdiagnose' is spelled 'xdi!gnose'. 
What I **don't** know is whether you can edit that file to fix the problem.

---

### Post by Ali paco on 2013-04-07
I don't know how to edit the file or where should i go to edit the file! I think it is from the xdiagnose package.. But i didn't install this package it is not installed

Please any ideas here to how to change this package name or delete it
When I tried to update the software I received a message: Run this command in Terminal: **apt-get install -f**
When I tried to run this command this message applied: 

```
ghostpc@ghostpc-desktop:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

---

### Post by Frogs Hair on 2013-04-07
You need to be root . ```
sudo apt-get install -f
```

---

### Post by ibjsb4 on 2013-04-07
> **Iowan said:**
> I'm not familiar w/ the process, but looks like a typo has sneaked in. You can look in */var/lib/dpkg/status* near line 24730 to see if 'xdiagnose' is spelled 'xdi!gnose'.

In terminal:

```
gksudo gedit /var/lib/dpkg/status
```

To get line numbers go to Edit>preferences

[ATTACH=CONFIG]241078[/ATTACH]

Just be careful what you do

---

### Post by Ali paco on 2013-04-07
I've inserted **sudo apt-get install -f**  see the results:

```
ghostpc@ghostpc-desktop:~$ sudo apt-get install -f
[sudo] password for ghostpc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  printer-driver-pnm2ppa xdiagnose
Suggested packages:
  magicfilter apsfilter
The following NEW packages will be installed:
  printer-driver-pnm2ppa xdiagnose
0 upgraded, 2 newly installed, 0 to remove and 328 not upgraded.
Need to get 0 B/311 kB of archives.
After this operation, 1,466 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 24730 package 'ubuntu-desktop':
 `Depends' field, invalid package name `xdi!gnose': character `!' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
ghostpc@ghostpc-desktop:~$ 
```

It seems like another error.....

---

### Post by Ali paco on 2013-04-07
WAAAAAAAAAAAHAHAHAHAAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHA guys I am laughing soooo hard WAHAHAHAHAHAHA 
I don't believe that i've followed all of your descriptions and i succeed !!!

Thanks guys A loy specialy ibjsb4 and Frogs Hair !!!
I really appreciate you guys :)

---

### Post by ibjsb4 on 2013-04-07
Good show :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

