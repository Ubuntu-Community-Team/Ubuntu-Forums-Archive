---
title: "The installation or removal of a software package failed."
date: 2013-11-01
forum: General Help
---

### Post by blfrkt on 2013-11-01
this is the the problem    




```
installArchives() failed: Selecting previously unselected package fuse-utils. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 239317 files and directories currently installed.) 
Unpacking fuse-utils (from .../fuse-utils_2.8.6-2ubuntu2_all.deb) ... 
Selecting previously unselected package fuseiso. 
Unpacking fuseiso (from .../fuseiso_20070708-2_i386.deb) ... 
Selecting previously unselected package fuseiso9660. 
Unpacking fuseiso9660 (from .../fuseiso9660_0.2b-1.1build1_i386.deb) ... 
Selecting previously unselected package python-glade2. 
Unpacking python-glade2 (from .../python-glade2_2.24.0-3_i386.deb) ... 
Selecting previously unselected package furiusisomount. 
Unpacking furiusisomount (from .../furiusisomount_0.11.3.1~repack0-1_all.deb) ... 
Processing triggers for man-db ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for menu ... 
Setting up metasploit (4.5.2-2013031101-1precise1) ... 
psql: could not connect to server: No such file or directory 
    Is the server running locally and accepting 
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.7337"? 
Creating metasploit database user 'msf3'... 
createuser: could not connect to database postgres: could not connect to server: No such file or directory 
    Is the server running locally and accepting 
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.7337"? 
dpkg: error processing metasploit (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Setting up fuse-utils (2.8.6-2ubuntu2) ... 
Setting up fuseiso (20070708-2) ... 
Setting up fuseiso9660 (0.2b-1.1build1) ... 
Setting up python-glade2 (2.24.0-3) ... 
Setting up furiusisomount (0.11.3.1~repack0-1) ... 
Processing triggers for menu ... 
Errors were encountered while processing: 
 metasploit 
Error in function:  
Setting up metasploit (4.5.2-2013031101-1precise1) ... 
psql: could not connect to server: No such file or directory 
    Is the server running locally and accepting 
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.7337"? 
Creating metasploit database user 'msf3'... 
createuser: could not connect to database postgres: could not connect to server: No such file or directory 
    Is the server running locally and accepting 
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.7337"? 
dpkg: error processing metasploit (--configure): 
 subprocess installed post-installation script returned error exit status 1 


```

---

### Post by fantab on 2013-11-01
Post the output of:
```
sudo apt-get update
```

.... and tell us what were you doing or what are you trying to do?

---

