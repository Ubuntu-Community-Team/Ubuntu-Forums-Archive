---
title: "help error message when i try to install virtualbox"
date: 2007-05-21
forum: General Help
---

### Post by zach12 on 2007-05-21
hi i am geting a error message when i try to install virtualbox here it is zach@zach-laptop:~$ > sudo dpkg -i VirtualBox_1.3.8_Ubuntu_dapper drake.deb
Password:
dpkg: error processing VirtualBox_1.3.8_Ubuntu_dapper (--install):
 cannot access archive: No such file or directory
dpkg: error processing drake.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 VirtualBox_1.3.8_Ubuntu_dapper
 drake.deb
zach@zach-laptop:~$
thank you

---

### Post by bodhi.zazen on 2007-05-22
> **zach12 said:**
> hi i am geting a error message when i try to install virtualbox here it is zach@zach-laptop:~$ 
thank you

Where did you download the virtualbox .deb to ? your desktop?

You need to cd into the downloaded location.

Assuming your desktop:```
cd Desktop
```


Then re-run the install:

also Linux is case sensative and the name of the file you entered is wrong.

The correct codes is as follows:

```
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_dapper_i386.deb
```

You can use tab completion to make life easier.

Start typing the file name and, without any spaces, hit the tab key:

Virt<tab>

When you hit the tab key the command line will fill in the name of the file :)

---

### Post by zach12 on 2007-05-25
ok i did that and got a error message here it is > 8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb
dpkg: error processing [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb) (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb)
 odd
thank you!

---

### Post by bodhi.zazen on 2007-05-25
> **zach12 said:**
> ok i did that and got a error message here it is  odd
thank you!

Yea, that is a weird problem that has been reported. I am not sure about the exact cause but it seems the deb is sometimes corrupt and it leads to problems ...

Open a terminal and enter these commands :

```
wget http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb
md5sum  VirtualBox_1.3.8_Ubuntu_dapper_i386.deb
```

md5sum will check the integrity of your download.

It should be : > 58f4ddad88b214a6b90ccdcff21bd29e

If you do not have the correct value, re-download.

If the md5sum is OK, install with : ```
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_dapper_i386.deb
```

---

### Post by Pisi-Deff on 2007-05-25
> **zach12 said:**
> ok i did that and got a error message here it is  odd
thank you!
You need to download that file to your harddrive and then use that command...

Edit:// @bodhi.zazen : The file he downloaded wasn't corrupt, he simply entered the command wrong.

---

### Post by Praill on 2007-05-25
> sudo dpkg -i VirtualBox_1.3.8_Ubuntu_dapper drake.deb
Well you have a space in the file name and its stopping there. It tells you so in the error message. It says VirtualBox_1.3.8_Ubuntu_dapper doesnt exist and neither does drake.deb... which they probably dont.

Did you try 
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_dapper_drake.deb
??

Note the underline between dapper and drake that I have added.
Make sure you run this command from the directory the package resides in.

---

### Post by bodhi.zazen on 2007-05-25
> **Pisi-Deff said:**
> You need to download that file to your harddrive and then use that command...

Edit:// @bodhi.zazen : The file he downloaded wasn't corrupt, he simply entered the command wrong.

Heh, either that or I gave him the wrong command (see edit to my post) :redface:

---

### Post by zach12 on 2007-05-25
hello i'm haveing a new error message here it is > zach@zach-laptop:~$ wget [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb)
--22:01:05--  [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_dapper_i386.deb)
           => `VirtualBox_1.3.8_Ubuntu_dapper_i386.deb'
Resolving [www.virtualbox.org](www.virtualbox.org)... 88.198.19.108
Connecting to www.virtualbox.org|88.198.19.108|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,954,442 (10M) [application/x-debian-package]

100%[====================================>] 10,954,442   159.58K/s    ETA 00:00

22:02:13 (158.42 KB/s) - `VirtualBox_1.3.8_Ubuntu_dapper_i386.deb' saved [10954442/10954442]

zach@zach-laptop:~$ md5sum  VirtualBox_1.3.8_Ubuntu_dapper_i386.deb
58f4ddad88b214a6b90ccdcff21bd29e  VirtualBox_1.3.8_Ubuntu_dapper_i386.deb
zach@zach-laptop:~$ sudo dpkg -i VirtualBox_1.3.8_Ubuntu_dapper_i386.deb
Password:
Selecting previously deselected package virtualbox.
(Reading database ... 119279 files and directories currently installed.)
Unpacking virtualbox (from VirtualBox_1.3.8_Ubuntu_dapper_i386.deb) ...
Setting up virtualbox (1.3.8_Ubuntu_dapper) ...
 * Starting VirtualBox kernel module vboxdrv FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

zach@zach-laptop:~$ sudo dpkg -i VirtualBox_1.3.8_Ubuntu_dapper drake.deb
dpkg: error processing VirtualBox_1.3.8_Ubuntu_dapper (--install):
 cannot access archive: No such file or directory
dpkg: error processing drake.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 VirtualBox_1.3.8_Ubuntu_dapper
 drake.deb
zach@zach-laptop:~$
 thank you

---

### Post by bodhi.zazen on 2007-05-26
I am not sure about dapper ...

You can try : ```
sudo apt-get -f install
```

---

