---
title: "I really need to get this fixed..."
date: 2007-05-09
forum: General Help
---

### Post by obviouslyshane on 2007-05-09
I've been using Ubuntu now, on my desktop for about a year. I liked it so much (actually i got blue screens every ten minutes with vista), I decided to install it on my laptop. Things went fairly swimmingly, only a few hitches, such as wifi not working out of the box, screen resolution, disabling "tap to click"... but those, are things i expected, this however... I did not expect...

So the icon appeared to notify me that an update was available. I clicked it. This is what it told me:

> Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing gaim (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

I poked around the net for a while, and found nothing, and hoped that maybe it would magically fix itself. So, today i turn on my computer, and it's still messed up, then I learn that, when i go to add/remove programs, I get the following error:

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I haven't touched my sources list, so i doubt that is the problem, however, when i try to run 'sudo apt-get update' This is what happens:

> shane@Lappy:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing gaim (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
shane@Lappy:~$ 


So I'm stuck, I have no idea how to fix this, and I REALLY don't want to do a clean install... Any ideas? :(  :confused:

---

### Post by IgnorantGuru on 2007-05-10
I would first try

```

sudo killall adept
sudo killall dpkg
sudo dpkg --configure -a
sudo aptitude clean

```

---

### Post by strabes on 2007-05-10
Have you checked the permissions of the /var/lib/dpkg/status file?

---

### Post by heimo on 2007-05-10
This is a bit risky, but seems like you need to get it fixed anyway, so I'd try to replace package status file with a backup version, like this:
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-old2
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
sudo apt-get -f install

```If you don't get any errors, you're probably fine. If you still get errors about gaim, try the following:

```
sudo mv /var/lib/dpkg/info/gaim.* /tmp/
sudo apt-get --purge remove gaim
sudo apt-get install gaim

```

---

### Post by obviouslyshane on 2007-05-10
@ Ignorant guru

No process are killed when i run the first two, however, i get this when i run the third

> shane@Lappy:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 12201 package `gaim':
 `Depends' field, reference to `libdbus-1-3': version contains ` '

@Strabes

[IMG]http://img522.imageshack.us/img522/7991/screenshotstatuspropertpl1.png[/IMG]

---

### Post by obviouslyshane on 2007-05-10
@ heimo

Thank you so much! that did the trick!

---

