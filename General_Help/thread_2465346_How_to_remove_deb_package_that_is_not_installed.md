---
title: "How to remove deb package that is not installed"
date: 2021-07-30
forum: General Help
---

### Post by Acharn on 2021-07-30
I started to debug my printer, which does not print, and 'ubuntu-bug cups' paused and asked me which I wanted to check, cups 0.1.0 or "cups 2.3.1-ubuntu1.1 deb package," because "both are installed." I would prefer to remove the 2.3.1 package, because 0.1.0 is the most recent (???), but synaptic package manager says it's not installed, yet when I search for "cups" in synaptic it gives the names "cups" and "cups 2.3.1" in the left-hand column. The name "cups" is accompanied by a long list of names in the right column, while for "cups 2.3.1" the list is empty. I tried using ```
sudo dpkg --remove cups_2.3.1
``` but it responded "this package is not installed." I presume I have the name of the package wrong, but don't know how to find the correct name. What step should I take next?

---

### Post by guiverc on 2021-07-30
0.1.0 is a really old package and doesn't match any supported (*nor any ESM*) release of Ubuntu, so where was it from I wonder?

You can view the expected packages via CLI tools, or using web tools such as

[https://packages.ubuntu.com/search?keywords=cups&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=cups&searchon=names&suite=all&section=all)

which will show the package you mention (*wanting to remove*) is the updated version for 20.04 or *focal* - [https://packages.ubuntu.com/focal-updates/cups](https://packages.ubuntu.com/focal-updates/cups)

Given I don't know what release you're using (*maybe you're not using 20.04 thus why you want to remove that package*) I won't advise further, but even a CLI enquiry `rmadison cups` doesn't show any 0.1.0 even for ESM releases (1.5.3-0ubuntu8.7 for example for *precise* or an updated 12.04 system your profile details suggest)

(a quick *rdepends* query suggests to me removing `cups` for my release would **not**be a good idea for my system & release anyway).

---

### Post by Paddy Landau on 2021-07-30
It's always helpful to let us know which version of Ubuntu you're using.

I have Ubuntu 20.04, and it has only CUPS version 2.3.1 installed.

I wonder if, on your machine, CUPS 0.1.0 has been installed as a snap? You can find out with this command:
```
snap list | grep -F cups
```
If it returns nothing, that's not how it was installed.

Your command didn't work because the name of the package isn't [FONT=lucida console]cups_2.3.1[/FONT]. The name is just [FONT=lucida console]cups[/FONT], nothing else. You can see what CUPS packages are installed with this command:
```
dpkg-query --list 'cups*' | grep '^ii'
```
I advise that you **don't** uninstall CUPS, because that will damage your printing ability.

May I ask what makes you think that version 0.1.0 is more up-to-date than 2.3.1? It definitely isn't.

---

### Post by Acharn on 2021-07-30
Whoops, sorry, I thought I had mentioned that I'm working on Ubuntu 20.04. 

This query started out when I decided to prepare a bug report for my Canon G2010 printer. It does not print, although everything looks like it's right and the scanner works. I have the troubleshooting guide, 12 pages long, and expected to spend a long time gathering the data and adding it to the bug report. So I started with ```
ubuntu-bug cups
```
Before long I got a pop-up requesting authentication, and then another pop-up from Apport saying ```
You have two versions of this application installed, which one do you want to report a bug against?
x  cups 0.1.0 (latest/edge) snap
   cups 2.3.1-9ubuntu1.1 deb package
```
Since the line for 0.1.0 had the word "latest" I assumed it was the one installed.

So, ```
snap list | grep -F cups
cups     0.1.0     432     latest/edge     openprinting*
```

and
```
dpkg-query --list 'cups*' | grep '^ii'
ii  cups                      2.3.1-9ubuntu1.1 amd64        Common UNIX Printing System(tm) - PPD/driver support, web interface
ii  cups-browsed              1.27.4-1         amd64        OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd                  2.3.1-9ubuntu1.1 amd64        Common UNIX Printing System(tm) - BSD commands
ii  cups-client               2.3.1-9ubuntu1.1 amd64        Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common               2.3.1-9ubuntu1.1 all          Common UNIX Printing System(tm) - common files
ii  cups-core-drivers         2.3.1-9ubuntu1.1 amd64        Common UNIX Printing System(tm) - driverless printing
ii  cups-daemon               2.3.1-9ubuntu1.1 amd64        Common UNIX Printing System(tm) - daemon
ii  cups-filters              1.27.4-1         amd64        OpenPrinting CUPS Filters - Main Package
ii  cups-filters-core-drivers 1.27.4-1         amd64        OpenPrinting CUPS Filters - Driverless printing
ii  cups-ipp-utils            2.3.1-9ubuntu1.1 amd64        Common UNIX Printing System(tm) - IPP developer/admin utilities
ii  cups-pk-helper            0.2.6-1ubuntu3   amd64        PolicyKit helper to configure cups with fine-grained privileges
ii  cups-ppdc                 2.3.1-9ubuntu1.1 amd64        Common UNIX Printing System(tm) - PPD manipulation utilities
ii  cups-server-common        2.3.1-9ubuntu1.1 all          Common UNIX Printing System(tm) - server common files

```

The problem is not what I thought it was. I'm out of my depth. Maybe this conflict has something to do with my printer failing to print. It's clear the one I want to remove is the snap, but I'm not familiar with using snap. I would welcome suggestions.

---

### Post by Paddy Landau on 2021-07-30
Your printer might be failing because you have two different versions of CUPS installed. They could be conflicting, or your printer software could be using the older version.

I suggest that you remove the snap version:
```
snap remove cups
```
Try your printer again, and see if you still have errors.

---

### Post by Acharn on 2021-07-30
That successfully removed the snap, and 'ubuntu-bug cups' now runs to completion, but the printer still sits there like a lox. Thanks a lot for giving me confidence to run that snap command. I was really worried it would mess up the installed version. I'll come back to preparing a complete bug report tomorrow.

---

### Post by Paddy Landau on 2021-07-30
Before reporting a bug, because that might not be where the problem lies…

I think that you've started in the wrong place: Reporting a bug with CUPS instead of finding help with installing your printer. After all, your printer and computer are already communicating. It tells me that it's not a bug but a configuration problem.

Reinstall your printer from scratch.

 If that doesn't work, start a new thread giving details of your make and model, and explicitly what you've done to try to get it to work. Remember that people can't see your screen, so give details.

Good luck!

---

