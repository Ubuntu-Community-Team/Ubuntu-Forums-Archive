---
title: "dpkg error"
date: 2013-06-01
forum: General Help
---

### Post by GirishAvinashPatil on 2013-06-01
Hello All,

Am getting following error while launching Ubuntu Software Center [/B]

```
installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.28-0ubuntu0.12.04.2); however:
  Version of mysql-server-core-5.5 on system is 5.5.31-0ubuntu0.12.04.1.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.28-0ubuntu0.12.04.2); however:
  Version of mysql-server-core-5.5 on system is 5.5.31-0ubuntu0.12.04.1.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
```


Any one has some clue about this issue...
Any help would be greatly appretiated..............

---

### Post by tgalati4 on 2013-06-01
**5.5.28**-0ubuntu0**.12.04.2** however: Version of mysql-server-core-5.5 on system is **5.5.31**-0ubuntu0.**12.04.1**.

Are there other updates that need to be performed?

Open a terminal and post the output of:

```
sudo apt-get update
sudo apt-get upgrade
```

It appears that you may not have all the upgraded components when going from 12.04.1 to 12.04.2.

---

### Post by cariboo on 2013-06-01
Moved to General Help, as this is a better place to get an answer to your question.

---

### Post by cpmman on 2013-06-12
After several attempts to resolve the 12.04.1 / 12.04.2 issue (which disallows any apt-get solutions because it cannot update the db file lists) I managed to solve it by

Terminal

1. rm all mysql files with .list extension (makes mysql blind to its own files).

Synaptic - 

2. completely remove anything installed with mysql prefix.
3. in my case I had an error related to mythtv (whatever bloatware that is) and completely removed those entries.
4. install mysql-common, mysql-client, mysql-server.

Although I got queries re assuming no files @ 2. it carried on to do it.

Checked by an aptitude update and safe-upgrade which worked fine (upgrading telepathy-gabble, whatever that is)

It may not work for you but I shall keep my eyes crossed!

Good luck.

---

### Post by GirishAvinashPatil on 2013-06-21
sudo apt-get remove &#8211;purge mysql.*

---

### Post by GirishAvinashPatil on 2013-06-21
sudo apt-get remove –purge mysql.*

---

