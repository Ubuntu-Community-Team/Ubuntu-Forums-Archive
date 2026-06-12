---
title: "How to install pyQt5 on Ubuntu 15.04?"
date: 2015-09-12
forum: General Help
---

### Post by swatto on 2015-09-12
Hello all,

Does anyone have a step-by-step guide to installing pyQt5 on Ubuntu or have a working pyQt5 installation that Python 3 recognises?

I followed the following steps but I still cannot run scripts that import the pyQt5 module (get module not found errors)

Download and Install Qtcreator:
Qt Online Installer for Linux 64-bit
Install python dev:
sudo apt-get install python-dev
Download and Install SIP:
sip-4.16.7.tar.gz Linux, UNIX, MacOS/X source
Set QT5 by default:
sudo apt-get install qt5-default.
Download and install PyQT:
PyQt-gpl-5.4.1.tar.gz Linux, UNIX, MacOS/X source

Thanks very much

---

### Post by steeldriver on 2015-09-12
Isn't the default version in the repository already 5.4.1?

```

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"


$ apt-cache policy python3-pyqt5
python3-pyqt5:
  Installed: (none)
  Candidate: 5.4.1+dfsg-2
  Version table:
     5.4.1+dfsg-2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages

```

---

### Post by swatto on 2015-09-12
Thanks for the reply - I just ran the same commands you did:

```

:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"

:~$ apt-cache policy python3-pyqt5
python3-pyqt5:
  Installed: 5.4.1+dfsg-2
  Candidate: 5.4.1+dfsg-2
  Version table:
 *** 5.4.1+dfsg-2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages
        100 /var/lib/dpkg/status

```

I found out what was causing the error I was getting which was:

> Traceback (most recent call last):
  File "HelloWorld.py", line 10, in <module>
    from PyQt5 import QtWidgets
ImportError: No module named PyQt5


------------------
(program exited with code: 1)
Press return to continue


I have literally spent hours re-installing Qt to try and resolve it, it was because I was clicking the run button in Geany to run the script.  When I ran it directly from the terminal using: python3 HelloWorld.py it worked fine.

Strange?

---

### Post by steeldriver on 2015-09-12
Did you tell geany to use python3 as the execute command for the project?

    Build --> Set build commands --> Execute

Otherwise it will probably default to python (i.e. python2 rather than python3)

---

### Post by swatto on 2015-09-12
Thanks very much steeldriver.  That fixed it :)

---

### Post by GreatDanton on 2015-09-17
I came around similar problem in PyCharm. After few hours of installing and reinstalling pyqt5 packages, I saw I was running python3 script with: python name_of_the_script.py instead of python3 name_of_the_script.py

---

