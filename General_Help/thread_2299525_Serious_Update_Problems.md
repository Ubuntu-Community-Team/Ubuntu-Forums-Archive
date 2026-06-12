---
title: "Serious Update Problems :/"
date: 2015-10-19
forum: General Help
---

### Post by computer_geek2 on 2015-10-19
Hi, everybody. I am having serious updating problems with Ubuntu 15.04 and the system will NOT install ANY updates AT ALL. When attempting to install/uninstall anything through Terminal, it just complains about some application, spits out a ton of text, and does not perform the requested operation. >:(
Failure Log:
```
[COLOR=#070F14][FONT=Verdana]Setting up util-linux (2.25.2-4ubuntu3) ...[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: warning: script 'S95masquradescript' missing LSB tags and overrides[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: script virtualbox: service vboxdrv already provided![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: script virtualbox: service virtualbox already provided![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: warning: script 'nat.sh' missing LSB tags and overrides[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: There is a loop between service masquradescript and rc.local if started[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: loop involving service rc.local at depth 8[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: loop involving service masquradescript at depth 1[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: exiting now without changing boot order![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]update-rc.d: error: insserv rejected the script header[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: error processing package util-linux (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]subprocess installed post-installation script returned error exit status 1[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Setting up cups-browsed (1.0.67-0ubuntu2.4) ...[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: warning: script 'S95masquradescript' missing LSB tags and overrides[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: script virtualbox: service vboxdrv already provided![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: script virtualbox: service virtualbox already provided![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: warning: script 'nat.sh' missing LSB tags and overrides[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: There is a loop between service masquradescript and rc.local if started[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: loop involving service rc.local at depth 8[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: loop involving service masquradescript at depth 1[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: exiting now without changing boot order![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]update-rc.d: error: insserv rejected the script header[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: error processing package cups-browsed (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]subprocess installed post-installation script returned error exit status 1[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Setting up cups-daemon (2.0.2-1ubuntu3.2) ...[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: warning: script 'S95masquradescript' missing LSB tags and overrides[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: script virtualbox: service vboxdrv already provided![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: script virtualbox: service virtualbox already provided![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: warning: script 'nat.sh' missing LSB tags and overrides[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: There is a loop between service masquradescript and rc.local if started[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: loop involving service rc.local at depth 8[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: loop involving service masquradescript at depth 1[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: exiting now without changing boot order![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]update-rc.d: error: insserv rejected the script header[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: error processing package cups-daemon (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]subprocess installed post-installation script returned error exit status 1[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: dependency problems prevent configuration of cups-core-drivers:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]cups-core-drivers depends on cups-daemon (>= 2.0.2-1ubuntu3.2); however:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package cups-daemon is not configured yet.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]dpkg: error processing package cups-core-drivers (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: dependency problems prevent configuration of cups:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]cups depends on cups-core-drivers (>= 2.0.2-1ubuntu3.2); however:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package cups-core-drivers is not configured yet.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]cups depends on cups-daemon (>= 2.0.2-1ubuntu3.2); however:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package cups-daemon is not configured yet.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]dpkg: error processing package cups (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: dependency problems prevent configuration of printer-driver-hpcups:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]printer-driver-hpcups depends on cups (>= 1.4.0) | cupsddk; however:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package cups is not configured yet.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package cupsddk is not installed.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]printer-driver-hpcups depends on cups; however:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package cups is not configured yet.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]dpkg: error processingNo apport report written because MaxReports is reached already[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]No apport report written because MaxReports is reached already[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]No apport report written because MaxReports is reached already[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]No apport report written because MaxReports is reached already[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]No apport report written because MaxReports is reached already[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]No apport report written because MaxReports is reached already[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]package printer-driver-hpcups (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: dependency problems prevent configuration of hplip:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]hplip depends on printer-driver-hpcups (= 3.15.2-0ubuntu4.2); however:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package printer-driver-hpcups is not configured yet.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]hplip depends on cups (>= 1.1.20); however:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package cups is not configured yet.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]dpkg: error processing package hplip (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: dependency problems prevent configuration of hplip-gui:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]hplip-gui depends on hplip (>= 3.15.2-0ubuntu4.2); however:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package hplip is not configured yet.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]dpkg: error processing package hplip-gui (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]printer-driver-postscript-hp depends on hplip (>= 3.15.2-0ubuntu4.2); however:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Package hplip is not configured yet.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]dpkg: error processing package printer-driver-postscript-hp (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Setting up unattended-upgrades (0.83.6ubuntu1) ...[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: warning: script 'S95masquradescript' missing LSB tags and overrides[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: script virtualbox: service vboxdrv already provided![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: script virtualbox: service virtualbox already provided![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: warning: script 'nat.sh' missing LSB tags and overrides[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: There is a loop between service masquradescript and rc.local if started[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: loop involving service rc.local at depth 8[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: loop involving service masquradescript at depth 1[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: Starting nat.sh depends on rc.local and therefore on system facility `$all' which can not be true![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]insserv: exiting now without changing boot order![/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]update-rc.d: error: insserv rejected the script header[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]dpkg: error processing package unattended-upgrades (--configure):[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]subprocess installed post-installation script returned error exit status 1[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]No apport report written because MaxReports is reached already[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]util-linux[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]cups-browsed[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]cups-daemon[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]cups-core-drivers[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]cups[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]printer-driver-hpcups[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]hplip[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]hplip-gui[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]printer-driver-postscript-hp[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]unattended-upgrades[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/COLOR]
```


What is going on!?!?!?
Please help, and thanks in advance.

---

### Post by ian-weisser on 2015-10-19
Yes, that 'ton of text' is the system trying to tell you exactly what the problem is. I see about three different problems in there, but two might be related.

Here's an example:
> insserv: warning: script 'S95masquradescript' missing LSB tags and overrides

It means you have a script S95masquradescript somewhere in /etc/init.d/ or /etc/rc.* . See if you can find it.

LSB tags and overrides are the lines at the top of all scripts in /etc/init. Debian and Ubuntu systems use them to determine exactly when it's appropriate to run the script. Look at any script in /etc/init (except S95masquradescript, obviously) for an example.

This kind of error often occurs when a user copy-and-pastes scripts from random (sometimes very old) internet blogs. If S95masquradescript was installed by a package from the Ubuntu repositories, please file a bug report!

 After you fix your S95masquradescript, try an apt-get update and see how the error messages are fewer and different.
If you don't understand the new error message, post it here.

---

### Post by cmcanulty on 2015-10-19
you probably already tried this but it often fixes system issues for me

```
sudo dpkg --configure -a
```

---

### Post by ajgreeny on 2015-10-19
There is a repeat in the log of
> insserv: script virtualbox: service vboxdrv already provided!
insserv: script virtualbox: service virtualbox already provided!
Is this an installation of Ubuntu in VBox?

As **cmcanulty** says, it is worth trying the commands ```
sudo apt-get install -f
sudo dpkg --configure -a
```the first of which can fix broken packages and the second, configure any that are not completely installed, perhaps as a result of a crash of the system.

---

### Post by computer_geek2 on 2015-10-19
How do I fix the script? Just copy/paste the LSB tags/overrides from one script to that one??

---

### Post by ian-weisser on 2015-10-19
That's one way...assuming the header says what you want it to say. Getting the header wrong might make your problem much worse.

Another way is to explain exactly why you added that (apparently) non-Ubuntu software. We might be able to point you toward a safer way to accomplish your goal.

Yet another way is to complain to whomever wrote the script without the proper header, and ask their help to fix their mistake.

---

### Post by computer_geek2 on 2015-10-19
IDK how it got there.How can I track down it's respective application and safely remove it?

---

### Post by ian-weisser on 2015-10-20
One easy way is to use the 'dpkg' command.

Example: Let's look for the package that installed the script /etc/init.d/cron
```
$ dpkg --search /etc/init.d/cron
**cron**: /etc/init.d/cron

```
The file was installed by the 'cron' package.
You CAN edit the file, but those edits might be overwritten by a future update of the package. So keep a backup or journal of any customizations you make.
NEVER delete a file that was installed by a package. Use the package manager to uninstall the entire package.


Another example: Let's look for the package that installed the directory /tmp/skype-1996...which I happen to know is NOT installed by any package.
```
$ dpkg --search /tmp/skype-1996
dpkg-query: no path found matching pattern /tmp/skype-1996
```
See the difference?
Some application created this file, not the package manager.
You can edit the file, or delete it as you wish...and will merely break that application.

---

### Post by computer_geek2 on 2015-10-22
Currently on a road to nowhere... :(

Waiiit... FIXED!!!!

Do beans mean posts?

---

