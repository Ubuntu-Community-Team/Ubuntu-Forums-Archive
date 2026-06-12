---
title: "Borked Packages - cannot start or reconfigure mysql-server"
date: 2014-11-11
forum: General Help
---

### Post by tahaan on 2014-11-11
I recently installed Kubuntu 14.04 in the hopes that it would have a non-broken mysql-workbench somewhere - the .deb download package have dependencies that I had problems installing in 13.04.  So I then installed mysql-workbench but this version is still broken (I think it is 6.0.8), though not quite as old as the one in the 13.04 repositories that I had previously (v5.?.?).

In my search for a newer release of mysql-workbench I discovered the MySQL developers' APT repository.  I don't like the way it is structured - you first install a special apt-repository-config package, and then after the repository is added to your sources through this unusual method, you get access to packages in the MySQL Origin.  <shudder>

I installed mysql-workbench-community from here, which wasn't any better, even though it is at a current version.  It turns out that I'm experiencing this issue: [https://bugs.kde.org/show_bug.cgi?id=339324](https://bugs.kde.org/show_bug.cgi?id=339324)

Changing the GTK theme as suggested however does not completely solve the issue.  It does change it from a consistent problem to an occasional/intermittend one, but the program still crashes.  So I have temporarily given up on MySQL workbench - I will probably try running it in a VM where I care less about how the desktop looks at some future time, but I have more pressing issues right now. 

 Here is where my real problems started.

After this I decided to upgrade to the latest mysql-server, the one from the MySQL community Origin.  This borked a lot of things - I too late noticed that this package wanted to remove a lot of my KDE related packages because it clashed with the MySQL software from the Ubuntu repositories.  After that "installation" operation completed, I un-installed the package and added the kubuntu-desktop and some other packages back in to repair the damage.  I wish I had operating system state check-points in Kubuntu, but alas.

The desktop is still seemingly working, but I have a problem with mysql.  I am unable to start or dpkg-reconfigure the server. 

When trying to start the service I get:
```
tahaan@Komputer:~$ sudo service mysql start
start: Job failed to start
tahaan@Komputer:~$ sudo service mysql restart
stop: Unknown instance: 
start: Job failed to start
```

When trying to reconfigure the package I get:
```
tahaan@Komputer:~$ sudo dpkg-reconfigure mysql-server-5.5
/usr/sbin/dpkg-reconfigure: mysql-server-5.5 is broken or not fully installed
```

Question 1. I don't understand APT packaging well enough - how do I fix this?

Question 2.  I don't understant the Ubuntu / Kubuntu environment well enough - why can't I get rid of MySQL without breaking my desktop?  Or how can I get rid of MySQL?

I should just stick MySQL into a dedicated VM, so I'd like to remove the mysql server packages and ideally move up to v 5.6 for anything that I can't get rid of (eg mysql-client).

---

### Post by ian-weisser on 2014-11-11
Fixing it.

Generally, the right way to fix it is to first uninstall the conflicting packages, then to reinstall the desktop environment and applications, and finaly to install a compatible version of MySQL.

More specifically:

1) Backup your data. Just in case.

2) Uninstall all mysql packages. Autoremove all their dependencies. The goal is to uninstall _all_ software from non-Ubuntu repositories.

3) Disable the non-Ubuntu repository in /etc/apt/sources.list or /etc/apt/sources.list.d/ to prevent apt from installing the same conflicting packages again.

4) Refresh the dpkg database. (sudo apt-get update) to cause apt to forget that the non-Ubuntu packages ever existed.

5) Reinstall your KDE applications, which should reinstall most of your KDE environment.

6) Install the Ubuntu version of MySQL

---

