---
title: "Unable to update Ubuntu 22.04 due to Python3 missing"
date: 2023-08-14
forum: General Help
---

### Post by oletkt on 2023-08-14
Hello,

We have installed Virtualizor on a **production **Ubuntu 22.04 server. We had an issue with VNC (couldn't connect to VPS with VNC) so we opened a ticket to Virtualizor to help us solve it.

Following their guidance, we made the following changes:

```
ls -lh /usr/bin/python 
apt-get install python2 -y 
ln -s /usr/bin/python2 /usr/bin/python 
mc 
ls -lh /usr/bin/python 
rm /usr/bin/python3.10 
ls -lh /usr/bin/python 
ln -s /usr/bin/python2 /usr/bin/python 
unlink /usr/bin/python3.10 
ls /usr/bin 
unlink /usr/bin/python 
ls /usr/bin 
ls -lh /usr/bin/python 
ln -s /usr/bin/python2 /usr/bin/python ls -lh /usr/bin/python
```


VNC now works perfectly fine. However, these changes caused another serious issue. We cannot make any updates on Ubuntu.

We tried to make an apt-get update and received the following error:

```
Hit:1 [http://mirror.leaseweb.com/ubuntu](http://mirror.leaseweb.com/ubuntu) jammy InRelease
Hit:2 [http://mirror.leaseweb.com/ubuntu](http://mirror.leaseweb.com/ubuntu) jammy-updates InRelease
Hit:3 [http://mirror.leaseweb.com/ubuntu](http://mirror.leaseweb.com/ubuntu) jammy-backports InRelease
Hit:4 [http://mirror.leaseweb.com/ubuntu](http://mirror.leaseweb.com/ubuntu) jammy-security InRelease
Hit:5 [https://ppa.launchpadcontent.net/eugenesan/ppa/ubuntu](https://ppa.launchpadcontent.net/eugenesan/ppa/ubuntu) jammy InRelease
Hit:6 [https://repo.cloudlinux.com/kernelcare-debian/11](https://repo.cloudlinux.com/kernelcare-debian/11) stable InRelease
sh: 1: /usr/lib/cnf-update-db: not found
Reading package lists... Done
E:  Problem executing scripts APT::Update::Post-Invoke-Success 'if  /usr/bin/test -w /var/lib/command-not-found/ -a -e  /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code
```

We also tried running 

```
/usr/lib/cnf-update-db
```

and got

```
/usr/lib/cnf-update-db: /usr/bin/python3: bad interpreter: No such file or directory
```

Would you be so kind to let us know how do we fix the Ubuntu update issue? Is there any way to install the necessary python3 files?

From what we've read, we should not just go right ahead and install the python3 version needed as this might cause issues. This is why we open this thread to kindly ask you for the best approach on the issue.

Thank you

---

### Post by TheFu on 2023-08-14
Python2 lost all support in 2020 after 15 yrs of warnings.  Any software still dependent on python2 should be considered dead.  
Any Linux distro since 2020 should use python3 and being dependent on that isn't optional.  The virtualizor team made their stuff work, since they consider that the most important thing on any system.  This is unfortunate, since it will effectively break any modern Linux OS.  

You have a choice to make.

If it was me, I'd dump any python2-based software. I don't consider it a difficult choice.

BTW, VNC isn't really the best answer for anything, unless you only have Android clients, perhaps a tablet.

Always remember, Unix-like OSes will let us do foolish things because they don't know if we are being stupid or genus OR both.  Just because it is possible, that doesn't mean it is a good idea.

---

### Post by oletkt on 2023-08-14
> **TheFu said:**
> Python2 lost all support in 2020 after 15 yrs of warnings.  Any software still dependent on python2 should be considered dead.  
Any Linux distro since 2020 should use python3 and being dependent on that isn't optional.  The virtualizor team made their stuff work, since they consider that the most important thing on any system.  This is unfortunate, since it will effectively break any modern Linux OS.  


Hello.

Well we all know that. You're totally right saying it. However, as Virtualizor is the software we use at the moment (and most likely will continue to use for the next 1-3 years as there are not good-enough alts for us), there isn't much we can do and we have to rely to whatever they do. 

With that said, we proceeded fixing the issue. As we've seen it posted about a dozen times before, i'll post below what we did for future reference.

**IF ANYONE HAS A BETTER WAY FIXING IT, PLEASE BE SO KIND TO POST IT BELOW FOR FUTURE REFERENCE.**

When we were trying to make

```
apt-get update
```

we were receiving the errors

```
E:  Problem executing scripts APT::Update::Post-Invoke-Success 'if  /usr/bin/test -w /var/lib/command-not-found/ -a -e  /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code
```

After searching online we saw that it was an issue with the fact that we were not using python3 but rather python2.

So we ran

```
apt-get install python3
```

only to find out that we were already using python3

```
python3 is already the newest version (3.10.6-1~22.04).
```

Upon checking (again) what python version we were using, we ran

```
ls -lh /usr/bin/python
```

This returned

```
/usr/bin/python -> /usr/bin/python2
```

So we ran

```
unlink /usr/bin/python 
```

and when ran

```
ls -lh /usr/bin/python
```

we got

```
ls: cannot access '/usr/bin/python': No such file or directory
```

Next move was to link python3 so we ran

```
ln -s /usr/bin/python3 /usr/bin/python
```

and then

```
ls -lh /usr/bin/python
```

which returned

```
/usr/bin/python -> /usr/bin/python3
```

We ran again

```
sudo apt update
```

but the error persisted. 

```
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if  */usr/bin/test -w /var/lib/command-not-found/* -a -e  /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi' 
E: Sub-process returned an error code 
```

So we went to

```
apt upgrade
```

which (Thank God) proceeded and ended correctly.

Finally we verified that we could ran without any errors the

```
sudo apt update
```

and saw that it did finish just right.



The issue now is that we no longer have access to our VPS with VNC (it doesn't work).

**If we made any mistakes in the process or if we want to mention anything to help us become better, please kindly do let us know.**

Thank you. :)

---

### Post by #&amp;thj^% on 2023-08-14
> **oletkt said:**
> 

The issue now is that we no longer have access to our VPS with VNC (it doesn't work).


I'm just throwing this out to consider, with:
```
apt show python-is-python3 -a
Package: python-is-python3
Version: 3.11.4-1
Priority: optional
Section: python
Source: what-is-python (14)
Maintainer: Matthias Klose  <doko@debian.org>
Installed-Size: 15.4 kB
Depends: python3
Breaks: python, python-dev-is-python2, python-dev-is-python3 (<< 3.11.1-2), python-is-python2, python-is-python2-but-deprecated, python-minimal
Replaces: python, python-dev-is-python2, python-dev-is-python3 (<< 3.11.1-2), python-is-python2, python-is-python2-but-deprecated, python-minimal
Cnf-Ignore-Commands: python
Download-Size: 3,044 B
APT-Sources: https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
Description: symlinks /usr/bin/python to python3
 Starting with the Debian 11 (bullseye) and Ubuntu 20.04 LTS (focal)
 releases, all python packages use explicit python3 or python2
 interpreter and do not use unversioned /usr/bin/python at all. Some
 third-party code is now predominantly python3 based, yet may use
 /usr/bin/python.
 .
 This is a convenience package which ships a symlink to point
 the /usr/bin/python interpreter at the current default python3. It may
 improve compatibility with other modern systems, whilst breaking some
 obsolete or 3rd-party software.
 .
 No packages may declare dependencies on this package.

Package: python-is-python3
Version: 3.11.1-3
Priority: optional
Section: python
Source: what-is-python (13)
Maintainer: Matthias Klose  <doko@debian.org>
Installed-Size: 15.4 kB
Depends: python3
Breaks: python, python-dev-is-python3 (<< 3.11.1-2), python-is-python2, python-is-python2-but-deprecated, python-minimal
Replaces: python, python-dev-is-python3 (<< 3.11.1-2), python-is-python2, python-is-python2-but-deprecated, python-minimal
Cnf-Ignore-Commands: python
Download-Size: 3,000 B
APT-Sources: http://deb.debian.org/debian bookworm/main amd64 Packages
Description: symlinks /usr/bin/python to python3
 Starting with the Debian 11 (bullseye) and Ubuntu 20.04 LTS (focal)
 releases, all python packages use explicit python3 or python2
 interpreter and do not use unversioned /usr/bin/python at all. Some
 third-party code is now predominantly python3 based, yet may use
 /usr/bin/python.
 .
 This is a convenience package which ships a symlink to point
 the /usr/bin/python interpreter at the current default python3. It may
 improve compatibility with other modern systems, whilst breaking some
 obsolete or 3rd-party software.
 .
 No packages may declare dependencies on this package.

```

---

### Post by MAFoElffen on 2023-08-14
I find it curious that it says it supports Ubuntu 18 through 22, but recommended installing python2. When I read it's installer docs, it has no mention of python2, except in the section for using VNC with CentOS 8...

I find it curious that the recommend using VNC for connecting to the control panel, when the control panel is [https://ip_address:4084]("http://ip_address:4084"). I mean that is a remote connection, especially if you tunnel the traffic within a GRE, IPsec, SSL, IP-in-IP, SSH, PPTP, SSTP, L2TP, or VXLAN network tunnel.

I do not know the details of what they are using that requires python 2.7. But if you 'are' using differing versions of Python on a system, you usually use either PyENV or update-alternatives... So that you keep them isolated and can switch between.

The last thing I find curious, is that you didn't ask the vendor what happened, when following their instructions, broke the system.

Just curiosities... Especially when dealing with the config for a production server.

---

### Post by Ralph L on 2023-08-29
This may or may not be helpful for you. I run python windows organizer. I find it very useful to fit windows on my laptop screen. pywo needs Python 2.7.  I installed python 2.7 following instruction in this website: [https://linux.how2shout.com/how-to-install-python-2-on-ubuntu-22-04-lts-jammy-linux/](https://linux.how2shout.com/how-to-install-python-2-on-ubuntu-22-04-lts-jammy-linux/) . 
I changed /usr/bin/python to /usr/bin/python.old for alternatives (I don't remember why I used that name; normally I would just have used python.old)
I put a symbolic link in /usr/bin/ to link “python” to point to /usr/bin/python2.7. 

From the pywo error message and looking at line 34 of pywo I could see that it was looking for Xlib in /usr/lib/python2.7/dist-packages/. I used thunar to look at the that location in xubuntu 18.04 and could see that 18.04 had a bunch of stuff in dist-packages, but 22.04 had only 2 items. So I renamed 22.04 dist-packages “dist-packages.old and copied the folder dist-packages from 18.04 to replace the original dist-packages in 22.04. This seemed to work and I am now running pywo in xubuntu 22.04.

Everything seems to work in xubuntu 22.04. I have no problem with updates.

---

### Post by TheFu on 2023-08-29
Maybe using software that is over 3 yrs passed end of life isn't a good idea?  Support for python2 ended in 2020.  It is dead.  [https://www.python.org/doc/sunset-python-2/](https://www.python.org/doc/sunset-python-2/)

---

