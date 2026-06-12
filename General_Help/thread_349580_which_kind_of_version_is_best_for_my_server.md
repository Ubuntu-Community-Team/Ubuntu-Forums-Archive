---
title: "which kind of version is best for my server??"
date: 2007-01-30
forum: General Help
---

### Post by mymuscle on 2007-01-30
I have a new dell poweredge server:

Dual (2x) Dual Core Intel Xeon 5060 at 3.20GHz/2x2MB, 1066MHz
4 GB DDR2 SDRAM 667MHz (4 DIMMS) 
3 x SAS 73GB 10K RPM 2.5-inch, RAID5


I would like to know which version of ubuntu is the best for my server, cuase I see there are different ypes like i386, x64 etc... I don't know what that stuff means, any help?

---

### Post by mymuscle on 2007-01-30
:d

---

### Post by tinman on 2007-01-30
Well hell I'll give it a shot! With dual core you can use the 64bit or the 32bit version 
of whatever operating system you want to use. You will get better performance from the 64bit 
version on the dual core although. The repositories are better suited for 32bit but I have done the 64bit as well, if it is a server without desktop and gui then you should be ok with the 64bit.:o

---

### Post by houstonbofh on 2007-01-30
> **mymuscle said:**
> I have a new dell poweredge server:

Dual (2x) Dual Core Intel Xeon 5060 at 3.20GHz/2x2MB, 1066MHz
4 GB DDR2 SDRAM 667MHz (4 DIMMS) 
3 x SAS 73GB 10K RPM 2.5-inch, RAID5


I would like to know which version of ubuntu is the best for my server, cuase I see there are different ypes like i386, x64 etc... I don't know what that stuff means, any help?
The first question is "Server for what?"  You have a 64 bit system, and 64 bit is nice, but not all apps run on it.  Installing the "server" version will give a kernel optimized for I/O, and can be nice.  It also is a very easy way to get a LAMP server going.  However, it does not install a GUI by default.  This can be easily done with the command "sudo apt-get install ubuntu-desktop" if you desire.

---

### Post by mymuscle on 2007-01-30
It a server specifically for LAMP. so you guys reccomned to install the x64 with the gui?

---

### Post by tinman on 2007-01-30
Well if it is going to be a dedicated server installing the server version (without the desktop) would be the better way to go as it is less resource demanding, but if you are just going to mess around and learn, then yes, I would do that. There are also gui's that are very minimal that you can use too if it is dedicated.

---

### Post by mymuscle on 2007-01-31
yes it is dedicated. What other gui's do you reccomend? I thought gnome was the best?

---

### Post by houstonbofh on 2007-02-07
Gnome is tightly intergrated into Ubuntu.  It has the most configu tools, and the update-manager Ubuntu prefers is built in to the gnome version of Ubuntu.

KDE is lighter weight.  Some say it is cleaner.  It did have some upgrade problems from Dapper to Edgy because of a missing update-manager.

Xubuntu is very light.  It has the least tools, but it is damn lean.  For experianced users on a server, this is the winner.

After installing a LAMP server from the ubuntu server CD, from the command line type;
> sudo apt-get install ubuntu-desktop
or
> sudo apt-get install kbuntu-desktop
or
> sudo apt-get install xubuntu-desktop

---

