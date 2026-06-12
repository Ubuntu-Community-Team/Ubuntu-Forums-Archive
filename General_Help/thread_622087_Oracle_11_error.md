---
title: "Oracle 11 error"
date: 2007-11-24
forum: General Help
---

### Post by LoquitoSlack on 2007-11-24
When installing oracle 11 in ubuntu-server 7.10, I get the following error... 

To install the oracle 11 using the manual this website


========================================================	
Checking the requirements of the operating system ...
 	
Expected score: A enterprise-4,enterprise-5,redhat-4,redhat-5,SuSE-10,asianux-2,asianux-3
	
Real score: (Operating System Version unknown)
	
Checking finished. The overall result of this check is: Judgment <<<<
	
Problem: Oracle Database 11g is not certified in the current operating system.
Recommendation: Be sure to install the software on the platform correct.
========================================================

thank you

---

### Post by IcemanV9 on 2007-11-24
Happened to me a couple of years ago ...

```
./runInstaller -ignoreSysPrereqs
```

---

### Post by LoquitoSlack on 2007-11-24
If, wrote this option  . / RunInstaller -ignoreSysPrereqs
And I came this mistake

Which will be the problem?

Thanks


kike

---

### Post by IcemanV9 on 2007-11-26
What was the error message?

---

### Post by LoquitoSlack on 2007-11-28
The error message was:

./runInstaller -ignoreSysPrereqs
Checking the requirements of the operating system …
Expected score: One of enterprise-4, enterprise-5, redhat-4, redhat-5, SuSE-10, asianux-2, asianux-3
Real score: (Operating System Version unknown)
Checking finished. The overall result of this check is: Judgment <<<<
Problem: Oracle Database 11g is not certified in the current operating system.
Recommendation: Be sure to install the software on the platform correct.
================================================== ======

Testing requirements bundle operating system …
Checking finished. The overall result of this check is not performed <<<<
OUI-18001: The operating system ‘Linux version (Operating System Version unknown)’ is not supported.
Recommendation: Set up packages required before proceeding with the installation.
================================================== ======

Checking kernel parameters
Checking finished. The overall result of this check is not performed <<<<
OUI-18001: The operating system ‘Linux version (Operating System Version unknown)’ is not supported.
Recommendation: Follow the specific instructions of the operating system to upgrade the kernel parameters.
================================================== ======

Checking version of glibc Recommended
Checking finished. The overall result of this check is not performed <<<<
OUI-18001: The operating system ‘Linux version (Operating System Version unknown)’ is not supported.
Recommendation: There can be installed packages that make them are obsolete, in which case, you can pick up correctly with the installation. If not, it is recommended that does not continue. See technical notes on the product version to obtain the missing packages and upgrade the system.


But already settled, only activating options myself, 
And adding to / etc / profile
Export ORACLE_SID = orcl
Where is my orcl database
thank for the help
kike
lima-peru

---

### Post by IcemanV9 on 2007-11-29
Great! Glad you got it up and running.

Where is your Oracle DB? On my box, it is in /usr/lib/oracle directory.

```
whereis oracle
```

---

### Post by LoquitoSlack on 2007-12-03
Thank you friend, I came all right but you want to add export ORACLE_SID = orcl
Orcl where is the name of the database

Doing that I am glad I ran Linux is more than a feeling …
Kike

---

