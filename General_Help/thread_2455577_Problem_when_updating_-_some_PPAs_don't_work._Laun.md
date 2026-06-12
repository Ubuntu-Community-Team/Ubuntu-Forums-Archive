---
title: "Problem when updating - some PPAs don't work. Launchpad.net problem?"
date: 2020-12-22
forum: General Help
---

### Post by GhX6GZMB on 2020-12-22
The last week, I've had problems running "sudo apt update", which has until now worked for a year at least.
Libreoffice and oibaf PPAs refuse connecting to launchpad .net. I've checked my PPAs, and they're as always:

```
macro@macro-pc:~$ sudo apt update
[sudo] password for macro: 
Hit:1 http://de.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [109 kB]                                        
Hit:3 http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu focal InRelease                                   
Hit:4 http://de.archive.ubuntu.com/ubuntu focal-updates InRelease                                                                           
Hit:5 https://deb.opera.com/opera-stable stable InRelease                                                                                   
Get:6 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [24,3 kB]                         
Get:7 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [56,6 kB]         
[COLOR=#ff0000]Err:8 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal InRelease                                                                       [/COLOR]
[COLOR=#ff0000]  Could not connect to ppa.launchpad.net:80 (2001:67c:1560:8008::19), connection timed out Could not connect to ppa.launchpad.net:80 (91.189.95.85), connection timed out [IP: 2001:67c:1560:8008::19 80][/COLOR]
[COLOR=#ff0000]Err:9 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu focal InRelease[/COLOR]
[COLOR=#ff0000]  Unable to connect to ppa.launchpad.net:http: [IP: 2001:67c:1560:8008::19 80][/COLOR]
Fetched 190 kB in 31s (6.197 B/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
[COLOR=#ff0000]W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/focal/InRelease  Could not connect to ppa.launchpad.net:80 (2001:67c:1560:8008::19), connection timed out Could not connect to ppa.launchpad.net:80 (91.189.95.85), connection timed out [IP: 2001:67c:1560:8008::19 80][/COLOR]
[COLOR=#ff0000]W: Failed to fetch http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/dists/focal/InRelease  Unable to connect to ppa.launchpad.net:http: [IP: 2001:67c:1560:8008::19 80][/COLOR]
[COLOR=#ff0000]W: Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]

```The PPA files in /etc/apt/sources.list.d look like this:
```
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal main

deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu focal main
# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu focal main

```


I've made absolutely no changes to my system. But I also see no reports that launchpad has a problem.

Any help is highly appreciated, Thank You.

---

### Post by TheFu on 2020-12-23
Google found this answer: [http://ubuntuhandbook.org/index.php/2020/08/libreoffice-7-0-install-ppa-ubuntu-20-04-18-04/](http://ubuntuhandbook.org/index.php/2020/08/libreoffice-7-0-install-ppa-ubuntu-20-04-18-04/)

For GPU drivers, just use the normal Canonical repos.  The 'ubuntu-drivers' program should install the correct driver automatically.

Be certain to remove the PPA, do an update and perhaps reboot BEFORE doing the **ubuntu-drivers autoinstall** stuff.

---

### Post by GhX6GZMB on 2020-12-23
@TheFu, Thank You.
Interesting link.
I presume that the old LibreOffice PPA was then switched off a week or two ago, and therefore my PPA is not working? Would make sense.

Concerning the GPU driver, I've had problems with "flashing" during login. The Oibaf PPA seemed to solve that.

---

### Post by TheFu on 2020-12-23
Oibaf may have decided not to maintain the ppa anymore. You'd need to ask them. A PPA s something anyone can create.  That person/team can also decide not to continue at any point for any reason. There are no rules.

libreoffice has been trying to convince the openoffice project to shutdown the last few months. LibreOffce as kept moving and OO as been barely alive the last few years.  The corporate sponsor for OO that cased all these issues hoped it would die.

---

### Post by ajgreeny on 2020-12-23
If you want to continue using a libreoffice ppa this is the one that I know works; I have been using it since 16.04, as far as I can remember, and it upgraded three days ago to LO 7.0.4 which is working fine.
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

---

### Post by GhX6GZMB on 2020-12-23
OK, here's an update.

The culprit seems to have been the Oibaf PPA, which spilled over into others.
I've removed the Oibaf PPA completely, as well as the KiCAD PPA (which seemed to be affected). The LibreOffice errors in my OP seem to stem from the other two failing.

I've reinstalled the KiCAD PPA, but not the Oibaf one, and now everyting seems to run.

I wont need the Oibaf any more, my graphics work fine now, so I'll leave it out.

It's still mysterious, though. But Thanks for your efforts.

---

