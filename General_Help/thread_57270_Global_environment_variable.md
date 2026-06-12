---
title: "Global environment variable"
date: 2005-08-15
forum: General Help
---

### Post by arlie on 2005-08-15
I'm new to linux and I have no idea whatsoever about linux admin but I'm learning. How do I set the environment variables below so that it would available to all users. Please Help!

#
# Sybase Product Environment variables
#
SYBASE="/opt/sybase"
export SYBASE
SYBASE_OCS="OCS-12_5"
export SYBASE_OCS
PATH="/opt/sybase/OCS-12_5/bin":$PATH
export PATH
LD_LIBRARY_PATH="/opt/sybase/OCS-12_5/lib:/opt/sybase/OCS-12_5/lib3p":$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
INCLUDE="/opt/sybase/OCS-12_5/include":$INCLUDE
export INCLUDE
LIB="/opt/sybase/OCS-12_5/lib":$LIB
export LIB
SYBASE_JRE="/opt/sybase/shared-1_0/JRE-1_3"
export SYBASE_JRE
PATH="/opt/sybase/JS-12_5/bin":$PATH
export PATH
SYBASE_SYSAM="SYSAM-1_0"
export SYBASE_SYSAM
LM_LICENSE_FILE="/opt/sybase/SYSAM-1_0/licenses/license.dat"
export LM_LICENSE_FILE
SYBASE_ASE="ASE-12_5"
export SYBASE_ASE
PATH="/opt/sybase/ASE-12_5/bin:/opt/sybase/ASE-12_5/install":$PATH
export PATH
LD_LIBRARY_PATH="/opt/sybase/ASE-12_5/lib":$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
PATH="/opt/sybase/RPL-12_5/bin":$PATH
export PATH

---

### Post by amohanty on 2005-08-15
A useful resource to understanding login and customizations:
[http://supportweb.cs.bham.ac.uk/howto/login/](http://supportweb.cs.bham.ac.uk/howto/login/)

HTH
AM

---

### Post by arlie on 2005-08-17
[QUOTE=amohanty]A useful resource to understanding login and customizations:
[http://supportweb.cs.bham.ac.uk/howto/login/](http://supportweb.cs.bham.ac.uk/howto/login/)

HTH
AM[/QUOTE]
 I tried creating .login file in /home but I don't think .login was ever executed by ubuntu. I'm new to linux and I really find all this confusing. Is there a simple step or easier way to set my environment variables globally because none has worked so far.

I'm trying to make Sybase ASE Server Express Edition run on Ubuntu. Only Red Hat, Red Flag, Turbo Linux and SUSE are officialy recognized by Sybase to be capable of running Sybase SQL Server and I would like to include Ubuntu on that list. If I'm successful with this, Ubuntu would be our official linux server for Sybase here in Cebu City, Philippines. Our company is a business software developer and distributor of Sybase SQL Server.

By the way, this my first time to try linux and I'm trying to convince top manangement that linux is the wave of the future.

We have a large client base that we can migrate linux.

---

### Post by amohanty on 2005-08-18
Technically .login should be executed everytime you login. 
Can you post the .login file?

To set it on a system wide basis, set it in the /etc/environment.
Remember its not the same as a .login (ie its not a bash script) so you do not set the env variables as you do in .login:
export ENV_VARIABLE='value'

In /etc/environment all you need to do is:
ENV_VARIABLE='value'

HTH
AM

---

### Post by arlie on 2005-08-20
[QUOTE=amohanty]Technically .login should be executed everytime you login. 
Can you post the .login file?

To set it on a system wide basis, set it in the /etc/environment.
Remember its not the same as a .login (ie its not a bash script) so you do not set the env variables as you do in .login:
export ENV_VARIABLE='value'

In /etc/environment all you need to do is:
ENV_VARIABLE='value'

HTH
AM[/QUOTE]

Where can I find the .login file?

---

### Post by amohanty on 2005-08-25
It should be in /home/<username>

If it is not there, create one.

AM

---

### Post by arlie on 2005-08-27
[QUOTE=amohanty]It should be in /home/<username>

If it is not there, create one.

AM[/QUOTE]

Will .login be executed even if I don't open the terminal window. I need the environments variables to be set before running sybase which I have a desktop shortcut/launcher.

---

### Post by amohanty on 2005-08-27
Technically it should be executed everytime you login. 
The easiest way to check is to launch a program from it.

AM

---

### Post by amohanty on 2005-08-27
Look for default.session and put it in there. If you want it on a per user basis you will need to setup a session via System->Preferences->Sessions.

---

