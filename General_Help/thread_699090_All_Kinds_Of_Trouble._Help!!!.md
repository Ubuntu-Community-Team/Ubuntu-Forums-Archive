---
title: "All Kinds Of Trouble. Help!!!"
date: 2008-02-17
forum: General Help
---

### Post by romeojg30 on 2008-02-17
Where do I begin.  I'm trying to learn how to use and configure Ubuntu.  In the process of installing "Automatix2" I screwed something up on the OS.  Now when I try to run Synaptic Manager I get this error:

E: Type "wget" is not known on line 74 in source list /etc/apt/sources.list
E: The list of sources could not be readGo to the repository dialog to correct the problem.
E:_cache->open()failed, please report.

That's one error.  My next problem lies during package installer.  I get this error:

"Software index is brokenThis is a major failure of your software management system.  Please check for broken packages with synaptic.  Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

Of couse i tried Synaptic only to be met with my first problem.  Anyhow, my next issue lies with the partitioning of my hard drive.  I thought I created my own hard drive partition for ubuntu only to realize I installed it on the same partition as my Vista OS.  Oh a partition was created but it was made with free space.  I tried to uninstall Ubuntu in hopes to do a clean install but couldn't figure that out either.  So here are my questions:

How do I fix the errors I'm getting?  How do I do an uninstall and clean install of ubuntu (for future reference)?Last, how do I fix my partition problem?Help is greatly appreciated.  
Thanks
Julian

---

### Post by meindian523 on 2008-02-17
For the errors:

Open /etc/apt/sources.list.```

gksudo gedit /etc/apt/sources.list
```
Go to line 74 and remove the word wget from that line.Meaning right now it would be something like wget deb...something something
Change it to deb something something.
The run sudo apt-get install -f and sudo apt-get update

---

### Post by meindian523 on 2008-02-17
Uninstall of Ubuntu==>removal of it's partitions,just what you would do to uninstall Windows too,because both are OS's,you don't have an uninstall program for OS's.
For your partition problems,please provide ```
sudo fdisk -l
```

---

