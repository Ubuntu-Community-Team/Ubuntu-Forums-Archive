---
title: "Porblem with update manager"
date: 2007-11-03
forum: General Help
---

### Post by utrex on 2007-11-03
I tried to install "avast4server-3.0.1-i586.deb", this is a deb package from the AVAST antivirus.
The package refused to install and then refused to be removed. I cannot longer update my Ubuntu.
I searched the web for answers, but all of them failed. I tried the following as root:

**First try:**   apt-get remove --purge avast4server-3.0.1-i586
**Answer**:
root@fausto-laptop:/home/fausto/etc# apt-get remove --purge avast4server-3.0.1-i586
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package avast4server needs to be reinstalled, but I can't find an archive for it.

**Second try**:
root@fausto-laptop:/home/fausto/etc# dpkg --force-all --purge avast4server-3.0.1-i586
**Answer**:
dpkg - warning: ignoring request to remove avast4server-3.0.1-i586 which isn't installed.

**Third try**:
root@fausto-laptop:/home/fausto/etc# dpkg --remove --force-remove-reinstreq avast4server-3.0.1-i586
**Answer**:
dpkg - warning: ignoring request to remove avast4server-3.0.1-i586 which isn't installed.

---

### Post by Maestro23 on 2007-11-03
> **utrex said:**
> I tried to install "avast4server-3.0.1-i586.deb", this is a deb package from the AVAST antivirus.
The package refused to install and then refused to be removed. I cannot longer update my Ubuntu.
I searched the web for answers, but all of them failed. I tried the following as root:

**First try:**   apt-get remove --purge avast4server-3.0.1-i586
**Answer**:
root@fausto-laptop:/home/fausto/etc# apt-get remove --purge avast4server-3.0.1-i586
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package avast4server needs to be reinstalled, but I can't find an archive for it.

**Second try**:
root@fausto-laptop:/home/fausto/etc# dpkg --force-all --purge avast4server-3.0.1-i586
**Answer**:
dpkg - warning: ignoring request to remove avast4server-3.0.1-i586 which isn't installed.

**Third try**:
root@fausto-laptop:/home/fausto/etc# dpkg --remove --force-remove-reinstreq avast4server-3.0.1-i586
**Answer**:
dpkg - warning: ignoring request to remove avast4server-3.0.1-i586 which isn't installed.

Try:

sudo dpkg --remove --force-remove-reinstreq avast4server-3.0.1-i586

If it works, then:
> 
sudo apt-get update

sudo apt-get upgrade

---

### Post by utrex on 2007-11-03
I tried what you told me: sudo dpkg --remove --force-remove-reinstreq avast4server-3.0.1-i586

But I get this answer:
root@fausto-laptop:/home/fausto/etc# sudo dpkg --remove --force-remove-reinstreq avast4server-3.0.1-i586
dpkg - warning: ignoring request to remove avast4server-3.0.1-i586 which isn't installed.

Could you give me another hint? Thanks.

---

### Post by tgiannak on 2008-02-05
please did anyone solve that problem?? i have the same problem with avast and i can't update please help

---

### Post by tgiannak on 2008-02-07
i guess its an unsolved problem....so i have to install gnome again :(


[B][COLOR="Red"]EDIT
Problem Solved with the command: sudo dpkg --remove --force-remove-reinstreq avast4server[/COLOR][/B]

---

### Post by blackdiamond on 2008-03-15
I got the same problem, but i can't solve it!!!
:confused::confused::confused:

i obtain this

root@blackdiamond-desktop:~# dpkg --remove --force-remove-reinstreq avast4server-3.0.1-i586
dpkg - warning: ignoring request to remove avast4server-3.0.1-i586 which isn't installed.
root@blackdiamond-desktop:~# 

what can i do?
the fact is that so there is no way to update my pc..
and there is no way to install any packages!
help!

bye from Italy

---

### Post by blackdiamond on 2008-03-15
btw i'm using hardy

---

### Post by blackdiamond on 2008-03-15
root@blackdiamond-desktop:~# dpkg --remove --force-remove-reinstreq avast4server
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 205961 files and directories currently installed.)
Removing avast4server ...
.: 93: Can't open /etc/sysconfig/avastd
dpkg: error processing avast4server (--remove):
 subprocess pre-removal script returned error exit status 2
.: 93: Can't open /etc/sysconfig/avastd
invoke-rc.d: initscript avastd, action "restart" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 avast4server


solutions?

---

### Post by blackdiamond on 2008-03-15
I solve in this way

sudo  gedit /var/lib/dpkg/status

in the document i find this

Package: avast4workstation
Status: install ok installed
Priority: extra
Section: alien
Installed-Size: 22144
Maintainer: root <root@sinclair>
Architecture: i386
Version: 1.0.8-2
Depends: libc6 (>= 2.3.2.ds1-21)
Description: avast! antivirus
 avast! is an antivirus package that lets you do both on-demand and
 on-access scanning. It combines excellent detection rates with
 high speed and superior stability of the antivirus engine.
 .
 (Converted from a rpm package by alien version 8.52.)

and i cut it, then save and i solve the problem!!!!
now the update manager works again!

---

### Post by pjfcurran on 2008-06-10
I tried Blackdiamonds solution posted Apr, 2007 - it did allow Synaptic and the Update Manager to run, however my system still did not seem to run right.

I tried the following and it worked...

sudo gedit /var/lib/dpkg/status

in the document find this...

Package: avast4server
Status: deinstall reinstreq half-configured
Priority: extra
Section: alien
.....

and change it to...

Package: avast4server
Status: install ok installed
Priority: extra
Section: alien
....

Next go to the .deb installation package that you downloaded and open it in archive manager.  Extract to your hard disk.  You can now browse to these files to find the 'data.tar.gz' file which is another archive.  Open this as 'root' and find the file 'avastd'  -- it's in the directory (within the archive) called '/./etc/init.d/' 

As 'root', create in your filesystem a directory called /etc/sysconfig/ and then extract 'avastd' to that directory.

Start Synaptic.  It will identify a broken link which is the 'avast4server' package.  You can select this to do a 'Complete Removal'

Removal proceeds without error!

---

