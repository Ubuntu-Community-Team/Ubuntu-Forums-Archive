---
title: "SystemBack Not Installing"
date: 2018-04-17
forum: General Help
---

### Post by open4epl on 2018-04-17
Any possible way to install System Back in 18.4?

Terminal Info:
eddie@eddie-HP-Notebook:~$ sudo add-apt-repository ppa:nemh/systemback
[sudo] password for eddie: 
 Simple system backup and restore application with extra features


Systemback makes it easy to create backups of the system and the users configuration files. In case of problems you can easily restore the previous state of the system. There are extra features like system copying, system installation and Live system creation.


This PPA contain the stable version of Systemback.


Currently supported Ubuntu releases:
- 14.04.X LTS
- 15.04
- 15.10
- 16.04.X LTS
- 16.10


```
* DEVELOPMENT AND SUPPORT ENDED *
 More info: [https://launchpad.net/~nemh/+archive/ubuntu/systemback](https://launchpad.net/~nemh/+archive/ubuntu/systemback)
Press [ENTER] to continue or Ctrl-c to cancel adding it.


Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease [235 kB]
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease          
Ign:8 [http://ppa.launchpad.net/nemh/systemback/ubuntu](http://ppa.launchpad.net/nemh/systemback/ubuntu) bionic InRelease        
Hit:9 [http://ppa.launchpad.net/zorinos/wine-testing/ubuntu](http://ppa.launchpad.net/zorinos/wine-testing/ubuntu) bionic InRelease  
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe i386 Packages [8,524 kB]
Err:11 [http://ppa.launchpad.net/nemh/systemback/ubuntu](http://ppa.launchpad.net/nemh/systemback/ubuntu) bionic Release          
  404  Not Found [IP: 91.189.95.83 80]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages [8,560 kB]
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/nemh/systemback/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
eddie@eddie-HP-Notebook:~$ sudo apt-get update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                     
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release               
Ign:7 [http://ppa.launchpad.net/nemh/systemback/ubuntu](http://ppa.launchpad.net/nemh/systemback/ubuntu) bionic InRelease   
Hit:8 [http://ppa.launchpad.net/zorinos/wine-testing/ubuntu](http://ppa.launchpad.net/zorinos/wine-testing/ubuntu) bionic InRelease   
Err:9 [http://ppa.launchpad.net/nemh/systemback/ubuntu](http://ppa.launchpad.net/nemh/systemback/ubuntu) bionic Release          
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/nemh/systemback/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
eddie@eddie-HP-Notebook:~$ sudo apt-get install systemback
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package systemback
eddie@eddie-HP-Notebook:~$ sudo apt-get install systemback
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package systemback
eddie@eddie-HP-Notebook:~$
```

---

### Post by #&amp;thj^% on 2018-04-17
As you have already seen, the newest version for System Back is **16.10 in the PPA **so I would say the maintainer lost love for keeping it.
Deja Dup is the default backup program for Ubuntu. :[https://community.ubuntu.com/t/default-backup-program-in-18-04/2134](https://community.ubuntu.com/t/default-backup-program-in-18-04/2134)

---

### Post by fconidi on 2018-05-04
Hi 
I updated Systemback, now 1.9.3,  for Debian Stretch, Ubuntu 17-10 and Ubuntu 18-04 ;)
[http://www.francoconidi.it/systemback-1-9-3-per-debian-9-ubuntu-17-10-18-04/](http://www.francoconidi.it/systemback-1-9-3-per-debian-9-ubuntu-17-10-18-04/)

---

### Post by bionic3epl on 2018-05-04
> **fconidi said:**
> Hi 
I updated Systemback, now 1.9.3,  for Debian Stretch, Ubuntu 17-10 and Ubuntu 18-04 ;)
[http://www.francoconidi.it/systemback-1-9-3-per-debian-9-ubuntu-17-10-18-04/](http://www.francoconidi.it/systemback-1-9-3-per-debian-9-ubuntu-17-10-18-04/)

I downloaded the file but it won't install. The Terminal said 
"tar: systemback-install_pack-1.9.3.tar.xz: Cannot open: No such file or directorytar: Error is not recoverable: exiting now"

Please help me w/ this.

---

### Post by yancek on 2018-05-04
No such file or directory is usually the result of running some command from the wrong directory.  If you just downloaded it from the site linked in post 3, then it should be in your user Downloads file.  What exactly did you do to get that result?  You need to either run the proper command from the correct directory to extract the tar.xz file or you can probably right click it and extract it to a folder.  Either method should get you a folder named systemback-install_pack-1.9.3 which will contain a packages directory, a readme.txt file  (which you should read) and an install.sh file which you can run to install it.  You need to be root or use sudo to do that which is also explained at the link.

---

### Post by fconidi on 2018-05-05
> **yancek said:**
> No such file or directory is usually the result of running some command from the wrong directory.  If you just downloaded it from the site linked in post 3, then it should be in your user Downloads file.  What exactly did you do to get that result?  You need to either run the proper command from the correct directory to extract the tar.xz file or you can probably right click it and extract it to a folder.  Either method should get you a folder named systemback-install_pack-1.9.3 which will contain a packages directory, a readme.txt file  (which you should read) and an install.sh file which you can run to install it.  You need to be root or use sudo to do that which is also explained at the link.

infact :)
anyway I add "cd Download/" into the post

---

### Post by open4epl on 2018-05-05
I extracted the files, opened Term. and got: 

$ sudo tar xvf systemback-install_pack-1.9.3.tar.xz
[sudo] password for eddie: 
tar: systemback-install_pack-1.9.3.tar.xz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by open4epl on 2018-05-05
Since the packages were all .deb packages, I managed to get System Back 1.9.3 installed using the Ubuntu Software Center.

---

### Post by monkeybrain20122 on 2018-05-05
> **open4epl said:**
> I extracted the files, opened Term. and got: 

$ sudo tar xvf systemback-install_pack-1.9.3.tar.xz
[sudo] password for eddie: 
tar: systemback-install_pack-1.9.3.tar.xz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Just right click and extract here. Why are you running that command with sudo? sudo shouldn't be abused.

---

### Post by fconidi on 2018-05-06
cd Download/
tar xvf systemback-install_pack-1.9.3.tar.xz
cd systemback-install_pack-1.9.3/
sudo ./install.sh

---

### Post by numark3 on 2018-08-06
thank you fcodini!
it works great on ubuntu 18.04 LTS!

---

### Post by wermwould on 2018-09-07
You, my friend, are my hero. Thank you!

---

### Post by albertoatabay on 2018-12-07
> **fconidi said:**
> Hi 
I updated Systemback, now 1.9.3,  for Debian Stretch, Ubuntu 17-10 and Ubuntu 18-04 ;)
[http://www.francoconidi.it/systemback-1-9-3-per-debian-9-ubuntu-17-10-18-04/](http://www.francoconidi.it/systemback-1-9-3-per-debian-9-ubuntu-17-10-18-04/)

how about 32 bit support?

---

