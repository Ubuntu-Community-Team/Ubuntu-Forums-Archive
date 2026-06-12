---
title: "Password doesn't work in Konsole."
date: 2007-07-12
forum: General Help
---

### Post by Pepse3 on 2007-07-12
I can't get my password to work in a Konsole.  I type SU hit enter and then type my password and the error is:  su: Authentication failure  Sorry.  I was a Mandriva user for 6 years and don't recall having problems getting in to a Konsole.  So, what is the trick here?  I need to try to get libdvdcss so I can play DVD's, and from what I have seen on some other posts I need to use SUDO, and that is apparently a Konsole based system.

Pepse.

---

### Post by pxwpxw on 2007-07-12
in ubuntu by default su will not work in a console, there is no root password.
You need to use sudo <command>
or if in a desktop terminal gksu  <command>

---

### Post by scxtt on 2007-07-12
if you've already launched konsole, try: **sudo su -** and enter your user's password.

---

### Post by Pepse3 on 2007-07-12
OK, that is good.  Now where do I find a tutorial on acquiring software for Kubuntu 7.04?  For starters I need to get libdvdcss so I can watch DVD's.  This is definitely greek to me compared to Mandriva.  It seems some things are available through Adept Manager and others through SUDO.

Later. Pepse.

---

### Post by scxtt on 2007-07-13
software isn't available via sudo, sudo isn't a package manager or anything like that ... sudo just allows a normal user account to run commands as root ...

for your specific "problem", i'd do: **sudo aptitude search libdvd** and install any package it returns ... then there's a script (installed w/ libdvdread or libdvdcss) that will sort things out ...

---

### Post by Nythain on 2007-07-13
you are going to have to research apt/apt-get/aptitude and how to edit your /etc/apt/sources.list file to include other repositories to find software outside of the standard ubuntu repo

libdvdcss2 is the dvd package you are wanting, and i think its in the medibuntu repo, or possibly in the ubuntu universe or multiverse repo...

synaptic is a great gtk front end for apt so you dont have to do everythign in teh command line

and my advice on the su bit... dont use it... just use sudo and gksudo... there's reasons why ubuntu defaults to no root password and account login... remaining in root and playing around can seriously jeopardize your install

Edit: i know adept is the package manager that comes with kubuntu vs. synaptic wich comes with ubuntu, and synaptic is gtk based and will require download and running the gnome libraries, but in this case i consider it seriously worth it... its one of the few gtk apps i would install in kde because adept BLOWS!!!

---

### Post by Pepse3 on 2007-07-13
This is where I am going to look stoopid.  What?  Nythain states do not use SU, but use SUDO or GKSUDO because of the hazards of working in root.  OK, aren't sudo and gksudo found in a konsole (which is root)??  BUT, on the other hand I will look into downloading synaptic.  I went to adept pkg mngr and searched for synaptic and it has given me 12 synaptic related files.  The one I assume I need is the one with a Ubuntu logo next to it.  Then by downloading synaptic I presume it will show up in my KDE>SYSTEM area?  Is synaptic going to be enough?  Or do I still go to a konsole and sudo the libdvdcss file?  

Later. Pepse.

---

### Post by scxtt on 2007-07-13
"konsole" is an xterm (X Terminal) frontend - it's just the CLI, has NOTHING to do w/ package management and isn't inherently "root" -- you can use sudo to gain root privileges IN konsole, but you can do that in ANY xterm frontend for any DE ...

sudo = run a CLI command as root
gksudo = run a GUI program as root

the version of synaptic you want to install is just called "synaptic" - running **sudo aptitude install synaptic** from konsole will install it for you ...

synaptic isn't going to make your DVD's play - you need to install the libdvd* packages and possibly run a script they provide to get CSS working ...

---

### Post by Pepse3 on 2007-07-13
OK, so I went to a konsole (terminal) and typed " sudo aptitude search libdvd " and the reply is: 

p  libdvdnav-dev  - The DVD navigation library, developement pa

p  libdvdnav4  - The DVD navigation library

p   libdvdplay0  - portable extraction library for DVD menus

p   libdvdplay0-dev   - developement files for libdvdplay0

p   libdvdread-dev   - library for reading DVDs (development)

i  libdvdread3  - library for reading DVDs
v   libdvdread3-dev   -

 So, do I go to a konsole and " sudo aptitude search xxxx" each item it found in that search or ............??

Pepse.

---

### Post by aysiu on 2007-07-13
**Install *libdvdcss2***
Paste these commands in the Konsole: ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-1plf3_i386.deb
```

**Understand software installation in Kubuntu**
Read this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

**Understand using *sudo* instead of *su***
Read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by scxtt on 2007-07-13
aptitude does what you tell it to do - no more, no less ...

aptitude search <package> = search for a package
sudo aptitude install <package> = install a package
sudo aptitude remove <package> = remove a package

---

### Post by aysiu on 2007-07-13
If you're searching, you don't even need *sudo* ```
aptitude search *packagename*
``` will suffice.

---

### Post by Pepse3 on 2007-07-17
OK, I have never been good at cut & paste so I went to a konsole and typed the  whole shpiel Aysiu gave.  Well it installed everything that I listed and DVD's still don't play.  And I don't recall it asking to do any more than I did.  So, I assume I am still missing something.

Pepse.

---

