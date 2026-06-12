---
title: "Error 139 makes me crazy! Please help."
date: 2007-07-30
forum: General Help
---

### Post by navneeth on 2007-07-30
Till this morning I was a very happy computer user, and a very happy Ubuntu user. 

While using the evil OS this morning, the stuff of the monitor disappeared all of a sudden. I could start the CPU, but nothing appeared on the monitor. Well, that problem was settled a bit later - I could then boot into either OS. I think I can say with some certainity that the problem was hardware associated. But ever since, Ubuntu has been acting a bit crazy. More importanty Firefox (in Ubuntu) has been problematic. It wouldn't launch, and even if it did, it would crash. (seg. fault, core dump, etc.). I tried uninstalling and reinstalling, but it wouldn't because of the error that keeps popping-up. :(

I feel **CRIPPLED** without my Firefox and its settings (thank goodness for FEBE!) PLEASE HELP! I'm having to make-do with Opera, but it's no Firefox. It takes me more than 5 seconds to look-up an article in Wikipedia. :( :D [Something like this has not happened before, btw]

```
navneeth@ubuntu:~$ sudo apt-get autoremove
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfaad2-0 libnspr4-0d libgd2-noxpm gnuplot-x11 gnuplot-nox cabextract
  libmozjs0d
The following packages will be REMOVED:
  cabextract gnuplot-nox gnuplot-x11 libfaad2-0 libgd2-noxpm libmozjs0d
  libnspr4-0d
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4452kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 138029 files and directories currently installed.)
Removing cabextract ...
Removing gnuplot-x11 ...
Removing gnuplot-nox ...
Removing libfaad2-0 ...
Removing libgd2-noxpm ...
Removing libmozjs0d ...
Removing libnspr4-0d ...
Setting up firefox (2.0.0.5+1-0ubuntu1) ...
Segmentation fault (core dumped)
dpkg: error processing firefox (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)
navneeth@ubuntu:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del libqt4-qt3support 4.3.0-2ubuntu1~feisty1 [1039kB]
Del libqt4-sql 4.3.0-2ubuntu1~feisty1 [156kB]
Del libqt4-core 4.3.0-2ubuntu1~feisty1 [1673kB]
Del libqt4-gui 4.3.0-2ubuntu1~feisty1 [4879kB]
Del automatix2 1.1-4.11-7.04feisty_i386 [257kB]
Del libqt4-dev 4.3.0-2ubuntu1~feisty1 [4284kB]
navneeth@ubuntu:~$ sudo apt-get remove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox sun-java6-plugin yelp
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.9MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 137954 files and directories currently installed.)
Removing sun-java6-plugin ...
Segmentation fault (core dumped)
dpkg: error processing sun-java6-plugin (--remove):
 subprocess pre-removal script returned error exit status 139
Removing yelp ...
Segmentation fault (core dumped)
dpkg: error processing yelp (--remove):
 subprocess pre-removal script returned error exit status 139
dpkg: firefox: dependency problems, but removing anyway as you request:
 sun-java6-plugin depends on firefox | iceweasel | mozilla-firefox | iceape | mozilla-browser | epiphany-browser | galeon | konqueror; however:
  Package firefox is to be removed.
  Package iceweasel is not installed.
  Package mozilla-firefox is not installed.
  Package iceape is not installed.
  Package mozilla-browser is not installed.
  Package epiphany-browser is not installed.
  Package galeon is not installed.
  Package konqueror is not installed.
 yelp depends on firefox (>= 1.5).
Removing firefox ...
Segmentation fault (core dumped)
dpkg: error processing firefox (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 sun-java6-plugin
 yelp
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)
navneeth@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
navneeth@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  firefox sun-java6-plugin yelp
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.9MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 136515 files and directories currently installed.)
Removing sun-java6-plugin ...
Segmentation fault (core dumped)
dpkg: error processing sun-java6-plugin (--remove):
 subprocess pre-removal script returned error exit status 139
Removing yelp ...
Segmentation fault (core dumped)
dpkg: error processing yelp (--remove):
 subprocess pre-removal script returned error exit status 139
dpkg: firefox: dependency problems, but removing anyway as you request:
 sun-java6-plugin depends on firefox | iceweasel | mozilla-firefox | iceape | mozilla-browser | epiphany-browser | galeon | konqueror; however:
  Package firefox is to be removed.
  Package iceweasel is not installed.
  Package mozilla-firefox is not installed.
  Package iceape is not installed.
  Package mozilla-browser is not installed.
  Package epiphany-browser is not installed.
  Package galeon is not installed.
  Package konqueror is not installed.
 yelp depends on firefox (>= 1.5).
Removing firefox ...
Segmentation fault (core dumped)
dpkg: error processing firefox (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 sun-java6-plugin
 yelp
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Paul S on 2007-07-30
I think this is a bug with "apt-get autoremove", so stop using it.  In fact, with upgrade to feisty, we are supposed to stop using "apt-get" and switch to "aptitude".  So you need to change.

In the meantime, keep trying this until you get success:

sudo dpkg -P --force-all firefox
sudo dpkg -P --force-all sun-java6-plugin
sudo dpkg -P --force-all yelp
sudo apt-get -f install
sudo apt-get --purge remove firefox
sudo apt-get --purge remove sun-java6-plugin
sudo apt-get --purge remove yelp
sudo apt-get install firefox sun-java6-plugin yelp

HTH

---

### Post by navneeth on 2007-07-30
> **Paul S said:**
> I think this is a bug with "apt-get autoremove", so stop using it.  In fact, with upgrade to feisty, we are supposed to stop using "apt-get" and switch to "aptitude".  So you need to change.

In the meantime, keep trying this until you get success:

sudo dpkg -P --force-all firefox
sudo dpkg -P --force-all sun-java6-plugin
sudo dpkg -P --force-all yelp
sudo apt-get -f install
sudo apt-get --purge remove firefox
sudo apt-get --purge remove sun-java6-plugin
sudo apt-get --purge remove yelp
sudo apt-get install firefox sun-java6-plugin yelp

HTH

Thanks. I will try that. 

I doubt if it has anything to do with autoremove, since the first time I got this error was when I tried to remove Firefox via synaptic*. As for autoremove, I got a message saying that there was stuff that I didn't need, and they could be removed with autoremove.

*Exact message : E: firefox: subprocess post-installation script returned error exit
status 139

---

### Post by navneeth on 2007-07-30
```
navneeth@ubuntu:~$ sudo dpkg -P --force-all firefox
Password:
dpkg: firefox: dependency problems, but removing anyway as you request:
 sun-java6-plugin depends on firefox | iceweasel | mozilla-firefox | iceape | mozilla-browser | epiphany-browser | galeon | konqueror; however:
  Package firefox is to be removed.
  Package iceweasel is not installed.
  Package mozilla-firefox is not installed.
  Package iceape is not installed.
  Package mozilla-browser is not installed.
  Package epiphany-browser is not installed.
  Package galeon is not installed.
  Package konqueror is not installed.
(Reading database ... 137907 files and directories currently installed.)
Removing firefox ...
Purging configuration files for firefox ...
dpkg - warning: while removing firefox, directory `/usr/lib/firefox/components' not empty so not removed.
navneeth@ubuntu:~$ sudo dpkg -P --force-all sun-java6-plugin
(Reading database ... 136452 files and directories currently installed.)
Removing sun-java6-plugin ...
Segmentation fault (core dumped)
dpkg: error processing sun-java6-plugin (--purge):
 subprocess pre-removal script returned error exit status 139
Errors were encountered while processing:
 sun-java6-plugin
navneeth@ubuntu:~$ sudo dpkg -P --force-all yelp
(Reading database ... 136452 files and directories currently installed.)
Removing yelp ...
Purging configuration files for yelp ...
navneeth@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox
Suggested packages:
  firefox-gnome-support latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9262kB of archives.
After unpacking 29.4MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
navneeth@ubuntu:~$ sudo apt-get --purge remove sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  sun-java6-plugin*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 73.7kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 136452 files and directories currently installed.)
Removing sun-java6-plugin ...
Segmentation fault (core dumped)
dpkg: error processing sun-java6-plugin (--purge):
 subprocess pre-removal script returned error exit status 139
Errors were encountered while processing:
 sun-java6-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
navneeth@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox
Suggested packages:
  firefox-gnome-support latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9262kB of archives.
After unpacking 29.4MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
navneeth@ubuntu:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  sun-java6-plugin 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  sun-java6-plugin: Depends: firefox but it is not installable or
                             iceweasel which is a virtual package. or
                             mozilla-firefox but it is not installable or
                             iceape which is a virtual package. or
                             mozilla-browser which is a virtual package. or
                             epiphany-browser but it is not installable or
                             galeon but it is not installable or
                             konqueror but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
firefox [2.0.0.5+1-0ubuntu1 (feisty-security, feisty-security)]

Score is -19

Accept this solution? [Y/n/q/?] 

```

It's the java-plugin. :( There's the update icon sitting on the panel waiting for me to install Firefox. I've tried that a few times, and Fx keeps crashing. Will installing the "pure-version" (non-Ubuntu) help?

---

