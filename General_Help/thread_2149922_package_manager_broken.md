---
title: "package manager broken"
date: 2013-05-30
forum: General Help
---

### Post by phthenry on 2013-05-30
I get this following messages when I open up my software manager:

Items cannot be repaired or installed or removed until the package is repaired.

When I try to repair the package manager, I get the message I posted below.

I have tried everything to fix it, including

sudo apt-get -f install, but get this message:

mysql-server-5.5 (5.5.31-0ubuntu0.12.04.1) breaks mysql-server (<< 5.5.31-0ubuntu0.12.04.1) and is installed.
  Version of mysql-server to be configured is 5.5.29-0ubuntu0.12.04.2.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have MySQL 5.5.31 installed, and I installed it by using the Ubuntu package manager.

Thanks!

Paul


============Original message=================

installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "None.None"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "None.None"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "None.None"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "None.None"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server-5.5 (5.5.31-0ubuntu0.12.04.1) breaks mysql-server (<< 5.5.31-0ubuntu0.12.04.1) and is installed.
  Version of mysql-server to be configured is 5.5.29-0ubuntu0.12.04.2.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 mysql-server
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server-5.5 (5.5.31-0ubuntu0.12.04.1) breaks mysql-server (<< 5.5.31-0ubuntu0.12.04.1) and is installed.
  Version of mysql-server to be configured is 5.5.29-0ubuntu0.12.04.2.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured

-- 
Paul Tremblay
ICQA Program Developer

---

### Post by philinux on 2013-05-30
Try this.

[http://askubuntu.com/questions/292865/upgrade-mysql-server-issue](http://askubuntu.com/questions/292865/upgrade-mysql-server-issue)

---

### Post by phthenry on 2013-05-31
> **philinux said:**
> Try this.

[http://askubuntu.com/questions/292865/upgrade-mysql-server-issue](http://askubuntu.com/questions/292865/upgrade-mysql-server-issue)

Yes, that worked. Thanks!

---

