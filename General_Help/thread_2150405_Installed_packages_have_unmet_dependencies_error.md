---
title: "Installed packages have unmet dependencies error"
date: 2013-05-31
forum: General Help
---

### Post by nadarajan on 2013-05-31
Hi,
I have a 64bit machine running Ubuntu 12.04 LTS. For the past few weeks there is a red dot at the top of the window. When I click on it it shows "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: "Error: BrokenCount>0". This usually means that your installed packages have unmet dependencies". I am unable to install anything. When I try, I get the following error message:

installArchives() failed: dpkg: dependency problems prevent configuration of mysql-client: 
 mysql-client-core-5.5 (5.5.31-0ubuntu0.12.04.1) breaks mysql-client (<< 5.5.31-0ubuntu0.12.04.1) and is installed. 
  Version of mysql-client to be configured is 5.5.29-0ubuntu0.12.04.2. 
dpkg: error processing mysql-client (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 mysql-client 
Error in function:  
dpkg: dependency problems prevent configuration of mysql-client: 
 mysql-client-core-5.5 (5.5.31-0ubuntu0.12.04.1) breaks mysql-client (<< 5.5.31-0ubuntu0.12.04.1) and is installed. 
  Version of mysql-client to be configured is 5.5.29-0ubuntu0.12.04.2. 
dpkg: error  processing mysql-client (--configure): 
 dependency problems - leaving unconfigured

Please let me know how to resolve it.

Thanks

---

### Post by cariboo on 2013-06-01
The Resolution Centre is a place where can voice your complaints against the Moderation Team, not for asking support questions. Moved to General Help.

---

### Post by tgalati4 on 2013-06-01
You have a couple of things going on.  One, you perhaps installed something from a PPA or third-party repository recently and that package uses a database (most likly mysql) but a slightly newer version.  The package manager is telling you that the mysql client version is slightly newer and may break the mysql client that you already have on your system.

The second issue is that the crash reporting system apport is having a problem because you have reached the limit of crash reports and it has turned itself off.  I believe that limit is 3 per crashing program, base on what I could find.  So that could be related to what you last installed or something else.

Some things to check:  [http://askubuntu.com/questions/31667/what-does-no-apport-report-written-because-maxreports-is-reached-already-mean](http://askubuntu.com/questions/31667/what-does-no-apport-report-written-because-maxreports-is-reached-already-mean)

To fix the problem, remove the offending program or try a forced installation and expect some breakage.

---

### Post by nadarajan on 2013-06-01
Thanks for the input. I don't know how to resolve it. I tried to uninstall MySQL by trying sudo apt-get remove --purge mysql-common mysql-client mysql-server which also failed. I also tried 'apt-get -f install' without success. Not sure what else to do. I have entered detailed report here [http://paste.ubuntu.com/5724524/](http://paste.ubuntu.com/5724524/)

---

### Post by mc4man on 2013-06-01
"mysql-client-core-5.5 (5.5.31-0ubuntu0.12.04.1) breaks mysql-client (<< 5.5.31-0ubuntu0.12.04.1) and is installed.
Version of mysql-client to be configured is 5.5.29-0ubuntu0.12.04.2." 

 5.5.29-0ubuntu0.12.04.2 is the old 12.04 release version, in 12.04 it's now up to 5.5.31-0ubuntu0.12.04.2, was recently upped from 5.5.31-0ubuntu0.12.04.1

So try this - 
open software-sources, (software-properties-gtk), under the "Updates" tab make sure that 1st 2 are enabled (security & updates
If not then  enable, then run sudo apt-get update & ck. if 5.5.31-0ubuntu0.12.04.2 is available

If still not available then re-open software sources & on main tab change the mirror, (Download from)  to  "Main server" or "Server for United States", run sudo apt-get update & recheck

post this if continuing to have issue - 
```
apt-cache policy mysql-client*
```

---

### Post by Cheesehead on 2013-06-01
mc4man is right - you are trying to update from two different release repositories.

Post your /etc/apt/sources.list here.

---

