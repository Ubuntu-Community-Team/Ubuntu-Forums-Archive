---
title: "apt-get has problems with 'unmet dependencies'"
date: 2015-10-01
forum: General Help
---

### Post by Jethro_Borsje on 2015-10-01
Hi all,

I try to install a package (doesn't matter which one) and apt-get always complains about unmet-dependencies:
```
[COLOR=#000000][FONT=monospace]jethro@jethro-MacBookPro:~$ sudo apt-get install hipchat [/FONT][/COLOR][FONT=monospace][sudo] password for jethro:  
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-community-server : Depends: mysql-common (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is to be installed
                          Recommends: mysql-client (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is to be installed
 mysql-server : Depends: mysql-community-server (= 5.6.27-1ubuntu15.04) but 5.6.26-1ubuntu15.04 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/FONT]

```

If I run **apt-get -f install **I get the following:
```
[COLOR=#000000][FONT=monospace]jethro@jethro-MacBookPro:~$ sudo apt-get -f install [/FONT][/COLOR][FONT=monospace]Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 mysql-community-server : Depends: mysql-common (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is installed
                          Recommends: mysql-client (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is installed
 mysql-server : Depends: mysql-community-server (= 5.6.27-1ubuntu15.04) but 5.6.26-1ubuntu15.04 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
[/FONT]

```

I have added extra 'sources' to apt, the contents of the **/etc/apt/sources.list.d/** directory:
```

[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root   55 okt  1 20:18 atlassian-hipchat.list                                                                       [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root   55 okt  1 20:18 atlassian-hipchat.list.save                                                                  [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root  118 okt  1 20:18 cassandra.sources.list                                                                       [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root  118 okt  1 20:18 cassandra.sources.list.save                                                                  [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root  176 okt  1 20:18 google-chrome.list                                                                           [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root  176 okt  1 20:18 google-chrome.list.save                                                                      [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root  566 okt  1 20:44 mysql.list                                                                                   [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root  564 okt  1 20:18 mysql.list.save                                                                              [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root  134 okt  1 20:18 webupd8team-ubuntu-java-vivid.list                                                           [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rw-r--r-- 1 root root  134 okt  1 20:18 webupd8team-ubuntu-java-vivid.list.save [/FONT][/COLOR]

```

I tried
```
sudo apt-get clean
```
and then
```
sudo apt-get -f autoremove
```
this gave:
```

[FONT=monospace][COLOR=#000000]jethro@jethro-MacBookPro:/etc/apt/sources.list.d$ sudo apt-get -f  autoremove[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-community-server
The following packages will be upgraded:
  mysql-community-server
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 14,2 MB of archives.
After this operation, 33,8 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://repo.mysql.com/apt/ubuntu/ vivid/mysql-5.6 mysql-community-server amd64 5.6.27-1ubuntu15.04 [14,2 MB]
Fetched 14,2 MB in 36s (384 kB/s)                                                                                                    
Preconfiguring packages ...
(Reading database ... 157246 files and directories currently installed.)
Preparing to unpack .../mysql-community-server_5.6.27-1ubuntu15.04_amd64.deb ...
................
dpkg: error processing archive /var/cache/apt/archives/mysql-community-server_5.6.27-1ubuntu15.04_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-community-server_5.6.27-1ubuntu15.04_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]
```

How should I proceed?

Best regards,
Jethro

---

### Post by TheFu on 2015-10-01
Remove all the added sources, do a full update/upgrade cycle, then add in the PPAs one at a time to see which is causing the dependency issue.

I appears the mysql PPA in the list is the issue.

---

### Post by claracc on 2015-10-02
> **TheFu said:**
> Remove all the added sources, do a full update/upgrade cycle, then add in the PPAs one at a time to see which is causing the dependency issue.

I appears the mysql PPA in the list is the issue. +1

I also think the mysql ppa repository is the culprit

---

### Post by Jethro_Borsje on 2015-10-02
[FONT=monospace][COLOR=#000000]I removed all the extra sources from **/etc/apt/sources.list.d **by using **rm**, is that the right way?. Then I ran **sudo apt-get update **followed by **sudo apt-get upgrade**. This last one resulted in the same problem:

```

jethro@jethro-MacBookPro:/etc/apt/sources.list.d$ sudo apt-get upgrade
[/COLOR]Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-community-server : Depends: mysql-common (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is installed
                          Recommends: mysql-client (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is installed
 mysql-server : Depends: mysql-community-server (= 5.6.27-1ubuntu15.04) but 5.6.26-1ubuntu15.04 is installed
E: Unmet dependencies. Try using -f.

```

Running the same command with the -f switch did not help either:
```
jethro@jethro-MacBookPro:/etc/apt/sources.list.d$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 mysql-community-server : Depends: mysql-common (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is installed
                          Recommends: mysql-client (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is installed
 mysql-server : Depends: mysql-community-server (= 5.6.27-1ubuntu15.04) but 5.6.26-1ubuntu15.04 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```
[/FONT]

---

### Post by TheFu on 2015-10-02
mysql-community-server and mysql-server are having issues. I would remove (not purge) mysql-server.

No, deleting those PPA files is **not** the way I'd do it.  I would have moved them to somewhere else on my system, so they would be easy to put back later. Of course, if you have great, versioned, backups this is a non-issue. Just restore them from a backup which contains them 1 at a time AFTER the upgrade is working.

Don't forget that every time the list of available PPAs is modified, **sudo apt-get update** is needed. It is easy to forget that step.

---

### Post by Jethro_Borsje on 2015-10-02
> **TheFu said:**
> mysql-community-server and mysql-server are having issues. I would remove (not purge) mysql-server.
[FONT=monospace][COLOR=#000000]
I tried to remove mysql-server with **sudo apt-get remove mysql-server**, but this didn't work:
```

jethro@jethro-MacBookPro:/etc/apt/sources.list.d$ sudo apt-get remove mysql-server[/COLOR]  
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-community-server : Depends: mysql-common (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is to be installed
                          Recommends: mysql-client (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

The same goes for removing mysql-community-server:
```

jethro@jethro-MacBookPro:/etc/apt/sources.list.d$ sudo apt-get remove mysql-community-server
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 akonadi-backend-mysql : Depends: mysql-server-core-5.6 but it is not going to be installed or
                                  virtual-mysql-server-core
 mysql-server : Depends: mysql-community-server (= 5.6.27-1ubuntu15.04) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Should I downgrade these packages to the ones which are in the official Ubuntu repositories somehow? It seems like the ones I have installed are from the mysql repository.[/FONT]

> 
No, deleting those PPA files is **not** the way I'd do it.  I would have moved them to somewhere else on my system, so they would be easy to put back later. Of course, if you have great, versioned, backups this is a non-issue. Just restore them from a backup which contains them 1 at a time AFTER the upgrade is working.
I actually first copied them to another location on my machine, so I still have them :)

---

### Post by dino99 on 2015-10-02
The way to get back a cleaned archive:
- set back the "added sources"
- install ppa-purge

then you can use 'ppa-purge' to remove the ppas; usually 

```
sudo ppa-purge ppa:xyz/abcd
```

  ( xyz is the name of each ppa to remove)
when done, update the ubuntu archive

---

### Post by Jethro_Borsje on 2015-10-02
> **dino99 said:**
> The way to get back a cleaned archive:
- set back the "added sources"
- install ppa-purge

then you can use 'ppa-purge' to remove the ppas; usually "sudo ppa-purge ppa:xyz/abcd"  ( xyz is the name of each ppa to remove)
when done, update the ubuntu archive
I know, but I can not install ppa-purge at the moment, because apt-get install fails because of the 'unmet dependencies' problem.

---

### Post by Jethro_Borsje on 2015-10-02
If I try removing more things related to the wrong mysql stuff, I get this:
```

[FONT=monospace][COLOR=#000000]jethro@jethro-MacBookPro:~$ sudo apt-get remove mysql-community-* mysql-client mysql-server    [/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Note, selecting 'mysql-community-server' for regex 'mysql-community-*'
Note, selecting 'mysql-community-client' for regex 'mysql-community-*'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 akonadi-backend-mysql : Depends: mysql-client-core-5.6 but it is not going to be installed or
                                  virtual-mysql-client-core
                         Depends: mysql-server-core-5.6 but it is not going to be installed or
                                  virtual-mysql-server-core
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Is there a way to remove the wrong stuff and install the correct stuff in one go?[/FONT]

---

### Post by TheFu on 2015-10-02
Don't manually remove files installed through a package manager. It will make it worse.

I forgot something - it is 2nd nature to me.  I don't use apt-get and haven't for a few years.  I use  aptitude - it tends to be smarter about dependency issues like this.

Try **sudo aptitude update** and see if it offers  a  dependency resolution that you  like. It is ok to refuse the 1st offer and hopefully it will offer another.

---

### Post by Jethro_Borsje on 2015-10-02
There must be a better way to fix this problem using apt-get? The only real alternative I see is reinstalling my entire system.

---

### Post by mc4man on 2015-10-02
> **Jethro_Borsje said:**
> There must be a better way to fix this problem using apt-get? The only real alternative I see is reinstalling my entire system.
I'm sure you can, please post link to which mysql ppa you are using

---

### Post by Jethro_Borsje on 2015-10-02
> **mc4man said:**
> I'm sure you can, please post link to which mysql ppa you are using
[http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/](http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/) is the link to the guide I followed. Which boils down to: [http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/index.html#repo-qg-apt-repo-manual-setup](http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/index.html#repo-qg-apt-repo-manual-setup).

---

### Post by Jethro_Borsje on 2015-10-02
> **TheFu said:**
> Don't manually remove files installed through a package manager. It will make it worse.

I forgot something - it is 2nd nature to me.  I don't use apt-get and haven't for a few years.  I use  aptitude - it tends to be smarter about dependency issues like this.

Try **sudo aptitude update** and see if it offers  a  dependency resolution that you  like. It is ok to refuse the 1st offer and hopefully it will offer another.
I can not use aptitude, because I cannot install it with apt-get:
```
[COLOR=#000000][FONT=monospace]jethro@jethro-MacBookPro:~$ sudo apt-get -f install aptitude                                                                          [/FONT][/COLOR][FONT=monospace]Reading package lists... Done                                                                                                         
Building dependency tree                                                                                                              
Reading state information... Done                                                                                                     
You might want to run 'apt-get -f install' to correct these:                                                                          
The following packages have unmet dependencies:                                                                                       
 aptitude : Depends: aptitude-common (= 0.6.11-1ubuntu3) but it is not going to be installed                                          
            Depends: libcwidget3 but it is not going to be installed                                                                  
            Recommends: aptitude-doc-en but it is not going to be installed or                                                        
                        aptitude-doc                                                                                                  
 mysql-community-server : Depends: mysql-common (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is to be installed                    
                          Recommends: mysql-client (= 5.6.26-1ubuntu15.04) but 5.6.27-1ubuntu15.04 is to be installed                 
 mysql-server : Depends: mysql-community-server (= 5.6.27-1ubuntu15.04) but 5.6.26-1ubuntu15.04 is to be installed                    
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
[/FONT]

---

### Post by mc4man on 2015-10-02
Initially it was  downloading the proper package from the [external repo]("http://repo.mysql.com/apt/ubuntu/pool/mysql-5.6/m/mysql-community/") but failing on "subprocess new pre-installation script returned error exit status 1"
So you may wish to explore what the issue was there (if that .repo is still availabe in your sources.

Otherwise identify all packages you have installed from that repo, download the Ubuntu versions into a folder & install in bulk with dpkg.
(sudo dpkg -i *.deb
Note that dpkg does not resolve/install missing  dependencies so you need to get all. If any packages are missing dpkg will fail, (no big deal) but will tell you why. Get what you need & re run dpkg until it completes without error.

Edit: you could also try just purging the mysql packages you know are installed, you'd want to do it with one apt-get command, apt-cache policy would show you, list of possible from that repo - 
```
mysql-server
mysql-community-server
mysql-client
mysql-community-client
mysql-common
libmysqlclient18
libmysqlclient-dev
libmysqld-dev 
mysql-testsuite
mysql-community-test
mysql-community-bench
mysql-community-source
mysql-workbench-community	
mysql-connector-python-py3	
mysql-connector-python	
mysql-utilities-1.5
```

So this, look for installed packages, &  remove all that are.
```
apt-cache policy mysql-server mysql-community-server mysql-client mysql-common \
mysql-community-client libmysqlclient18 libmysqlclient-dev libmysqld-dev \
mysql-testsuite mysql-community-test mysql-community-bench mysql-community-source \
mysql-workbench-community mysql-connector-python-py3 mysql-connector-python \
mysql-utilities-1.5
```
If successful then make sure that repo is gone before re-installing any removed packages.

---

### Post by Jethro_Borsje on 2015-10-03
That sounds like a plan, but I cannot purge those packages:
```
[COLOR=#000000][FONT=monospace]jethro@jethro-MacBookPro:~$ sudo apt-get -f purge mysql-community-server mysql-common mysql-community-client libmysqlclient18
[/FONT][/COLOR][FONT=monospace]Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 akonadi-backend-mysql : Depends: mysql-client-core-5.6 but it is not going to be installed or
                                  virtual-mysql-client-core
                         Depends: mysql-server-core-5.6 but it is not going to be installed or
                                  virtual-mysql-server-core
 amarok : Depends: libmysqlclient18 (>= 5.5.24+dfsg-1) but it is not going to be installed
 libqt4-sql-mysql : Depends: libmysqlclient18 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/FONT]
```
[FONT=monospace]
Using **dpkg -P **yields the same result. Is apt-get not capable of installing the needed mysq alternatives itself while removing the corrupt ones?[/FONT]

---

### Post by mc4man on 2015-10-03
This is fairly screwed up by a few things - 

You either have akonadi-backend-mysql installed or apt is trying to install it to keep some other package that would be broken by what you're trying to remove. Or you are on a kubuntu install which may complicate this, are you ??
Removing the packages in that list would remove amarok, as far as akonadi*,  amarok does not depend on them

Also that mysql repo has both 5.6.26 & 5.6.27 packages, you seem to have been behind that somewhat, seen here earlier when that repo's mysql-community-server failed to upgrade, is to be installed means already is installed in this case - 

> mysql-community-server : Depends: mysql-common (= 5.6.[COLOR="#FF0000"]26[/COLOR]-1ubuntu15.04) but 5.6.[COLOR="#FF0000"]27[/COLOR]-1ubuntu15.04 is to be installed 

Additionally out of the 4 packages only 2 have Ubuntu replacements, 2 don't seem to exist
2 that don't exist are - 
mysql-community-server 
mysql-community-client

The 2 that do -
[http://packages.ubuntu.com/vivid-updates/mysql-common](http://packages.ubuntu.com/vivid-updates/mysql-common)
[http://packages.ubuntu.com/vivid-updates/libmysqlclient18](http://packages.ubuntu.com/vivid-updates/libmysqlclient18)

So if on Kubuntu please mention, **if not** then try also removing both akonadi-backend-mysql & amarok, if that doesn't work then try below or just try below...

(- if on kunutu  then best action may be to download those 2 packages that are in Ubuntu, put the .debs in an empty folder, cd to that folder & use the sudo dpkg -i *.deb command on. This will break those other 2 mysql repo packages & possibly then allow you to remove them
Note that the common package is for all arch's, the lib one you need to get proper arch for your install, i386 or amd64

---

### Post by Jethro_Borsje on 2015-10-03
Yes I am on Kubuntu.

I downloaded the two dependencies and installed them:
```
[FONT=monospace][COLOR=#000000]jethro@jethro-MacBookPro:~/Downloads/mysql-deb$ sudo dpkg -i *.deb  [/COLOR]  
Selecting previously unselected package libmysqlclient18:amd64.
(Reading database ... 155960 files and directories currently installed.)
Preparing to unpack libmysqlclient18_5.6.25-0ubuntu0.15.04.1_amd64.deb ...
Unpacking libmysqlclient18:amd64 (5.6.25-0ubuntu0.15.04.1) over (5.6.27-1ubuntu15.04) ...
Selecting previously unselected package mysql-common.
Preparing to unpack mysql-common_5.6.25-0ubuntu0.15.04.1_all.deb ...
Unpacking mysql-common (5.6.25-0ubuntu0.15.04.1) over (5.6.27-1ubuntu15.04) ...
dpkg: warning: mysql-common: conffile '/etc/mysql/conf.d/mysql.cnf' is not a plain file or symlink (= '/etc/mysql/conf.d/mysql.cnf')
Setting up mysql-common (5.6.25-0ubuntu0.15.04.1) ...
dpkg: warning: mysql-common: conffile '/etc/mysql/conf.d/mysql.cnf' is not a plain file or symlink (= '/etc/mysql/conf.d/mysql.cnf')
Installing new version of config file /etc/mysql/my.cnf.fallback ...
Setting up libmysqlclient18:amd64 (5.6.25-0ubuntu0.15.04.1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
[/FONT]

```

The contents of the folder is:
```
[FONT=monospace][COLOR=#000000]jethro@jethro-MacBookPro:~/Downloads/mysql-deb$ ll                                                                                    [/COLOR]
total 708                                                                                                                             
drwxrwxr-x 2 jethro jethro   4096 okt  3 20:53 [COLOR=#5454FF]**.**[/COLOR][COLOR=#000000]/                                                                                     [/COLOR]
drwxr-xr-x 5 jethro jethro   4096 okt  3 20:53 [COLOR=#5454FF]**..**[/COLOR][COLOR=#000000]/                                                                                    [/COLOR]
-rw-r----- 1 jethro jethro 690270 okt  3 20:53 [COLOR=#FF5454]**libmysqlclient18_5.6.25-0ubuntu0.15.04.1_amd64.deb**[/COLOR][COLOR=#000000]                                     [/COLOR]
-rw-r----- 1 jethro jethro  14698 okt  3 20:52 [COLOR=#FF5454]**mysql-common_5.6.25-0ubuntu0.15.04.1_all.deb**[/COLOR][COLOR=#000000]           [/COLOR]
[/FONT]

```

For some reason this seems to have solved the problem, because I was now able to successfully run **sudo apt-get -f install**:
```
jethro@jethro-MacBookPro:~/Downloads/mysql-deb$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libatkmm-1.6-1 libcairomm-1.0-1 libctemplate2 libglibmm-2.4-1c2a libgnome-keyring-common libgnome-keyring0 libgtkmm-2.4-1c2a
  libpangomm-1.4-1 libsigc++-2.0-0c2a libtinyxml2.6.2 python-ecdsa python-paramiko
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-client-core-5.6 mysql-server-core-5.6
The following packages will be REMOVED:
  mysql-community-client mysql-community-server
The following NEW packages will be installed:
  mysql-client-core-5.6 mysql-server-core-5.6
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 8296 kB of archives.
After this operation, 116 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://nl.archive.ubuntu.com/ubuntu/ vivid-updates/main mysql-client-core-5.6 amd64 5.6.25-0ubuntu0.15.04.1 [4036 kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ vivid-updates/main mysql-server-core-5.6 amd64 5.6.25-0ubuntu0.15.04.1 [4259 kB]         
Fetched 8296 kB in 13s (628 kB/s)                                                                                                   
dpkg: mysql-community-client: dependency problems, but removing anyway as you requested:
 akonadi-backend-mysql depends on mysql-client-core-5.6 | virtual-mysql-client-core; however:
  Package mysql-client-core-5.6 is not installed.
  Package virtual-mysql-client-core is not installed.
  Package mysql-community-client which provides virtual-mysql-client-core is to be removed.


(Reading database ... 155876 files and directories currently installed.)
Removing mysql-community-client (5.6.27-1ubuntu15.04) ...
Processing triggers for man-db (2.7.0.2-5) ...
Selecting previously unselected package mysql-client-core-5.6.
(Reading database ... 155835 files and directories currently installed.)
Preparing to unpack .../mysql-client-core-5.6_5.6.25-0ubuntu0.15.04.1_amd64.deb ...
Unpacking mysql-client-core-5.6 (5.6.25-0ubuntu0.15.04.1) ...
Processing triggers for man-db (2.7.0.2-5) ...
dpkg: mysql-community-server: dependency problems, but removing anyway as you requested:
 akonadi-backend-mysql depends on mysql-server-core-5.6 | virtual-mysql-server-core; however:
  Package mysql-server-core-5.6 is not installed.
  Package virtual-mysql-server-core is not installed.
  Package mysql-community-server which provides virtual-mysql-server-core is to be removed.


(Reading database ... 155843 files and directories currently installed.)
Removing mysql-community-server (5.6.26-1ubuntu15.04) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Processing triggers for man-db (2.7.0.2-5) ...
Selecting previously unselected package mysql-server-core-5.6.
(Reading database ... 155735 files and directories currently installed.)
Preparing to unpack .../mysql-server-core-5.6_5.6.25-0ubuntu0.15.04.1_amd64.deb ...
Unpacking mysql-server-core-5.6 (5.6.25-0ubuntu0.15.04.1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up mysql-client-core-5.6 (5.6.25-0ubuntu0.15.04.1) ...
Setting up mysql-server-core-5.6 (5.6.25-0ubuntu0.15.04.1) ...

```

After that I was able to install other packages like aptitude!

I will now again try to install mysql, because I need it on my laptop for development purposes.

Thank you very much for the help!

---

### Post by Jethro_Borsje on 2015-10-05
Just a follow up for people how might have been running into the same issue: after applying the aforementioned fix I was able to install mysql-server from the default Ubuntu repository without any problems. I now have a functioning system again.

---

### Post by den.koblov on 2015-10-05
You can try to kill all mysqld processes before "apt-get -f install".

---

