---
title: "I think a config file is corrupt - help please?"
date: 2007-04-15
forum: General Help
---

### Post by dryder on 2007-04-15
Hi,

I think I must have a corrupt config(?) file somewhere - any help would be very much appreciated.

I am trying to install hylafax-server and hyla-fax-client using 
sudo aptitude update
sudo aptitude install hylafax-server hylafax-client

I have also tried to use synaptic manager.

During the installation process of both methods, they reach a stage where the window goes crazy and rapidily repeats (as far as 
my eyes can detect at such speed) area code () area code () ... the only way of stopping is via system monitor and killing the porocess.

I have now reached a stage where I can see this report:
david@server-ubuntu:~$ sudo aptitude install hylafax-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up hylafax-server (4.3.0-5) ...
ln: creating symbolic link `pdf2fax' to `pdf2fax.gs': File exists
ln: creating symbolic link `ps2fax' to `ps2fax.gs': File exists
sed: can't read /etc/default/hylafax: No such file or directory
dpkg: error processing hylafax-server (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hylafax-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up hylafax-server (4.3.0-5) ...
ln: creating symbolic link `pdf2fax' to `pdf2fax.gs': File exists
ln: creating symbolic link `ps2fax' to `ps2fax.gs': File exists
sed: can't read /etc/default/hylafax: No such file or directory
dpkg: error processing hylafax-server (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hylafax-server

As a newbie I don't know what this is telling me that I can usefully use to correct the error.

Any help would be very much appreciated as I need a fax more versatile the efax, good though efax is.

MTIA,
David

---

### Post by dryder on 2007-04-17
Hi,

This problem is getting worse.

Every time I try to install something by command line or synaptic manager, I get hylafax errors.

I can not even reinstall efax, my previous fax program.

Is anybody able to help me sort this mess out please?

David

---

### Post by nevle on 2007-04-17
i have the same sort of problem except with vmware and synaptic,cant uninstall or upgrade anything.sorry i cant help you...

---

### Post by dryder on 2007-04-17
Hi nevle,

If nothing else at least I'm not alone :(

Let's hope somebody is able to help us  :confused:

---

