---
title: "Reinstall all packages without installation"
date: 2008-01-04
forum: General Help
---

### Post by Marcelo Ramone on 2008-01-04
[SIZE=3]**[FONT=Palatino Linotype][COLOR=#000000]I would like to download all the packages that I have installed on my Ubuntu, but last week I did an autoclean, I want to only save the packages in the cache, not install them, in order to burn a cd with aptoncd[/COLOR][/FONT]**[/SIZE]

---

### Post by plucky on 2008-01-05
> I did an autoclean

>  autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

```
cd  /var/cache/apt/archives
ls -l
```

to see if your packages are still there.

Good luck

---

### Post by Marcelo Ramone on 2008-01-05
[B]marcelo@linux:~$ cd /var/cache/apt/archives/
marcelo@linux:/var/cache/apt/archives$ ls -la
total 88
drwxr-xr-x 3 root root 77824 2008-01-05 01:45 .
drwxr-xr-x 3 root root  4096 2008-01-05 02:51 ..
-rw-r----- 1 root root     0 2008-01-05 03:53 lock
drwxr-xr-x 2 root root  4096 2008-01-04 23:11 partial
marcelo@linux:/var/cache/apt/archives$ 

I removed all packages from my apt cache some days ago, and I'm looking for a way to get missed packages to make a additional CD with AptonCD.

I try with "sudo apt-get install -f" and "sudo apt-get --reinstall" , and reinstall all packages with sinaptyc but [SIZE=3][FONT=Palatino Linotype][COLOR=#000000]it is impossible I get a errors and the packages can´t be downloaded[/COLOR][/FONT][/SIZE]
[/B]

---

### Post by joehack on 2008-01-06
Try ```
sudo apt-get install --reinstall [PACKAGE] 
```

Jochen

---

### Post by Marcelo Ramone on 2008-01-06
OK, done.

But, What about the Dependencies?

---

### Post by Lumenary on 2008-03-21
Hello All,


This problem had been vexing me as well, but after searching far-and-wide for info on this topic, I managed to stumble upon a simple Bash shell script at debianHELP.org that tackles a similar issue.  I took the script I found and modified it so it's a bit less "draconian" with regard to package reinstallation.


The modified script, presented below, uses dpkg to iterate through and reinstall all packages listed as installed by the package management database.  Each package is installed individually; this gets around "package x pre-depends on package y" errors.


Also, the script skips certain packages, namely apt- and dpkg- related packages (because you don't want your package manager to change mid-stream), and packages relating to mysql and mythtv (because these packages don't take too well to non-interactive configuration).  Feel free to add your own additional exception patterns to the [FONT="Fixedsys"][COLOR=Blue]egrep[/COLOR][/FONT] command embedded within the script.


Because the script reinstalls packages one at a time, it isn't fast, but it does get the job done.  On an Intel 2.4GHz Q6600 with 2GB of RAM, a fast SATA-II drive, and using Kubuntu Gutsy (32-bit), the script will reinstall anywhere from 250 to 750 packages an hour, depending on the state of the package cache and other factors.


To use the script, follow the steps below:


Step 0:  Backup all of your data.


Step 1:  Open a plain text editor, and copy/paste the following code:

```
[COLOR=Blue]#!/bin/bash

for pkg in `dpkg --get-selections | awk '{print $1}' | egrep -v '(dpkg|apt|mysql|mythtv)'` ; do apt-get -y --force-yes install --reinstall $pkg ; done
[/COLOR]
```

[INDENT]:!: [COLOR=Sienna]Important:  The commands "[COLOR=Blue]for pkg ... done[/COLOR]" should all be on the same line.[/COLOR][/INDENT]


Step 2:  Save the file with an appropriate name, such as:

[INDENT][COLOR=Green]reinstall_all.sh[/COLOR][/INDENT]


Step 3:  Open a Bash shell, change the script's owner to "root", and make it executable:

[INDENT][COLOR=Red]sudo chown root:root reinstall_all.sh
sudo chmod 755 reinstall_all.sh[/COLOR][/INDENT]


Step 4:  Execute the script:

[INDENT][COLOR=Red]sudo ./reinstall_all.sh[/COLOR][/INDENT]


I hope this helps...


[I]Script based upon solution presented by Tod Detre on debianHELP.org at 2007-09-20 17:00.

[INDENT][[COLOR=Green]http://www.debianhelp.org/node/10487[/COLOR]]("http://www.debianhelp.org/node/10487")[/INDENT][/I]

---

### Post by wolfgangpauli on 2008-04-07
This script is really nice. However, I inserted a "| egrep -v deinstall" so that it does not reinstall packages that have deinstall status.

for pkg in `dpkg --get-selections | egrep -v deinstall | awk '{print $1}' | egrep -v '(dpkg|apt|mysql|mythtv)'` ; do apt-get -y install --reinstall $pkg ; done

---

