---
title: "Problem in opening of Ubuntu software center"
date: 2014-08-08
forum: General Help
---

### Post by sram180990 on 2014-08-08
Hello Guys,
I have a problem that when I try to open software center it does not open.
When I try open the software center it just opens and closes automatically.
Why this happens? tell me the solution for this problem

---

### Post by Bashing-om on 2014-08-09
sram180990; Hi !

Before seeing the errors generated in terminal from attempting to open the software-center application, let's make sure the package management system is in a consistent state.

what results from terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

a process in
[INDENT][INDENT]fault isolation to restoration
[/INDENT][/INDENT]

---

### Post by sram180990 on 2014-08-09
After this command

sudo apt-get update
E: Malformed line 1 in source list /etc/apt/sources.list.d/getdeb.list (dist)
E: The list of sources could not be read.
_______________________________________________________________________


After this command
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  unity-settings-daemon
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 489 kB of archives.
After this operation, 24.6 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main unity-settings-daemon amd64 14.04.0+14.04.20140606-0ubuntu1 [489 kB]
Fetched 489 kB in 28s (16.9 kB/s)                                              
(Reading database ... 258430 files and directories currently installed.)
Preparing to unpack .../unity-settings-daemon_14.04.0+14.04.20140606-0ubuntu1_amd64.deb ...
Unpacking unity-settings-daemon (14.04.0+14.04.20140606-0ubuntu1) over (14.04.0+14.04.20140414-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.0-2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up unity-settings-daemon (14.04.0+14.04.20140606-0ubuntu1) ...

and still the same problem exists

---

### Post by grahammechanical on 2014-08-09
This is the cause of the problem

> [COLOR=#000000]E: Malformed line 1 in source list /etc/apt/sources.list.d/getdeb.list (dist)[/COLOR]
[COLOR=#000000]E: The list of sources could not be read.[/COLOR]

You have added getdeb as a software source and there is something wrong with the first line of the file getdeb.list. That is the answer to your "Why" question. The solution? I do not like offering solutions that I have not tested because I have no experience with getdeb.

If you remove that getdeb PPA then software centre should load. That is all I am prepared to say. Fixing getdeb is another matter and as this is not my machine I will not offer my guesses.

[http://en.wikipedia.org/wiki/GetDeb](http://en.wikipedia.org/wiki/GetDeb)

[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

Regards.

---

### Post by Jesse_Campton on 2014-08-09
Good Morning, lets try opening a terminal. Now copy & paste this into your terminal: ```
[COLOR=#000000][FONT=verdana]cat /etc/apt/sources.list[/FONT][/COLOR]
``` and post the outcome for us. Also, post the outcome for ```
cat /etc/apt/sources.list.d/getdeb.list
```.

---

### Post by Jonathan Precise on 2014-08-09
Hello sram180990!

Seems that the problem is the getdeb ppa. Please post the output of:

```
cat /etc/apt/sources.list.d/getdeb.list
```

It should guide us to where in the getdeb ppa the problem lies.

EDIT: I should have scrolled all the way down.

---

### Post by vasa1 on 2014-08-09
> **Jonathan Precise said:**
> Hello sram180990!

Seems that the problem is the getdeb ppa. Please post the output of:

```
cat /etc/apt/sources.list.d/getdeb.list
```

It should guide us to where in the getdeb ppa the problem lies.See the post from four hours ago just above yours.

---

### Post by Jonathan Precise on 2014-08-09
> **vasa1 said:**
> See the post from four hours ago just above yours.

Oops! I should have scrolled all the way down.

---

