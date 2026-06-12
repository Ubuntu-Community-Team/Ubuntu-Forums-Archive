---
title: "Updates - Not upgraded - Kept Back (Linux-Generic)"
date: 2017-08-11
forum: General Help
---

### Post by Alan5127 on 2017-08-11
Hi All,

I have a machine (Ubuntu 16.04.2 LTS) that has just given me the 'not upgraded / kept back' response to 'sudo apt-get upgrade'.

The three items 'not upgraded / kept back' are:

[LIST]
[*]linux-generic 
[*]linux-headers-generic 
[*]linux-image-generic 
[/LIST]

In the past, if I have had this with some program, I have usually done this:
[INDENT]sudo apt-get install --reinstall exampleprogramname[/INDENT]
 
However, given that these three are not just programs, but are more fundamental / low level, I thought it best to ask here how best to resolve this.

For the avoidance of doubt, all other items have upgraded fine, and there is nothing showing to remove.

This is the actual output from sudo apt-get upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

Thank you for any assistance you can provide,

Alan.

---

### Post by deadflowr on 2017-08-11
The packages are held back because they require the installation of new packages and sudo apt-get upgrade does not install new packages.
To install the required new packages you can run
```
sudo apt-get dist-upgrade
```

To note this only updates the current release and does not upgrade that to another, newer, release
(like upgrading from 14.04 to 16.04, it will not do that)

Basically apt-get upgrade only updates packages that exist on the system. But will never install new packages.
apt-get dist-upgrade will install new packages if the updates require them.

---

### Post by Alan5127 on 2017-08-11
Hi deadflowr,

> **deadflowr said:**
> The packages are held back because they require the installation of new packages and sudo apt-get upgrade does not install new packages.
To install the required new packages you can run
```
sudo apt-get dist-upgrade
```

To note this only updates the current release and does not upgrade that to another, newer, release
(like upgrading from 14.04 to 16.04, it will not do that)

Basically apt-get upgrade only updates packages that exist on the system. But will never install new packages.
apt-get dist-upgrade will install new packages if the updates require them.


I had been considering changing my 'script' (string of commands) that I run periodically to change from 'upgrade' to 'dist-upgrade' anyway, so perhaps this confirms that I should.

I currently run the following:

```
sudo apt-get clean && cd /var/lib/apt && sudo mv lists lists.old_`date '+%Y%m%d_%H%M'` && sudo mkdir -p lists/partial && sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

which I got from somewhere (maybe here!) a very long time ago, and at the time, I suspect I had little idea what it was really doing (not that I am any expert now), and I have just never really thought about it until recently (last few months).

So, is there any (significant) downside to me changing that to dist-upgrade as follows?

```
sudo apt-get clean && cd /var/lib/apt && sudo mv lists lists.old_`date '+%Y%m%d_%H%M'` && sudo mkdir -p lists/partial && sudo apt-get clean && sudo apt-get update && sudo apt-get dist-upgrade
``` 


Thanks,

Alan.

---

### Post by deadflowr on 2017-08-11
> So, is there any (significant) downside to me changing that to dist-upgrade as follows?

One downsize might be that the way dist-upgrade works is that if a new packages require an older version to be uninstalled it will uninstall that older version.
I have never seen this to be a problem, myself.

> I had been considering changing my 'script' (string of commands) that I run periodically to change from 'upgrade' to 'dist-upgrade' anyway, so perhaps this confirms that I should.
Two things stand out in the command:
1) you should only need to run the *sudo apt-get clean* command once.
(running it twice it like taking the trash out, then walking back into your home and then walking back out to empty the empty trash can)

2)mv-ing or rm-ing the /var/lib/apt/lists folder should really only be done as a nuclear option.
usually you only need to run that when there is some sort of error from *sudo apt-get update* that produces a reference to that folder, typically a mismatch hashsum error.
Otherwise it's overkill.

(And it also extends the amount of time it takes to generate the output for *sudo apt-get update*, since it has to re download everything from scratch.
Normally, apt reads the hashes from the lists folder files and sees what matches to the hashes from the server, and then updates those which do not match.
So at times some archives do not change a lot, which makes it faster as apt will simply ignore those that it already sees as up-to-date)

If that makes sense.

---

### Post by Alan5127 on 2017-08-11
Hi deadflowr,

> **deadflowr said:**
> One downsize might be that the way dist-upgrade works is that if a new packages require an older version to be uninstalled it will uninstall that older version.
I have never seen this to be a problem, myself.

If this was a server, I might be more cautious, but it is a user machine, so I'm okay with that potential issue.  If anything, I would rather it was running the latest version of things, and old versions get removed, and if it causes a problem, we'll address that for the specific circumstances at the time.

I just ran 'sudo apt-get dist-upgrade' and it worked perfectly - nothing showing there to be updated now.


> **deadflowr said:**
>  Two things stand out in the command:
1) you should only need to run the *sudo apt-get clean* command once.
(running it twice it like taking the trash out, then walking back into your home and then walking back out to empty the empty trash can)

Noted - Definitely don't want to do the trash twice :-) 


> **deadflowr said:**
>  2)mv-ing or rm-ing the /var/lib/apt/lists folder should really only be done as a nuclear option.
usually you only need to run that when there is some sort of error from *sudo apt-get update* that produces a reference to that folder, typically a mismatch hashsum error.
Otherwise it's overkill.

(And it also extends the amount of time it takes to generate the output for *sudo apt-get update*, since it has to re download everything from scratch.
Normally, apt reads the hashes from the lists folder files and sees what matches to the hashes from the server, and then updates those which do not match.
So at times some archives do not change a lot, which makes it faster as apt will simply ignore those that it already sees as up-to-date)

If that makes sense.

Makes perfect sense.  In general, I don't really care how long it takes the updates to run - I normally set them off on a machine, do something else (maybe updates on another machine), and it is done when I check back, but good point.


If I may, there is a command in there that I don't get at all:

```
mkdir -p lists/partial
```

This seems to make a new directory, but it does not get used anywhere else in the command string.  What might be the point of that?

If I run 'sudo ls /var/lib/apt/lists/partial/' the directory is empty.


Thanks,

Alan.

---

### Post by again? on 2017-08-11
The directory /var/lib/apt/lists/partial/ is used for temp storage when updating lists.
The script you're running appears to be more for update error recovery or if you're low on disk space([COLOR="#FF0000"]*[/COLOR]apt-get clean) rather than something you need to run regularly.

"sudo mkdir -p lists/partial" creates the /var/lib/apt/lists/partial/ directory including any parent directories (-p) as needed.
FYI, if I delete the directory /var/lib/apt/lists/ then run an update, the directory and lists are recreated automatically, including the partial folder contained within.

[COLOR="#FF0000"]*[/COLOR]man apt-get
> **clean**
clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/.

**autoclean**
Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control. The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

**autoremove** 
autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed.

Script is just a hodgepodge of unnecessary commands really.

---

### Post by Alan5127 on 2017-08-12
Hi Guys,

I am moving to using 'sudo apt-get dist-upgrade' (rather than upgrade), and I will handle any issues that might cause on the workstation(s) if something gets removed as being 'old'.

One last query:

If I am now using 'sudo apt-get dist-upgrade', should I also periodically run a 'sudo apt autoremove' or is that implicit in dist-upgrade?  The man pages seem to imply that it might be, but they are not explicit in either direction.

If so (meaning that 'sudo apt autoremove' does something that 'sudo apt-get dist-upgrade' does not do), what is that?

dist-upgrade:  may therefore remove some packages.

autoremove:  is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed as dependencies changed or the package(s) needing them were removed in the meantime.


It *seems* like the author of the man page is hedging their bets by saying that dist-upgrade *may* remove some packages if required, rather than saying that it *will* remove some packages if required, but I rather suspect it is me not really understanding, rather than the author :-)


Thanks,

Alan.

---

### Post by again? on 2017-08-12
dist-upgrade only removes installed packages if that is necessary to satisfy dependencies.

autoremove removes packages automatically installed to satisfy dependencies for other packages and are now no longer needed.
So running autoremove periodically will remove packages no longer required by any application.

In my opinion it's safer to use "upgrade" and reserve "dist-upgrade" for when you have particular upgrade errors.

---

### Post by Alan5127 on 2017-08-13
Hi guber2,

That makes perfect sense - I will do that.

Thanks for the help everyone.

Alan.

---

### Post by Bashing-om on 2017-08-13
Alan5127' Hello;

If you are not "hands-on"  and you prefer the system to handle these details for you:
Use the unattended-upgrades package to regularly run autoremove for you. Edit the autoremove setting in /etc/apt/apt.conf.d/50unattended-upgrades from 'false' to 'true' .

Unattended-updates is triggered by a daily cronjob: /etc/cron.daily/apt-compat .
see:
[https://ubuntuforums.org/showthread.php?t=2343732](https://ubuntuforums.org/showthread.php?t=2343732)
[https://ubuntuforums.org/showthread.php?t=2339387](https://ubuntuforums.org/showthread.php?t=2339387)

for other ideas of what unattended-upgrades can do.

[INDENT][INDENT]puts a smile on your face
[/INDENT][/INDENT]

---

### Post by Alan5127 on 2017-08-13
Hi Bashing-om,

> **Bashing-om said:**
> Alan5127' Hello;

If you are not "hands-on"  and you prefer the system to handle these details for you:
Use the unattended-upgrades package to regularly run autoremove for you. Edit the autoremove setting in /etc/apt/apt.conf.d/50unattended-upgrades from 'false' to 'true' .

Unattended-updates is triggered by a daily cronjob: /etc/cron.daily/apt-compat .
see:
[https://ubuntuforums.org/showthread.php?t=2343732](https://ubuntuforums.org/showthread.php?t=2343732)
[https://ubuntuforums.org/showthread.php?t=2339387](https://ubuntuforums.org/showthread.php?t=2339387)

for other ideas of what unattended-upgrades can do.
[INDENT][INDENT]puts a smile on your face
[/INDENT]
[/INDENT]


I will go through those two threads - always good to have a smile on my face!

:)

Thanks,

Alan.

---

