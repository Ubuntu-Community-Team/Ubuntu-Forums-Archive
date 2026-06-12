---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-03-31
forum: General Help
---

### Post by CCgirl6690 on 2013-03-31
Hello 
i Love this forum so is why i ask my questions in here mostly 
i was doing a apt-get purge gnome-power-manager and i stopped it in the middle 
so now what ever i want to do i get this error

E: Sub-process /usr/bin/dpkg returned an error code (1)

help me out please........  heres some examples 
thank you
```
root@bt:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  smartphone-pentest-framework
The following packages will be upgraded:
  android-sdk magictree
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/106MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4942 package 'magictree':
 error in Version string 'r1643-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 14545 package 'udptunnel':
 error in Version string 'r19-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 18397 package 'untidy':
 error in Version string 'beta2-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 20735 package 'pwntcha':
 error in Version string 'rev4780-bt3': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 24654 package 'android-sdk':
 error in Version string 'r20.0.1-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 34530 package 'webslayer':
 error in Version string 'rev5-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 38757 package 'protos-sip':
 error in Version string 'r2-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 4955 package 'magictree':
 error in Version string 'r1643-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 14706 package 'udptunnel':
 error in Version string 'r19-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 18506 package 'untidy':
 error in Version string 'beta2-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 20876 package 'pwntcha':
 error in Version string 'rev4780-bt3': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 24799 package 'android-sdk':
 error in Version string 'r20.0.1-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 34639 package 'webslayer':
 error in Version string 'rev5-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 38423 package 'wifite':
 error in Version string 'r85-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 38770 package 'protos-sip':
 error in Version string 'r2-bt1': version number does not start with digit
dpkg: error processing /var/cache/apt/archives/android-sdk_r20.0.3-bt0_all.deb (--unpack):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 3 package 'android-sdk':
 error in Version string 'r20.0.3-bt0': version number does not start with digit
dpkg: error processing /var/cache/apt/archives/magictree_r1802-bt0_all.deb (--unpack):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 3 package 'magictree':
 error in Version string 'r1802-bt0': version number does not start with digit
Errors were encountered while processing:
 /var/cache/apt/archives/android-sdk_r20.0.3-bt0_all.deb
 /var/cache/apt/archives/magictree_r1802-bt0_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@bt:~
```

---

### Post by Frogs Hair on 2013-03-31
You can try the following ```
sudo apt-get autoremove
``````
sudo apt-get clean
``` ```
sudo apt-get update
```

---

### Post by CCgirl6690 on 2013-03-31
```
root@bt:~# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apport-gtk bogl-bterm cryptsetup cvs dmraid ecryptfs-utils gdb
  libaccess-bridge-java libaccess-bridge-java-jni libdebconfclient0
  libdebian-installer4 libdmraid1.0.0.rc16 libecryptfs0 libgadu3 libsilc-1.1-2
  libsilcclient-1.1-3 python-pyicu rdate reiserfsprogs
0 upgraded, 0 newly installed, 19 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 14.2MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4942 package 'magictree':
 error in Version string 'r1643-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 14545 package 'udptunnel':
 error in Version string 'r19-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 18397 package 'untidy':
 error in Version string 'beta2-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 20735 package 'pwntcha':
 error in Version string 'rev4780-bt3': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 24654 package 'android-sdk':
 error in Version string 'r20.0.1-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 34530 package 'webslayer':
 error in Version string 'rev5-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 38757 package 'protos-sip':
 error in Version string 'r2-bt1': version number does not start with digit
(Reading database ... 271730 files and directories currently installed.)
Removing apport-gtk ...
Removing bogl-bterm ...
Removing cryptsetup ...
update-initramfs: deferring update (trigger activated)
Removing cvs ...
Removing dmraid ...
update-initramfs: deferring update (trigger activated)
Removing ecryptfs-utils ...
Removing gdb ...
Removing libaccess-bridge-java-jni ...
Removing libaccess-bridge-java ...
Removing libdebconfclient0 ...
Removing libdebian-installer4 ...
Removing libdmraid1.0.0.rc16 ...
Removing libecryptfs0 ...
Removing libgadu3 ...
Removing libsilc-1.1-2 ...
Removing libsilcclient-1.1-3 ...
Removing python-pyicu ...
Removing rdate ...
Removing reiserfsprogs ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.6
Processing triggers for install-info ...
Processing triggers for menu ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 4942 package 'magictree':
 error in Version string 'r1643-bt0': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 14545 package 'udptunnel':
 error in Version string 'r19-bt0': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 18397 package 'untidy':
 error in Version string 'beta2-bt1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 20735 package 'pwntcha':
 error in Version string 'rev4780-bt3': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 24654 package 'android-sdk':
 error in Version string 'r20.0.1-bt0': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 34530 package 'webslayer':
 error in Version string 'rev5-bt0': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 38757 package 'protos-sip':
 error in Version string 'r2-bt1': version number does not start with digit
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4945 package 'magictree':
 error in Version string 'r1643-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 14528 package 'udptunnel':
 error in Version string 'r19-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 18362 package 'untidy':
 error in Version string 'beta2-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 20682 package 'pwntcha':
 error in Version string 'rev4780-bt3': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 24604 package 'android-sdk':
 error in Version string 'r20.0.1-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 34465 package 'webslayer':
 error in Version string 'rev5-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 38673 package 'protos-sip':
 error in Version string 'r2-bt1': version number does not start with digit
Setting up subterfuge (4.3-bt0) ...
tar (child): SubterfugePublicBeta4.3.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
/var/lib/dpkg/info/subterfuge.postinst: line 6: cd: subterfuge/: No such file or directory
python: can't open file 'installer_old.py': [Errno 2] No such file or directory
rm: cannot remove `SubterfugePublicBeta4.3.tar.gz': No such file or directory
dpkg: error processing subterfuge (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 subterfuge
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@bt:~# 

```

---

### Post by Frogs Hair on 2013-03-31
If smartphone-pentest-framework is a third party application it may be the cause of the problem. I don't see it my repository but I am running 13.04 beta.

```
sudo apt-get -f install
```

---

### Post by Nutster on 2013-03-31
It looks like some of the **dpkg** database entries have become corrupted.  To fix this, try:
```
sudo dpkg --audit | more
```
If it finds anything, it should also give you instructions on how to fix it.  If the output from this does not make sense to you, post the whole thing here and one of us will walk you through what you should do.

Something else that might help is to purge uninstalled packages.
```
sudo dpkg -l | grep -v '^ii' | more
```
Purge each package you want to completely remove.  You can put multiple packages on one line; just separate them with spaces.
```
sudo apt-get purge *package_name*
```

---

### Post by schragge on 2013-03-31
**Nutster**'s suggestions above are quite reasonable, so try them first. I'll only allow myself to amend the last command. As *apt-get* is known to bail out on any dpkg errors, a safer bet is purging packages directly with dpkg:
```
sudo dpkg -P --force-remove-reinstreq *package_name*
```
Unfortunately, even this may not succeed as a corruption of */var/lib/dpkg/status* pretty seriously affects dpkg's ability to perform any actions. OTOH, any damage to */var/lib/dpkg/available* is easily fixable with
```
sudo dpkg --clear-avail
```

If */var/lib/dpkg/status* actually got corrupted as the error messages suggest, I'm afraid you need to repair it by hand. There's a backup copy of the file in */var/lib/dpkg/status-old*, so first try using it:
```

sudo mv -v /var/lib/dpkg/status{,.save}
sudo cp -v /var/lib/dpkg/status{-old,}
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade

```
If this doesn't work, you can try older backups of *dpkg.status* stored under */var/backup/*
If they also don't work, you have two options: either looking into damaged dpkg.status, and trying to edit the wrong entries or re-creating it from scratch as described [here]("http://linuxmafia.com/faq/Debian/package-database-rebuild.html"). Quite possible, you will be able to make some shortcuts compared to procedure in the linked article as you most probably still have the whole */var/lib/dpkg* infrastructure intact.

Just in case you want to quickly assess what damage */var/lib/dpkg/status* has sustained, here is a simple way to do it:
```
grep -n . /var/lib/dpkg/status.save|egrep -C1 '^(4942|14545|18397|20735|24654|34530|38757):'
```

Also, could you please edit the name of this thread and change it to something like **Errors parsing /var/lib/dpkg/status**? There are many threads about update problems in the forum; most of them are benign and can be dealt with using apt-get commands like suggested by **Frogs Hair** above. Your case is different.

[highlight]Update[/highlight]
FYI, [Same issue as yours]("http://www.backtrack-linux.org/forums/showthread.php?t=49318"). Are you running BackTrack Linux? All the **-bt** parts in package versions suggest so. Or is it Kali Linux? As those dreaded */var/lib/dpkg/status* parsing errors are only warnings in your case, perhaps they are not consequences of an interrupted upgrade process, but instead just evidence of sloppy packaging practice on the part of BT developers. Have you observed them before? Then please ignore all I said above. If by chance you are trying to install packages from BT/Kali on Ubuntu then this may not work because they are not intended for Ubuntu. Still, you can try
```

sudo apt-get clean
sudo dpkg --clear-avail
sudo dpkg -P --force-remove-reinstreq subterfuge magictree udptunnel untidy pwntcha android-sdk webslayer protos-sip

```

---

### Post by CCgirl6690 on 2013-04-01
Hello Schrage  
thanks for your help 
i tried your last recommendation  , i got some errors but didnt get that main error . and yes im on BT  . please take a look and see of its fixed . im not sure....
P.S  thanks anyone  else who tried to help 
```
root@bt:~# apt-get clean
root@bt:~# sudo dpkg --clear-avai
dpkg: error: unknown option --clear-avai

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
root@bt:~# dpkg --clear-avai
dpkg: error: unknown option --clear-avai

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
root@bt:~# dpkg -P --force-remove-reinstreq subterfuge magictree udptunnel untidy pwntcha android-sdk webslayer protos-sip
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 14506 package 'udptunnel':
 error in Version string 'r19-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 18340 package 'untidy':
 error in Version string 'beta2-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 20660 package 'pwntcha':
 error in Version string 'rev4780-bt3': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 34433 package 'webslayer':
 error in Version string 'rev5-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 38641 package 'protos-sip':
 error in Version string 'r2-bt1': version number does not start with digit
dpkg: warning: there's no installed package matching magictree
dpkg: warning: there's no installed package matching android-sdk
(Reading database ... 270726 files and directories currently installed.)
Removing subterfuge ...
Removing udptunnel ...
Removing untidy ...
Removing pwntcha ...
Removing webslayer ...
Removing protos-sip ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
root@bt:~# apt-get update
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://32.repository.backtrack-linux.org revolution Release.gpg            
Ign http://32.repository.backtrack-linux.org/ revolution/main Translation-en_US
Ign http://32.repository.backtrack-linux.org/ revolution/microverse Translation-en_US
Hit http://all.repository.backtrack-linux.org revolution Release.gpg           
Ign http://all.repository.backtrack-linux.org/ revolution/main Translation-en_US
Ign http://all.repository.backtrack-linux.org/ revolution/microverse Translation-en_US
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                           
Hit http://updates.repository.backtrack-linux.org revolution Release.gpg       
Ign http://all.repository.backtrack-linux.org/ revolution/non-free Translation-en_US
Ign http://all.repository.backtrack-linux.org/ revolution/testing Translation-en_US
Ign http://32.repository.backtrack-linux.org/ revolution/non-free Translation-en_US
Ign http://32.repository.backtrack-linux.org/ revolution/testing Translation-en_US
Hit http://32.repository.backtrack-linux.org revolution Release                
Hit http://all.repository.backtrack-linux.org revolution Release               
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://32.repository.backtrack-linux.org revolution/main Packages          
Hit http://all.repository.backtrack-linux.org revolution/main Packages         
Ign http://updates.repository.backtrack-linux.org/ revolution/main Translation-en_US
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://32.repository.backtrack-linux.org revolution/microverse Packages    
Hit http://32.repository.backtrack-linux.org revolution/non-free Packages      
Hit http://32.repository.backtrack-linux.org revolution/testing Packages       
Hit http://all.repository.backtrack-linux.org revolution/microverse Packages   
Hit http://all.repository.backtrack-linux.org revolution/non-free Packages     
Hit http://all.repository.backtrack-linux.org revolution/testing Packages
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://updates.repository.backtrack-linux.org/ revolution/microverse Translation-en_US
Ign http://updates.repository.backtrack-linux.org/ revolution/non-free Translation-en_US
Ign http://updates.repository.backtrack-linux.org/ revolution/testing Translation-en_US
Hit http://updates.repository.backtrack-linux.org revolution Release    
Hit http://updates.repository.backtrack-linux.org revolution/main Packages
Hit http://updates.repository.backtrack-linux.org revolution/microverse Packages
Hit http://updates.repository.backtrack-linux.org revolution/non-free Packages
Hit http://updates.repository.backtrack-linux.org revolution/testing Packages
Reading package lists... Done
root@bt:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  smartphone-pentest-framework
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@bt:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libdevice-serialport-perl
The following packages will be upgraded:
  smartphone-pentest-framework
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,316kB of archives.
After this operation, 319kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://all.repository.backtrack-linux.org/ revolution/testing smartphone-pentest-framework 0.1.2-bt1 [1,237kB]
Get:2 http://32.repository.backtrack-linux.org/ revolution/main libdevice-serialport-perl 1.04-2 [79.4kB]
Fetched 1,316kB in 1min 38s (13.4kB/s)                                                 
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 4955 package 'magictree':
 error in Version string 'r1643-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 14706 package 'udptunnel':
 error in Version string 'r19-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 18506 package 'untidy':
 error in Version string 'beta2-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 20876 package 'pwntcha':
 error in Version string 'rev4780-bt3': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 24799 package 'android-sdk':
 error in Version string 'r20.0.1-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 34639 package 'webslayer':
 error in Version string 'rev5-bt0': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 38423 package 'wifite':
 error in Version string 'r85-bt1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 38770 package 'protos-sip':
 error in Version string 'r2-bt1': version number does not start with digit
Selecting previously unselected package libdevice-serialport-perl.
(Reading database ... 270499 files and directories currently installed.)
Unpacking libdevice-serialport-perl (from .../libdevice-serialport-perl_1.04-2_i386.deb) ...
Preparing to replace smartphone-pentest-framework 0.1-bt1 (using .../smartphone-pentest-framework_0.1.2-bt1_all.deb) ...
Unpacking replacement smartphone-pentest-framework ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up libdevice-serialport-perl (1.04-2) ...
Setting up smartphone-pentest-framework (0.1.2-bt1) ...
root@bt:~# 
 
```

---

### Post by schragge on 2013-04-01
Glad it worked. To get rid of dpkg warnings, run
```
dpkg --clear-avai[COLOR=red]l[/COLOR]
``` You made a typo last time.

---

### Post by CCgirl6690 on 2013-04-04
> **schragge said:**
> Glad it worked. To get rid of dpkg warnings, run
```
dpkg --clear-avai[COLOR=red]l[/COLOR]
``` You made a typo last time.

thank you so much . solved so far
love this forum

---

