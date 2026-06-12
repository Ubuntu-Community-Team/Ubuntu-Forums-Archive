---
title: "Can't install Mendeley desktop version 1.19.8 on Ubuntu 22.04"
date: 2022-04-27
forum: General Help
---

### Post by anychare on 2022-04-27
**I am having a nightmare trying to install Mendeley desktop 1.19.8 on Ubuntu 22.04. The following error is constantly being displayed. **

sudo dpkg -i /home/ac/Downloads/mendeleydesktop.deb
Selecting previously unselected package mendeleydesktop.
(Reading database ... 205876 files and directories currently installed.)
Preparing to unpack .../Downloads/mendeleydesktop.deb ...
Unpacking mendeleydesktop (1.19.8) ...
dpkg: dependency problems prevent configuration of mendeleydesktop:
 mendeleydesktop depends on python; however:
  Package python is not installed.

dpkg: error processing package mendeleydesktop (--install):
 dependency problems - leaving unconfigured
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Errors were encountered while processing:
 mendeleydesktop


**I have also tried installing this way and i still get an error:**

sudo apt-get install /home/ac/Downloads/mendeleydesktop.deb
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'mendeleydesktop' instead of '/home/ac/Downloads/mendeleydesktop.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mendeleydesktop : Depends: python but it is not installable
E: Unable to correct problems, you have held broken packages.

**I have tried several solutions given on various web forums but they have all not worked. Please assist I am getting frustrated. I badly need Mendeley desktop in Ubuntu and if I cannot have it installed because of the python dependency issue I might have to switch back to Windows.**

---

### Post by dragonfly41 on 2022-04-27
I don't use Mendeley so cannot help.
Can you perhaps use Zotero as an alternative?
You need both a standalone desktop app and browser connector.

[P.S.] The answer is posted here.
[https://askubuntu.com/questions/1405042/how-to-install-mendeley-on-ubuntu-22-04](https://askubuntu.com/questions/1405042/how-to-install-mendeley-on-ubuntu-22-04)

Python ...

---

### Post by grahammechanical on 2022-04-27
> dpkg: dependency problems prevent configuration of mendeleydesktop:
 mendeleydesktop depends on python; however: Package python is not installed.

There is the problem. Your operating system does not have Python installed. I have no idea if this guide is any good or is the best method for installing Python.

[https://phoenixnap.com/kb/how-to-install-python-3-ubuntu](https://phoenixnap.com/kb/how-to-install-python-3-ubuntu)


Regards

---

### Post by Holger_Gehrke on 2022-04-27
You actually DO have python installed. BUT as the description of the package python-is-python3 states:
> 
Starting with the Debian 11 (bullseye) and Ubuntu 20.04 LTS (focal)
 releases, all python packages use explicit python3 or python2 interpreter
 and do not use unversioned /usr/bin/python at all.

As a matter of fact there is no package named just python without a version, there are only packages python2 and python3. A package that depends on a package 'python' can probably not be installed on anything newer then 18.04. You could try to use the non-Ubuntu specific tar-archive they offer for download. Unpack it into your $HOME and then run 'python3 mendeleydesktop-1.19.8-linux-x86_64/bin/mendeleydesktop'. I got it to run up to the point were it wanted me to sign in. Since I don't have an account with mendeley - and don't intent to make one - I broke off at this point ...

Holger

---

### Post by anychare on 2022-04-28
Thanks for the suggestion. I ended up switching to Zotero and its working like a charm with LibreOffice 7.3.

---

### Post by vanadium on 2022-04-29
Zotero is open source, so is a better options from that point of view. That said, installing "python-is-python3" will install a symlink "python" that points to python3.

---

### Post by gleedadswell on 2022-05-19
Installing python-is-python3 didn't work for me.

It is possible to edit the .deb file to fix this.  See here:
[https://askubuntu.com/questions/1405042/how-to-install-mendeley-on-ubuntu-22-04](https://askubuntu.com/questions/1405042/how-to-install-mendeley-on-ubuntu-22-04)
and here:
[URL="https://serverfault.com/questions/250224/how-do-i-get-apt-get-to-ignore-some-dependencies"]https://serverfault.com/questions/250224/how-do-i-get-apt-get-to-ignore-some-dependencies
[/URL]
I edited the list of dependencies to replace python with python3.  It then installed successfully.  There was a worrying error during install

```
File "/opt/mendeleydesktop/apt/setup-apt-repository.py", line 15
    print "Setting up Mendeley Desktop apt repository"
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
SyntaxError: Missing parentheses in call to 'print'. Did you mean print(...)?
```

But after installation everything seems to work despite this.

---

### Post by dragonfly41 on 2022-05-19
This simply points to the use of different print notations  

it is

Python2.x .. print "Hello World"
Python3.x .. print("Hello World")

Clearly [COLOR=#000000][FONT=&amp]setup-apt-repository.py is expecting Python2.x (I don't know why if it is a modern installation of Mendeley).

See the clue .. [/FONT][/COLOR][COLOR=#000000][FONT=&amp]Did you mean print(...)?

Further explanation here ..

[/FONT][/COLOR]https://realpython.com/python-print/

---

