---
title: "Software center errors"
date: 2013-12-07
forum: General Help
---

### Post by austinramsay on 2013-12-07
I tried installing code blocks by downloading the .deb files and did dpkg -i *.deb and then it failed, then I went onto the ubuntu software center and im getting an error saying i have an error with currently installed software. It asks if i want to repair or cancel so i try the repair but it gives:

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 160813 files and directories currently installed.)
Preparing to replace codeblocks-contrib 12.11-2 (using .../codeblocks-contrib_12.11-2_amd64.deb) ...
Unpacking replacement codeblocks-contrib ...
dpkg: error processing /var/cache/apt/archives/codeblocks-contrib_12.11-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/codeblocks/plugins/libabbreviations.so', which is also in package codeblocks 12.11-2
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/codeblocks-contrib_12.11-2_amd64.deb
dpkg: dependency problems prevent configuration of codeblocks-contrib:
 codeblocks-contrib depends on libgamin0; however:
  Package libgamin0 is not installed.
 codeblocks-contrib depends on libhunspell-1.2-0 (>= 1.2.11); however:
  Package libhunspell-1.2-0 is not installed.


dpkg: error processing codeblocks-contrib (--configure):
 dependency problems - leaving unconfigured
```

What am I supposed to do? What is this telling me? I know it's saying it has dependency problems but how do I just delete everything and start over? It wont let me uninstall code blocks from the software center because it keeps giving the error.

---

### Post by varunendra on 2013-12-07
Welcome to the forums austinramsay !

Have you tried purging the offending package? That is -
```
sudo dpkg -P codeblocks-contrib
```

It might have been easier to troubleshoot the Software Center errors and install codeblocks from the default repositories. What was that error by the way?

---

### Post by andrej1741 on 2013-12-07
```
sudo apt-get update
```?

---

### Post by ian-weisser on 2013-12-07
Did you install CodeBlocks *only* from the Ubuntu Repositories?
This kind of error sometimes occurs if you also installed from a PPA or other non-Ubuntu repository, and didn't uninstall it completely.

---

### Post by heir4c on 2013-12-07
> I tried installing code blocks by downloading the .deb files and did dpkg -i *.deb and then it failed

> **ian-weisser said:**
> Did you install CodeBlocks *only* from the Ubuntu Repositories?
This kind of error sometimes occurs if you also installed from a PPA or other non-Ubuntu repository, and didn't uninstall it completely.

@austinramsay,
Why you want to install a .deb file when the program/package is in the repository of Ubuntu. Open UbuntuSoftwareCenter (or Synaptic if it's installed) and search for codeblocks.
Search always first in the repo's before you download a .deb or other installation file.
And if you install a .deb file (in a graphic environment) why use dpkg -i ? You can just doubleclick on it to install it.

---

### Post by austinramsay on 2013-12-08
> **varunendra said:**
> Welcome to the forums austinramsay !

Have you tried purging the offending package? That is -
```
sudo dpkg -P codeblocks-contrib
```

It might have been easier to troubleshoot the Software Center errors and install codeblocks from the default repositories. What was that error by the way?

That got rid of the errors and let me remove codeblocks in the software center but then i tried installing it from the software center and got: 

```
installArchives() failed: (Reading database ... (Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 160729 files and directories currently installed.)
Unpacking codeblocks (from .../codeblocks_12.11-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/codeblocks_12.11-2_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/cb_share_config.1.gz', which is also in package codeblocks-common 12.11-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/codeblocks_12.11-2_amd64.deb
Error in function: 
```

> **andrej1741 said:**
> ```
sudo apt-get update
```?

Done and didnt help!

> **heir4c said:**
> @austinramsay,
Why you want to install a .deb file when the program/package is in the repository of Ubuntu. Open UbuntuSoftwareCenter (or Synaptic if it's installed) and search for codeblocks.
Search always first in the repo's before you download a .deb or other installation file.
And if you install a .deb file (in a graphic environment) why use dpkg -i ? You can just doubleclick on it to install it.

I have no idea usually i just install from software center but i downloaded codeblocks from online and read some instruction to install it like that for some reason. Bad idea!

---

### Post by mc4man on 2013-12-08
I would clean your archives - 
```
sudo apt-get clean
```
Then remove any codeblocks packages that are installed, if any. To see run
```
apt-cache policy codeblocks*
```
If any are shown as installed then completely  remove them, (purge),  then update your sources. (sudo apt-get update

After that try from cli
```
sudo apt-get install codeblocks codeblocks-contrib
```

---

### Post by austinramsay on 2013-12-08
It wouldnt let me uninstall everything in that list from apt-cache policy codeblocks*, but it let me purge everything but 2 things. (libcodeblocks0, and codeblocks-libwxcontrib0). So i tried installing it again anyways though but still got:

```
Reading package lists... Doneaustin@dv5:~$ sudo apt-get install codeblocks codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  codeblocks-common libc6-dbg valgrind
Suggested packages:
  libwxgtk2.8-dev wx-common valgrind-dbg kcachegrind alleyoop valkyrie
The following NEW packages will be installed:
  codeblocks codeblocks-common codeblocks-contrib libc6-dbg valgrind
0 upgraded, 5 newly installed, 0 to remove and 257 not upgraded.
Need to get 44.8 MB of archives.
After this operation, 156 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/universe codeblocks-common all 12.11-2 [2,717 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ raring/universe codeblocks amd64 12.11-2 [1,852 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ raring/universe codeblocks-contrib amd64 12.11-2 [4,637 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libc6-dbg amd64 2.17-0ubuntu5.1 [3,511 kB]                                      
Get:5 http://us.archive.ubuntu.com/ubuntu/ raring/main valgrind amd64 1:3.8.1-1ubuntu5 [32.1 MB]                                               
Fetched 44.8 MB in 41s (1,075 kB/s)                                                                                                            
Selecting previously unselected package codeblocks-common.
(Reading database ... 165750 files and directories currently installed.)
Unpacking codeblocks-common (from .../codeblocks-common_12.11-2_all.deb) ...
Unpacking codeblocks (from .../codeblocks_12.11-2_amd64.deb) ...
Selecting previously unselected package codeblocks-contrib.
Unpacking codeblocks-contrib (from .../codeblocks-contrib_12.11-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/codeblocks-contrib_12.11-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/codeblocks/wxContribItems/libwxkwic.so.0.0.1', which is also in package codeblocks-libwxcontrib0 12.11-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package libc6-dbg:amd64.
Unpacking libc6-dbg:amd64 (from .../libc6-dbg_2.17-0ubuntu5.1_amd64.deb) ...
Selecting previously unselected package valgrind.
Unpacking valgrind (from .../valgrind_1%3a3.8.1-1ubuntu5_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Errors were encountered while processing:
 /var/cache/apt/archives/codeblocks-contrib_12.11-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
austin@dv5:~$
```

---

### Post by ian-weisser on 2013-12-08
> **austinramsay said:**
>  it let me purge everything but 2 things. (libcodeblocks0, and codeblocks-libwxcontrib0).

```

dpkg: error processing /var/cache/apt/archives/codeblocks-contrib_12.11-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/codeblocks/wxContribItems/libwxkwic.so.0.0.1', which is also in package codeblocks-libwxcontrib0 12.11-2

```

codeblock-libwxcontrib0 conflicts with codeblocks-contrib. You won't make progress until it is removed.
How are you trying to remove libcodeblocks0 and codeblocks-libwxcontrib0, and what errors are you getting?

---

### Post by andrej1741 on 2013-12-09
I'm sorry. I do not speak English well, so it meant that you should write output of this command
```
sudo apt-get update
```
and output of
```
apt-cache show codeblocks
```
can be useful.

---

