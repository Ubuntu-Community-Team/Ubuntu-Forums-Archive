---
title: "samba error"
date: 2008-01-30
forum: General Help
---

### Post by Electrical_shock on 2008-01-30
I tried to upgrade samba through synaptic on Ubuntu 6.06 and an error occured.  I'm not sure what happened but I attached a screenshot of the error message and the terminal view of the installation.  How can I fix this problem?

Thanks for you help.

---

### Post by dcstar on 2008-01-31
> **Electrical_shock said:**
> I tried to upgrade samba through synaptic on Ubuntu 6.06 and an error occured.  I'm not sure what happened but I attached a screenshot of the error message and the terminal view of the installation.  How can I fix this problem?

Thanks for you help.

You may be better to firstly manually remove the existing Samba packages, and then install the new ones.

---

### Post by Electrical_shock on 2008-01-31
What is the best way to manually remove Samba?

---

### Post by Electrical_shock on 2008-02-13
How does one manually remove samba?

---

### Post by TransitMan on 2008-02-14
Try this;
```
sudo apt-get purge samba_3.0.22-1ubuntu3.6_i386.deb
Also try sudo apt-get purge samba
```

---

### Post by Electrical_shock on 2008-02-16
> **TransitMan said:**
> Try this;
```
sudo apt-get purge samba_3.0.22-1ubuntu3.6_i386.deb
Also try sudo apt-get purge samba
```

For both I get:
E: Invalid operation purge

---

### Post by Sokertes on 2008-02-17
Have you tried to remove it in synaptic?

sudo apt-get purge

should have worked

what about 

sudo apt-get remove

---

### Post by Electrical_shock on 2008-02-17
> **Sokertes said:**
> Have you tried to remove it in synaptic?

sudo apt-get purge

should have worked

what about 

sudo apt-get remove


*********************************************************************
:~$ sudo apt-get remove samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba
0 upgraded, 0 newly installed, 1 to remove and 62 not upgraded.
Need to get 0B of archives.
After unpacking 7258kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 105124 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
*****************************************************************************
*****************************************************************************
:~$ sudo apt-get remove samba_3.0.22-1ubuntu3.6_i386.deb
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package samba_3.0.22-1ubuntu3.6_i386.deb

---

### Post by Electrical_shock on 2008-02-17
When I open Synaptic I get an error message:
"You have 1 broken package on your system!
Use the "Broken" filter to locate it."

When I try to remove samba thru synaptic I get an error message:
"E: samba: subprocess pre-removal script returned error exit status 102"

---

### Post by Electrical_shock on 2008-05-28
Do I have to go into every folder samba is installed in to remove samba?  Will that fix the issue?

---

### Post by Electrical_shock on 2008-06-19
Tried sudo apt-get remove and got the following.

$ sudo apt-get remove
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.3) but 3.0.22-1ubuntu3.7 is installed
E: Unmet dependencies. Try using -f.





Tried "sudo apt-get -f install" and got the following.

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 103 not upgraded.
Need to get 0B/2852kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 104975 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.3 (using .../samba_3.0.22-1ubuntu3.7_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.7_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bve on 2008-06-26
I'm running into the same issue, has a fix been posted?

---

### Post by riiidaa on 2008-06-26
Exactly the same fault here too, I'm running Dapper 6.06LTS

Was trying to install courier-imap when samba alleged dependencies demanded a downgrade of samba and samba-common from ....3.7 :confused:

---

### Post by riiidaa on 2008-06-26
Read this all the way thru

[http://www.debianhelp.org/node/4073](http://www.debianhelp.org/node/4073)

not tried it yet

---

### Post by riiidaa on 2008-06-26
> **riiidaa said:**
> Read this all the way thru

[http://www.debianhelp.org/node/4073](http://www.debianhelp.org/node/4073)

not tried it yet

Seems to have worked for me, :) Synaptic no longer alarms :guitar:

---

