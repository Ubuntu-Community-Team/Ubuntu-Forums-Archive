---
title: "I can't apt-get install Keepass or untar Firefox 1.5 correctly"
date: 2006-09-11
forum: General Help
---

### Post by CupofDice on 2006-09-11
I installed 5.10 yesterday, and everything (net, partitions, updates) is okay except the terminal apt-get (synaptic works just fine). 

I am trying to install KeypassX. [http://keepass.sourceforge.net/download.php]("http://keepass.sourceforge.net/download.php")
```
user@host:~$ cd Desktop
user@host:~/Desktop$ dirs
~/Desktop
user@host:~/Desktop$ dir
curly-004051b0cd.desktop  eog.desktop  firefox.desktop  KeePassX-0.2.2.deb
user@host:~/Desktop$ apt-get install KeePassX-0.2.2.deb
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
user@host:~/Desktop$ apt-get install ~/Desktop/KeePassX-0.2.2.deb
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
user@host:~/Desktop$ sudo apt-get install KeePassX-0.2.2.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package KeePassX-0.2.2.deb
user@host:~/Desktop$ sudo apt-get install ~/Desktop/ KeePassX-0.2.2.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package
user@host:~/Desktop$
```

I have no problems using Synaptic, but KeePass is not in there (I installed easyubuntu, and chose the main, universe, and that other one). Can I add a source forge repository sudo apt-get update works just fine.


The biggest problem though is that I can't install Firefox 1.5.7 into /usr/lib/ where Firefox is located. I can untar in my home partition, but thats not useful. Was I suppose to untar/install it there. (libstdc++5 is installed).
You can ignore ^ that. I just came across this helpful script. 
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

Thanks for any help.:D

---

### Post by zerone on 2006-09-11
Try this:
```
wget http://ovh.dl.sourceforge.net/sourceforge/keepassx/KeePassX-0.2.2.deb
sudo dpkg -i KeePassX-0.2.2.deb
```

You must install qt4 libs too:
```
wget http://keepassx.sourceforge.net/download/qt4_4.1.3-2_i386.deb
sudo dpkg -i qt4_4.1.3-2_i386.deb
```

---

### Post by CupofDice on 2006-09-11
```
user@Host:~$ wget [http://ovh.dl.sourceforge.net/source...assX-0.2.2.deb](http://ovh.dl.sourceforge.net/source...assX-0.2.2.deb)
--12:34:11--  [http://ovh.dl.sourceforge.net/source...assX-0.2.2.deb](http://ovh.dl.sourceforge.net/source...assX-0.2.2.deb)
           => `source...assX-0.2.2.deb'
Resolving ovh.dl.sourceforge.net... 213.186.33.91
Connecting to ovh.dl.sourceforge.net|213.186.33.91|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/source...assX-0.2.2.deb?download&failedmirror=ovh.dl.sourceforge.net](http://prdownloads.sourceforge.net/source...assX-0.2.2.deb?download&failedmirror=ovh.dl.sourceforge.net) [following]
--12:34:12--  [http://prdownloads.sourceforge.net/source...assX-0.2.2.deb?download&failedmirror=ovh.dl.sourceforge.net](http://prdownloads.sourceforge.net/source...assX-0.2.2.deb?download&failedmirror=ovh.dl.sourceforge.net)
           => `source...assX-0.2.2.deb?download&failedmirror=ovh.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:34:12 ERROR 404: Not Found.

user@Host:~$ sudo dpkg -i KeePassX-0.2.2.deb wget [http://keepassx.sourceforge.net/down...1.3-2_i386.deb](http://keepassx.sourceforge.net/down...1.3-2_i386.deb)
dpkg: error processing KeePassX-0.2.2.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing wget (--install):
 cannot access archive: No such file or directory
dpkg: error processing [http://keepassx.sourceforge.net/down...1.3-2_i386.deb](http://keepassx.sourceforge.net/down...1.3-2_i386.deb) (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 KeePassX-0.2.2.deb
 wget
 [http://keepassx.sourceforge.net/down...1.3-2_i386.deb](http://keepassx.sourceforge.net/down...1.3-2_i386.deb)
user@Host:~$ sudo dpkg -i qt4_4.1.3-2_i386.deb
```

---

### Post by zerone on 2006-09-11
Sorry, I use QUOTE

It will work now.

Try this:
```
wget http://ovh.dl.sourceforge.net/sourceforge/keepassx/KeePassX-0.2.2.deb
sudo dpkg -i KeePassX-0.2.2.deb
```

You must install qt4 libs too:
```
wget http://keepassx.sourceforge.net/download/qt4_4.1.3-2_i386.deb
sudo dpkg -i qt4_4.1.3-2_i386.deb
```

---

### Post by CupofDice on 2006-09-11
```
user@host:~$ wget http://ovh.dl.sourceforge.net/sourceforge/keepassx/KeePassX-0.2.2.deb
--14:08:03--  http://ovh.dl.sourceforge.net/sourceforge/keepassx/KeePassX-0.2.2.deb
           => `KeePassX-0.2.2.deb.1'
Resolving ovh.dl.sourceforge.net... 213.186.33.91
Connecting to ovh.dl.sourceforge.net|213.186.33.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 404,434 (395K) [application/octet-stream]

100%[====================================>] 404,434      189.78K/s

14:08:06 (189.29 KB/s) - `KeePassX-0.2.2.deb.1' saved [404434/404434]

user@host:~$ sudo dpkg -i KeePassX-0.2.2.deb
Selecting previously deselected package keepassx.
(Reading database ... 71608 files and directories currently installed.)
Unpacking keepassx (from KeePassX-0.2.2.deb) ...
Setting up keepassx (0.2.2-2) ...
user@host:~$ wget http://keepassx.sourceforge.net/download/qt4_4.1.3-2_i386.deb
--14:08:31--  http://keepassx.sourceforge.net/download/qt4_4.1.3-2_i386.deb
           => `qt4_4.1.3-2_i386.deb'
Resolving keepassx.sourceforge.net... 66.35.250.209
Connecting to keepassx.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45,964,000 (44M) [text/plain]

100%[====================================>] 45,964,000   298.49K/s    ETA 00:00

14:11:08 (286.12 KB/s) - `qt4_4.1.3-2_i386.deb' saved [45964000/45964000]
user@host:~$ sudo dpkg -i qt4_4.1.3-2_i386.deb
Selecting previously deselected package qt4.
(Reading database ... 71657 files and directories currently installed.)
Unpacking qt4 (from qt4_4.1.3-2_i386.deb) ...
dpkg: dependency problems prevent configuration of qt4:
 qt4 depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 qt4 depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
dpkg: error processing qt4 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 qt4
user@host:~$
```

---

### Post by zerone on 2006-09-11
Sorry...](*,) 

Try this ... again

```

http://mesh.dl.sourceforge.net/sourceforge/keepassx/KeePassX-0.2.2-bin.tar.gz
tar -xvzf KeePassX-0.2.2-bin.tar.gz

```

To run KeePassX:
```

./KeePassX-0.2.2-bin/keepass.sh

```

I'm newbie

/Sorry my english

---

### Post by CupofDice on 2006-09-11
No problem:D .
It seems that qt4 was broke on my system

Software index is broken
> 
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first. 

so I uninstalled. 

Right now I am redoing 
```
wget http://keepassx.sourceforge.net/download/qt4_4.1.3-2_i386.deb
sudo dpkg -i qt4_4.1.3-2_i386.deb
```

```
user@host:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  qt4
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 151MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 81322 files and directories currently installed.)
Removing qt4 ...



user@host:~$ wget http://keepassx.sourceforge.net/download/qt4_4.1.3-2_i386.deb
--14:47:19--  http://keepassx.sourceforge.net/download/qt4_4.1.3-2_i386.deb
           => `qt4_4.1.3-2_i386.deb.1'
Resolving keepassx.sourceforge.net... 66.35.250.209
Connecting to keepassx.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45,964,000 (44M) [text/plain]

100%[====================================>] 45,964,000   295.00K/s    ETA 00:00

14:49:59 (281.24 KB/s) - `qt4_4.1.3-2_i386.deb.1' saved [45964000/45964000]

user@host:~$ sudo dpkg -i qt4_4.1.3-2_i386.deb

user@host:~$ sudo dpkg -i qt4_4.1.3-2_i386.deb
Selecting previously deselected package qt4.
(Reading database ... 71657 files and directories currently installed.)
Unpacking qt4 (from qt4_4.1.3-2_i386.deb) ...
dpkg: dependency problems prevent configuration of qt4:
 qt4 depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 qt4 depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
dpkg: error processing qt4 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 qt4

```

And that error sign just popped right back up. So i get rid of it again. And now 

```
user@host:~$ http://mesh.dl.sourceforge.net/sourceforge/keepassx/KeePassX-0.2.2-bin.tar.gz
bash: http://mesh.dl.sourceforge.net/sourceforge/keepassx/KeePassX-0.2.2-bin.tar.gz: No such file or directory
user@host:~$ tar -xvzf KeePassX-0.2.2-bin.tar.gz
tar: KeePassX-0.2.2-bin.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
user@host:~$ ./KeePassX-0.2.2-bin/keepass.sh
bash: ./KeePassX-0.2.2-bin/keepass.sh: No such file or directory
user@host:~$
```

---

### Post by zerone on 2006-09-11
Let's we try again
1. Download file from
[http://prdownloads.sourceforge.net/keepassx/KeePassX-0.2.2-bin.tar.gz?download](http://prdownloads.sourceforge.net/keepassx/KeePassX-0.2.2-bin.tar.gz?download)
2. Untar it
3. There will be dir KeePassX. Go there
4. And there will be file keepass.sh - run  it

---

### Post by CupofDice on 2006-09-11
THANK YOU!=D> =D> =D>  Worked perfectly. Just a little question. How do I run it? Do I use the sh file every time, terminal, or was it supposed to install a icon.

---

### Post by zerone on 2006-09-11
You can creat activator (or something like that). Just right click on desktop and click "new activator".

---

### Post by CupofDice on 2006-09-11
Thanks. You were a great help.:D

---

### Post by eldy on 2006-10-11
Thank you! It's finally working!

---

