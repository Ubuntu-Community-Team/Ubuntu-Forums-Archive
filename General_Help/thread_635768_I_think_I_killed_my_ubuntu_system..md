---
title: "I think I killed my ubuntu system."
date: 2007-12-09
forum: General Help
---

### Post by gwyrlim on 2007-12-09
Hi.
I have a server running 6.04(I think) and last night I decided to remove some non used application like games,codecs and gimp. I also removed nvida driver since I have a G200 card. The server is used for picture backup and it has a 1-wire network and loggs some temperatures. It act as my DHCP and a experimental web server running joomla.  
I used the synaptic package manager but something went wrong and it told me to run "dkpg --configure -a" to fix the problem and W: Not using locking for read only lock file /var/lib/dpkg/lock
Running that gives me this. dpkg: unable to access dpkg status area: Read-only file system

I access this server using nx but that is no longer possible. I only access it now using putty.
It is possible to connect to the web but I get some DB errors.

I have tried apt-get update but it ends in   
...
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages - open (30 Read-only file system)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages - open (30 Read-only file system)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_dapper-security_main_source_Sources - open (30 Read-only file system)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_source_Sources - open (30 Read-only file system)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages - open (30 Read-only file system)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_dapper-security_universe_source_Sources - open (30 Read-only file system)
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I have tried.(not knowing what it rely does but others seams to have had some success with it,running man depmod gives man: can't create a temporary filename: Read-only file system).
sudo depmod -a
gives:
FATAL: Could not open /lib/modules/2.6.15-28-686/modules.dep.temp for writing: Read-only file system

I cant start gedit, comand not found.

I'm a little surprise that I could brake the system using the package manager.
Any suggestions to what to do?

---

### Post by PmDematagoda on 2007-12-09
Try doing an fsck on the drive using the Live CD, that could help.

---

### Post by Sef on 2007-12-09
> I have tried.

Did you run ```
sudo dpkg --configure -a
``` or not?  It is not clear to me by your message if you have.

---

### Post by PmDematagoda on 2007-12-09
Sef, gwyrlim's Ubuntu file system is mounted read-only, this is what is attributing to the apt-get problem, once that is solved, everything else will be solved along with it.

---

### Post by gwyrlim on 2007-12-09
> **PmDematagoda said:**
> Sef, gwyrlim's Ubuntu file system is mounted read-only, this is what is attributing to the apt-get problem, once that is solved, everything else will be solved along with it.

Any suggestions how to investigate/fix that?


Sef, yes running the command gave me dpkg: unable to access dpkg status area: Read-only file system.

---

### Post by PmDematagoda on 2007-12-09
I gave the answer earlier, run an fsck on the drive through a Live CD.

---

### Post by gwyrlim on 2007-12-09
> **PmDematagoda said:**
> I gave the answer earlier, run an fsck on the drive through a Live CD.

Ok, sorry. Why the Live CD and not through the putty client? It's just that I had some problems with the video card and monitor (that why  I run NX)so as long as I have this putty up and running I would like to use it unless it's not possible or not recommended.

---

### Post by gwyrlim on 2007-12-09
Looks like I got it. Could not get a CD player to boot the live cd but during normal boot the file system errors were detected and it asked me to run fsck manually. That fixed the problem. Now I just need to restore the gnome gui, must have removed some important parts.

Many thanks!

---

### Post by PmDematagoda on 2007-12-09
You can restore the GUI using:-

```
sudo aptitude install ubuntu-desktop
```

---

