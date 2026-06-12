---
title: "package manager stopped working after ubuntu 16.04 normal upgrade"
date: 2016-09-11
forum: General Help
---

### Post by momo5 on 2016-09-11
package manager stopped working after ubuntu 16.04 normal upgrade. i tried to click all error options on the notification center but no result.
[ATTACH=CONFIG]271084[/ATTACH]

---

### Post by Bashing-om on 2016-09-11
momo5; Hi ! Welcome to the forum.

In a situation such as this we resort to the CLI  to obtain needed info.
At the desktop key combo ctl+alt+t to get an interface ( terminal).
Here execute and copy paste the outputs:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we see where the problem lies .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-09-11
*Thread moved to **General Help**.* which is more appropriate for the problem and should be a better fit.

---

### Post by momo5 on 2016-09-13
Hi,
Please check the error that i get from #apt update && apt upgrade.

[COLOR=#000000]```
[/COLOR]
**# apt update && apt upgrade**
Hit:1 [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu) xenial InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:3 [http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu](http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu) xenial InRelease                                        
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                                                           
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease                              
Ign:6 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease                                    
Hit:7 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease                        
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release               
Hit:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease      
Hit:10 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release               
Hit:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease    
**Error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ExecFailed: Cannot launch daemon, file not found or permissions invalid <============= Error**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
7 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
**Some packages could not be installed. This may mean that you have**
**requested an impossible situation or if you are using the unstable**
**distribution that some required packages have not yet been created**
**or been moved out of Incoming.**
The following information may help to resolve the situation:


The following packages have unmet dependencies:
** python-fbthrift : Conflicts: python-thrift**
E: Broken packages
[COLOR=#000000]
```[/COLOR]

---

### Post by ian-weisser on 2016-09-13
Please show us the complete output of:
```
apt-cache policy python-fbthrift
```

---

### Post by momo5 on 2016-09-14
Hi,
Please check the output of : apt-cache policy python-fbthrift




 
[COLOR=#000000]```
[/COLOR]
apt-cache policy python-fbthrift
python-fbthrift:
  Installed: 0.31.0-0reddit5
  Candidate: 0.31.0-0reddit5
  Version table:
 *** 0.31.0-0reddit5 100
        100 /var/lib/dpkg/status
[COLOR=#000000]
```[/COLOR]

---

### Post by momo5 on 2016-09-14
Note: 
[COLOR=#000000]1- ctl+alt+t to get an interface ( terminal) ====== Not working. I must right click on desktop the click terminal.
2- Other programs such playonlinux stopped working. check below.

[/COLOR]```
[COLOR=#ff0000]**# playonlinux**[/COLOR]
Looking for python... 2.7.12 - Traceback (most recent call last):
  File "/usr/share/playonlinux/python/check_python.py", line 1, in <module>
    import os, wxversion
ImportError: No module named wxversion
failed tests
Looking for python2.7... 2.7.12 - Traceback (most recent call last):
  File "/usr/share/playonlinux/python/check_python.py", line 1, in <module>
    import os, wxversion
ImportError: No module named wxversion
failed tests
Looking for python2.6... 
Looking for python2... 2.7.12 - Traceback (most recent call last):
  File "/usr/share/playonlinux/python/check_python.py", line 1, in <module>
    import os, wxversion
ImportError: No module named wxversion
failed tests
Please install python before trying to run this program
**[COLOR=#ff0000]# apt install --reinstall python2.7[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 7 not upgraded.
Need to get 224 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python2.7 amd64 2.7.12-1~16.04 [224 kB]
Fetched 224 kB in 1s (169 kB/s)    
Selecting previously unselected package python2.7.
(Reading database ... 371713 files and directories currently installed.)
Preparing to unpack .../python2.7_2.7.12-1~16.04_amd64.deb ...
Unpacking python2.7 (2.7.12-1~16.04) over (2.7.12-1~16.04) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160701-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up python2.7 (2.7.12-1~16.04) ...
Error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ExecFailed: Cannot launch daemon, file not found or permissions invalid
[COLOR=#ff0000]**# playonlinux**[/COLOR]
Looking for python... 2.7.12 - Traceback (most recent call last):
  File "/usr/share/playonlinux/python/check_python.py", line 1, in <module>
    import os, wxversion
ImportError: No module named wxversion
failed tests
Looking for python2.7... 2.7.12 - Traceback (most recent call last):
  File "/usr/share/playonlinux/python/check_python.py", line 1, in <module>
    import os, wxversion
ImportError: No module named wxversion
failed tests
Looking for python2.6... 
Looking for python2... 2.7.12 - Traceback (most recent call last):
  File "/usr/share/playonlinux/python/check_python.py", line 1, in <module>
    import os, wxversion
ImportError: No module named wxversion
failed tests
Please install python before trying to run this program


```

---

