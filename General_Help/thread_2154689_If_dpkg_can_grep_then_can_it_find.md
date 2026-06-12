---
title: "If dpkg can grep then can it find?"
date: 2013-06-15
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-06-15
The Brother driver software and the page(S) that instruct an end user on how to install their software are a real mess. It is as though a Japanese software guy, with some English skills was tasked to make the Linux pages for their products. The instructions for installing, uninstalling and checking are just a mess. If you install the scanner software then you have to modify some file to make it usable by other than "root".  I'm marking this page as solved, even though my scanner is still not working. The printer did print a test page, so I guess that part is A-OK.


Lines from OP below:

I am finishing a fresh install of 12.04 LTS. 

I have to uninstall some packages that the Brother Printer requires. But the page that shows the [uninstall example]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_esp4.html#Inst5") does not show the directory name for where those packages are.

I figure if grep can find them to show the below info:

mark@Lexington:/$ dpkg -l | grep Brother
pi  mfc240ccupswrapper           1.0.1-1                                 Brother CUPS Inkjet Printer Definitions
pi  mfc240clpr                             1.0.1-1                                 Brother lpr Inkjet Printer Definitions

then grep can show the directories they are in and I can use their supplied command:

sudo dpkg -P mfc240clpr

What is the proper "argument" in grep that will show the folders/directores these two packages are in?

---

### Post by Cheesemill on 2013-06-15
You don't supply the path and filename of a package when you use 'dpkg -P' command, you just provide the name of the package you want to remove.
```
dpkg -P mfc240clpr
dpkg -P mfc240ccupswrapper
```

---

### Post by Mark_in_Hollywood on 2013-06-15
Per Cheesemill's suggestions, I tried:

mark@Lexington:~$ sudo dpkg -P mfc240clpr
[sudo] password for mark: 

dpkg: dependency problems prevent removal of mfc240clpr:
 mfc240ccupswrapper depends on mfc240clpr.
dpkg: error processing mfc240clpr (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 mfc240clpr

mark@Lexington:~$ sudo dpkg -P mfc240ccupswrapper

(Reading database ... 181868 files and directories currently installed.)
Removing mfc240ccupswrapper ...
/var/lib/dpkg/info/mfc240ccupswrapper.prerm: 3: /var/lib/dpkg/info/mfc240ccupswrapper.prerm: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: error processing mfc240ccupswrapper (--purge):
 subprocess installed pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc240ccupswrapper.postinst: 3: /var/lib/dpkg/info/mfc240ccupswrapper.postinst: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
Errors were encountered while processing:
 mfc240ccupswrapper

---

### Post by sum1nil on 2013-06-15
Try to do an 'apt-get purge mfc240clpr && apt-get update' or maybe more simpley the purge. Also, try the -f option in apt-get - 'apt-get --help'
Best of luck.

---

