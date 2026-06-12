---
title: "apt-get issue :'("
date: 2005-04-21
forum: General Help
---

### Post by Gandalf on 2005-04-21
hello,
i ran apt-get upgrade today, but an error has occured something about dependicie and i can't use anymore apt-get i always get broken package run apt-get -f install but when i run it i get:
```

wael@nasreddine:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs-data
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
(Reading database ... 140503 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by siebzehn on 2005-04-21
[QUOTE=Gandalf]hello,
i ran apt-get upgrade today, but an error has occured something about dependicie and i can't use anymore apt-get i always get broken package run apt-get -f install but when i run it i get:
```

wael@nasreddine:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs-data
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
(Reading database ... 140503 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```[/QUOTE]
 Try removing knetworkconf  then install kdelibs-data   Once you did this reinstall knetworkconf and all the packages removed when you removed it.

This error happened to me back when I was using debian and this solution worked for me

---

### Post by Gandalf on 2005-04-21
well
```

wael@nasreddine:~$ sudo apt-get remove knetworkconf
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is to be installed
  kubuntu-desktop: Depends: knetworkconf but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
:'( not working also

---

### Post by siebzehn on 2005-04-21
[QUOTE=Gandalf]well
```

wael@nasreddine:~$ sudo apt-get remove knetworkconf
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is to be installed
  kubuntu-desktop: Depends: knetworkconf but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
:'( not working also[/QUOTE]


Did you try  apt-get -f install   ?

---

### Post by Gandalf on 2005-04-21
yes same result as above

---

### Post by siebzehn on 2005-04-21
[QUOTE=siebzehn]Did you try  apt-get -f install   ?[/QUOTE]
 Ok,  try reinstalling  knetworkconf

---

### Post by Gandalf on 2005-04-21
[QUOTE=siebzehn]Ok,  try reinstalling  knetworkconf[/QUOTE]
 but i always get the same result...

---

### Post by siebzehn on 2005-04-21
[QUOTE=Gandalf]but i always get the same result...[/QUOTE]
 The problem should be solved, I'm not sure what's going on.  Don't worry, I'll get back to you in a little while

---

### Post by Firetech on 2005-04-21
I had the same problem and was just waiting for a thread like this.
What you have to do is, like siebzehn said, to remove knetworkconf, BUT bypass apt-get using dpkg directly...
run the following commands (It works, I've done it.):
```
sudo dpkg -r knetworkconf
sudo apt-get -f install
sudo apt-get install knetworkconf
```
This removes knetworkconf, bypassing apt-get, then fixes the problem and installs the new packages, and lastly installs knetworkconf again.

---

### Post by siebzehn on 2005-04-21
[QUOTE=Firetech]I had the same problem and was just waiting for a thread like this.
What you have to do is, like siebzehn said, to remove knetworkconf, BUT bypass apt-get using dpkg directly...
run the following commands (It works, I've done it.):
```
sudo dpkg -r knetworkconf
sudo apt-get -f install
sudo apt-get install knetworkconf
```
This removes knetworkconf, bypassing apt-get, then fixes the problem and installs the new packages, and lastly installs knetworkconf again.[/QUOTE]
 You are right, that's the thing I did when I had the same problem with debian.

Didn't remember...

Thanks for reminding me

---

### Post by fdoving on 2005-04-21
[QUOTE=Gandalf]but i always get the same result...[/QUOTE]
 If your setup hasn't changed much since the first post:
 'sudo dpkg --force-overwrite -i  /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb'

That should do it.


- Frode

---

### Post by Firetech on 2005-04-21
[QUOTE=fdoving]If your setup hasn't changed much since the first post:
 'sudo dpkg --force-overwrite -i  /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb'

That should do it.


- Frode[/QUOTE]
You always learn new stuff here, that one is much easier than mine ;)

---

### Post by Gandalf on 2005-04-21
[QUOTE=fdoving]If your setup hasn't changed much since the first post:
 'sudo dpkg --force-overwrite -i  /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb'

That should do it.


- Frode[/QUOTE]
 that worked thx man

---

### Post by fdoving on 2005-04-21
[QUOTE=Gandalf]that worked thx man[/QUOTE]
 anytime.

---

### Post by Gianni Exile on 2005-04-21
It's better to revert to the working version, other users report problems (menus, usb key mounting, splash screens etc), and wait till it gets fixed.

Another thread on this
[http://ubuntuforums.org/showthread.php?t=28678&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=28678&page=1&pp=10)

Bad idea to override the package manager unless you are an experienced user.  Fine if you know what you're doing, however in general users are best off just waiting a couple of days to update.

---

### Post by bluefrog on 2005-05-04
Read dpkg help.
 
Overwrite pretty much harmless especially in that case where only icons are going to be overwritten.

dpkg --force-help
 < overwrite              Overwrite a file from one package with another >

---

### Post by Jofel on 2005-05-07
I had the same issue with Kubuntu. But the listed solution didn't work for me entirely. I had to add something to it. I can't post the error codes as my language on Kubuntu is Dutch and most of you guys wouldn't understand it at all. :)

But the command ```
sudo dpkg -r knetworkconf
``` caused complaints about the KDE system depending on it. 
After reading the man pages of dpkg I changed the command to this:
```
sudo dpkg -r --force-depends knetworkconf
```

And that did the trick for me. 

Then I proceded with 

```
sudo apt-get -f install
sudo apt-get install knetworkconf
```

---

### Post by James Wilford on 2005-05-10
[QUOTE=Jofel]I had the same issue with Kubuntu. But the listed solution didn't work for me entirely. I had to add something to it. I can't post the error codes as my language on Kubuntu is Dutch and most of you guys wouldn't understand it at all. :)

But the command ```
sudo dpkg -r knetworkconf
``` caused complaints about the KDE system depending on it. 
After reading the man pages of dpkg I changed the command to this:
```
sudo dpkg -r --force-depends knetworkconf
```

And that did the trick for me. 

Then I proceded with 

```
sudo apt-get -f install
sudo apt-get install knetworkconf
```[/QUOTE]
 I'd like to add that I ran the command in Jofel's post, but it seems that all this does is remove and reinstall knetworkconf. Running apt-get upgrade after this gave me the same errors as before. I found that the following sequence did the trick:

> sudo dpkg -r --force-depends knetworkconf
sudo apt-get -f upgrade

---

