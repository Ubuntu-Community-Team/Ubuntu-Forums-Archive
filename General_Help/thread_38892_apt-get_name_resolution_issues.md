---
title: "apt-get name resolution issues"
date: 2005-06-02
forum: General Help
---

### Post by Craig Prevallet on 2005-06-02
I have the following problem:

penguin@Longhorn:~$ sudo apt-get install ace-of-penguins
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  ace-of-penguins
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 225kB of archives.
After unpacking 561kB of additional disk space will be used.
0% [Connecting to us.archive.ubuntu.com (1.0.0.0)]

The connection never completes.  The DNS number (1.0.0.0) looks wrong to me. 
However the connection proceeds if I fire up a browser and type in the host name (us.archive.ubuntu.com).  I'm on an ADSL internet connection and can ping just fine.  Any ideas?

---

### Post by arnieboy on 2005-06-02
try doing a "sudo apt-get update" and let me know what it says. Also copy and paste the contents of /etc/apt/sources.list

---

### Post by Craig Prevallet on 2005-06-02
Thanks for the reply

penguin@Longhorn:~$ sudo apt-get update
Password:
50% [Connecting to us.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
penguin@Longhorn:~$
penguin@Longhorn:~$ cat /etc/apt/sources.list
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary multiverse

---

### Post by arnieboy on 2005-06-02
alright. do the following:
in terminal type: sudo gedit /etc/apt/sources.list
when the file opens up, delete everything in it and paste the following:

##START COPYING FROM HERE
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

##deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
##deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

##DO NOT COPY FROM HERE

Save the file and exit. Now do a "sudo apt-get update" again and tell me what happens.

---

### Post by Craig Prevallet on 2005-06-02
penguin@Longhorn:~$ sudo apt-get update
0% [Connecting to us.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting to archive.ubuntu.com

But if I point my browser (Konqueror) to 

[http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/)

I get

penguin@Longhorn:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
99% [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to backports.ubuntuforu

Note that only the site I point the browser to seems to update.

Weird, huh?

---

### Post by arnieboy on 2005-06-02
did you configure your firewall (iptables) to max security? I think thats causing the problems. u shd try installing "firestarter" which is a nice GUI frontend to iptables and see whats being stopped and whats not. U can change lots of permissions from firestarter.
if apt-get works (pointing your browser trick which u have discovered), u can install it as:
sudo apt-get install firestarter. 
If it does not work, you can download it explicitly by googling for it.
run firestarter from menu.

---

### Post by Craig Prevallet on 2005-06-02
I ran firestarter but didn't get far.  The wizard came up and I went through it but got stuck when the save button I needed to press to proceed was greyed out (how'd that happen?)  

I did an NMAP scan on my router and found

penguin@Longhorn:~$ nmap 192.168.1.1

Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-06-02 20:23 BST
Interesting ports on mygateway.ar7 (192.168.1.1):
(The 1661 ports scanned but not shown below are in state: closed)
PORT   STATE SERVICE
23/tcp open  telnet
80/tcp open  http

I didn't configure the modem/router myself (my wife's company did) but they changed the admin password so I don't believe I can open up ports on it.

I would have thought that port 80 would have been sufficient for apt but that's just a guess. 

Thanks for the help thus far and any further advice would be appreciated.

---

