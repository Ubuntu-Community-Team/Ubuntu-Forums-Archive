---
title: "Installing Latest Pidgin PPA fails on 12.04"
date: 2014-12-17
forum: General Help
---

### Post by panorain on 2014-12-17
Hi, I have Ubuntu 12.04  installed on my computer. I have been trying to add the PPA for the  latest Pidgin messenger. 

[https://launchpad.net/~pidgin-developers/+archive/ubuntu/ppa?field.series_filter=precise]("https://launchpad.net/%7Epidgin-developers/+archive/ubuntu/ppa?field.series_filter=precise") <----Pidgin Developer PPA link.

I enter this command below in the terminal.

     Code:
     sudo add-apt-repository ppapidgin-developers/ppa 
Terminal Reports as follows:
--------------------------------
You are about to add the following PPA to your system:
 This PPA contains packages of the current version of Pidgin for all   versions of Ubuntu currently supported on the desktop. This allows you   to stay current with Pidgin while using a stable release of Ubuntu.
 More info: [https://launchpad.net/~pidgin-developer ... ubuntu/ppa]("https://launchpad.net/%7Epidgin-developers/+archive/ubuntu/ppa")
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing:  gpg --ignore-time-conflict --no-options --no-default-keyring   --secret-keyring /tmp/tmp.sRekqrI2sR --trustdb-name  /etc/apt/trustdb.gpg  --keyring /etc/apt/trusted.gpg --primary-keyring  /etc/apt/trusted.gpg  --keyserver [hkp://keyserver.ubuntu.com:80/](hkp://keyserver.ubuntu.com:80/) --recv 67265EB522BDD6B1C69E66ED7FB8BEE0A1F196A8
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: failed to create temporary file `/etc/apt/.#lk0x8c13910.desk/paul-HP.20273': No such file or directory
gpg: can't allocate lock for `/etc/apt/trusted.gpg'
gpg: failed to create temporary file `/tmp/.#lk0x8c13910.desk/paul-HP.20273': No such file or directory
gpg: can't allocate lock for `/tmp/tmp.sRekqrI2sR'
gpg: error writing keyring `/etc/apt/trusted.gpg': general error
gpg: key A1F196A8: public key "[User ID not found]" imported
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
gpg:               imported: 1  (RSA: 1)
paul@desk/paul-HP ~ $ 

     Code:
     apt-key list 
Terminal Reports as follows:
--------------------------------
gpg: failed to create temporary file `/home/paul/.gnupg/.#lk0x9afc8d0.desk/paul-HP.20288': No such file or directory
gpg: fatal: can't create lock for `/home/paul/.gnupg/trustdb.gpg'
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768

     Code:
     sudo apt-get update 
Terminal Reports as follows:
--------------------------------
Fetched 2,116 kB in 10s (206 kB/s)                                             
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net)   precise Release: The following signatures couldn't be verified because   the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8

How can I simply add this public key? 

I  tried it on another desktop running Ubuntu 10.04 with the same  failure.  I have to tried enabling backports prior to the 'apt-get  update'. I  don't want all those backports installed on my system just  the latest  Pidgin messenger. I know this PPA is not for Ubuntu 10.04  but I figured I  would try to install the PPA on the Ubuntu machine just  to see - and it  failed on that machine also. Any ideas are  appreciated.

Thank's for your help.

---

### Post by ibjsb4 on 2014-12-18
There are several ways to fix this error.  Take your choice.

[https://www.google.com/search?client=ubuntu&channel=fs&q=GPG+error+NO_PUBKEY+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=GPG+error+NO_PUBKEY+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by panorain on 2014-12-19
Thanks for your response.

I get this message:

paul@desk/paul-HP ~ $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7FB8BEE0A1F196A8
[sudo] password for paul: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.3I9GiVISuv --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 7FB8BEE0A1F196A8
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: failed to create temporary file `/etc/apt/.#lk0x8ad7c40.desk/paul-HP.4464': No such file or directory
gpg: can't allocate lock for `/etc/apt/trusted.gpg'
gpg: failed to create temporary file `/tmp/.#lk0x8ad7c40.desk/paul-HP.4464': No such file or directory
gpg: can't allocate lock for `/tmp/tmp.3I9GiVISuv'
gpg: error writing keyring `/etc/apt/trusted.gpg': general error
gpg: key A1F196A8: public key "[User ID not found]" imported
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
gpg:               imported: 1  (RSA: 1)
paul@desk/paul-HP ~ $

Any ideas?

---

### Post by ibjsb4 on 2014-12-19
Ok, I tried it on my 12o4 install.

```
sudo add-apt-repository ppa:pidgin-developers/ppa
bla, bla, bla
You are about to add the following PPA to your system:
bla, bla, bla
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpV9fleg/secring.gpg' created
gpg: keyring `/tmp/tmpV9fleg/pubring.gpg' created
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpV9fleg/trustdb.gpg: trustdb created
gpg: key A1F196A8: public key "Launchpad PPA for Pidgin Developers" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```

So it works for me.
A couple of things come to mind.
1) Did you completely remove the old pidgin?  May cause this conflict.
2) Could it be another ppa causing a conflict? Code:  ls /etc/apt/sources.list.d/*.list
3) Maybe using 'gdebi' would give better results for you.  [https://www.pidgin.im/download/ubuntu/](https://www.pidgin.im/download/ubuntu/)

The package 'ppa-purge' could come in handy.

---

### Post by panorain on 2014-12-19
Thank you for your help this issue as it has been nagging me for a few weeks. I actually wrote to the lead Pidgin developer and I/we were unable to come to any conclusion as to why I get this message coming up in terminal after quite some hours on my end.

Yes, I did remove the old Pidgin out via synaptic before I tried installing the key/ Actually the new Pidgin version 2.10.10 does appear in synaptic properly via I clk the 'http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu' repo. The issue of course on my end is that I am dealing with this key failing to import.

Here's an output in my terminal again. 

paul@desk/paul-HP ~ $ ls /etc/apt/sources.list.d/*.list
/etc/apt/sources.list.d/local-repository.list
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list
paul@desk/paul-HP ~ $ apt-key list 
gpg: failed to create temporary file `/home/paul/.gnupg/.#lk0x88ec8d0.desk/paul-HP.2653': No such file or directory
gpg: fatal: can't create lock for `/home/paul/.gnupg/trustdb.gpg'
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768

Here is actually the terminal output of/when I try to install the current pidgin.deb package from the Pidgin link you provided. (I had been on that page many times a couple weeks ago)

Selecting previously unselected package pidgin-ppa.
(Reading database ... 211991 files and directories currently installed.)
Unpacking pidgin-ppa (from .../pidgin-ppa_0.0.7_all.deb) ...
Setting up pidgin-ppa (0.0.7) ...
gpg: failed to create temporary file `/etc/apt/.#lk0x88e8988.desk/paul-HP.2750': No such file or directory
gpg: can't allocate lock for `/etc/apt/trusted.gpg'
gpg: failed to create temporary file `/tmp/.#lk0x88e8988.desk/paul-HP.2750': No such file or directory
gpg: can't allocate lock for `/tmp/tmp.SrLiOOlD6H'
gpg: error writing keyring `/etc/apt/trusted.gpg': general error
gpg: error reading `/usr/share/pidgin-ppa/pidgin-ppa.asc': general error
gpg: import from `/usr/share/pidgin-ppa/pidgin-ppa.asc' failed: general error
dpkg: error processing pidgin-ppa (--install):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 pidgin-ppa

For some reason my system is failing to be able to import GPG-keys I really have never even tried to even add odd/different repositories to this machine in the past. The situation is really the first time.

Would you think that trying to go back to just default source list would help? I added a 14.04 pidgin ppa prior to see if that one would install but same errors. 

Your assistance is certainly welcome and I appreciate your help with this.

---

### Post by slickymaster on 2014-12-19
Just as a _**crazy thought**_, you could delete all of the GPG keys in **/etc/apt**, add that key and re-run apt-get update:
```
cd /etc/apt
sudo rm *.gpg
gpg --export -a [COLOR=#000000]A1F196A8[/COLOR] | sudo apt-key add -
sudo apt-get update
```
_Beware that I'm not certain of the results you might get_, so if you're willing to try it, be certain to make a copy of your **/etc/apt/trusted.gpg** file.

---

### Post by panorain on 2014-12-19
Thanks for your Rapid response. Here is the output in terminal below. Prior to those commands I went and clk'd the Pidgin-Precise ppa. <---just to make sure thats done before: 
```

paul@desk/paul-HP ~ $ cd /etc/apt
paul@desk/paul-HP /etc/apt $ ls -lah
total 88K
drwxr-xr-x   6 root root 4.0K Nov 27  2013 .
drwxr-xr-x 168 root root  12K Dec 19 00:28 ..
drwxr-xr-x   2 root root 4.0K Nov 14 19:51 apt.conf.d
-rw-r--r--   1 root root  172 May  3  2012 preferences
drwxr-xr-x   2 root root 4.0K Apr 20  2012 preferences.d
-rw-r--r--   1 root root  707 Dec 19 00:59 sources.list
drwxr-xr-x   2 root root 4.0K Nov 28 16:36 sources.list.d
-rw-r--r--   1 root root  707 Dec 19 00:59 sources.list.save
-rw-------   1 root root 1.2K Apr  2  2013 trustdb.gpg
-rw-r--r--   1 root root  17K Apr  2  2013 trusted.gpg
-rw-r--r--   1 root root  17K Apr  2  2013 trusted.gpg~
drwxr-xr-x   2 root root 4.0K Apr 20  2012 trusted.gpg.d


```
paul@desk/paul-HP /etc/apt $ sudo rm *.gpg
[sudo] password for paul: 
paul@desk/paul-HP /etc/apt $ gpg --export -a A1F196A8 | sudo apt-key add -
gpg: can't open `/home/paul/.gnupg/pubring.gpg'
gpg: WARNING: nothing exported
gpg: key export failed: file open error
gpg: failed to create temporary file `/etc/apt/.#lk0x8a598f0.desk/paul-HP.2930': No such file or directory
gpg: keyblock resource `/etc/apt/trusted.gpg': general error
gpg: no valid OpenPGP data found.
paul@desk/paul-HP /etc/apt $ 

Now performing apt-get update the following errors reports:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: No keyring installed in /etc/apt/trusted.gpg.d/.
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release: No keyring installed in /etc/apt/trusted.gpg.d/.
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://packages.linuxmint.com](http://packages.linuxmint.com) maya Release: No keyring installed in /etc/apt/trusted.gpg.d/.

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release: No keyring installed in /etc/apt/trusted.gpg.d/.

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: No keyring installed in /etc/apt/trusted.gpg.d/.
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: No keyring installed in /etc/apt/trusted.gpg.d/.
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release: No keyring installed in /etc/apt/trusted.gpg.d/.
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  

Somethings going on apparently.

---

### Post by panorain on 2014-12-21
Are there any ideas as to how to install a fresh keyring on 12.04? I apologize for double posting. 

paul@desk/paul-HP /etc/apt $ apt-key list
gpg: failed to create temporary file `/home/paul/.gnupg/.#lk0x95608d0.desk/paul-HP.3288': No such file or directory
gpg: fatal: can't create lock for `/home/paul/.gnupg/trustdb.gpg'
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768
paul@desk/paul-HP /etc/apt $ sudo apt-key list
gpg: failed to create temporary file `/etc/apt/.#lk0x90e4b60.desk/paul-HP.3302': No such file or directory
gpg: fatal: can't create lock for `/etc/apt/trustdb.gpg'
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768
paul@desk/paul-HP /etc/apt $ 

paul@desk/paul-HP ~/.gnupg $ ls -lah
total 36K
drwx------  2 paul paul 4.0K Nov 27 02:31 .
drwx------ 57 paul paul 4.0K Dec 21 08:32 ..
-rw-------  1 paul paul 9.3K Nov 27 02:31 gpg.conf
-rw-------  1 paul paul 9.3K Nov 27 02:29 gpg.conf~
-rw-------  1 root root    0 May 24  2013 pubring.gpg
-rw-------  1 paul paul    0 May 24  2013 secring.gpg
-rw-------  1 paul paul 1.2K May 24  2013 trustdb.gpg
paul@desk/paul-HP ~/.gnupg $ 


I think that may be the anwser here 'installing a gpg-keyring fresh. Could there be a way to 'reinstall 'gpg' from scratch not compling of course. Could I have a permission error? <---just some thoughts.

Thank You.

---

### Post by slickymaster on 2014-12-22
Try to reinstall the ubuntu-keyring package:```
sudo apt-get install --reinstall ubuntu-keyring
```

---

### Post by panorain on 2014-12-22
paul@desk/paul-HP ~ $ sudo apt-get install --reinstall ubuntu-keyring
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
Need to get 16.7 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main ubuntu-keyring all 2011.11.21.1 [16.7 kB]
Fetched 16.7 kB in 0s (36.7 kB/s)   
(Reading database ... 211531 files and directories currently installed.)
Preparing to replace ubuntu-keyring 2011.11.21.1 (using .../ubuntu-keyring_2011.11.21.1_all.deb) ...
Unpacking replacement ubuntu-keyring ...
Setting up ubuntu-keyring (2011.11.21.1) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
gpg: failed to create temporary file `/etc/apt/.#lk0x97f18f0.desk/paul-HP.4493': No such file or directory
gpg: fatal: can't create lock for `/etc/apt/trustdb.gpg'
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768
paul@desk/paul-HP ~ $ 

paul@desk/paul-HP ~ $ cd /etc/apt/
paul@desk/paul-HP /etc/apt $ ls -lah
total 64K
drwxr-xr-x   6 root root 4.0K Dec 21 09:50 .
drwxr-xr-x 168 root root  12K Dec 21 13:12 ..
drwxr-xr-x   2 root root 4.0K Nov 14 19:51 apt.conf.d
-rw-r--r--   1 root root  172 May  3  2012 preferences
drwxr-xr-x   2 root root 4.0K Apr 20  2012 preferences.d
-rw-r--r--   1 root root  707 Dec 19 10:00 sources.list
drwxr-xr-x   2 root root 4.0K Nov 28 16:36 sources.list.d
-rw-r--r--   1 root root  707 Dec 19 10:00 sources.list.save
-rw-------   1 root root    0 Dec 19 09:42 trustdb.gpg
-rw-r--r--   1 root root  17K Apr  2  2013 trusted.gpg
drwxr-xr-x   2 root root 4.0K Apr 20  2012 trusted.gpg.d
paul@desk/paul-HP /etc/apt $ 

Is there something going on with this line ---> gpg: failed to create temporary file `/etc/apt/.#lk0x97f18f0.desk/paul-HP.4493': No such file or directory <--- 

I have changed the hosts/hostname on this computer <---for what that may matter. That was done months ago though. Via /etc/hosts & /etc/hostname files

/etc/hosts:
127.0.0.1    localhost
127.0.1.1    desk/paul-HP

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

/etc/hostname:
desk/paul-HP

Thank you for your help.

---

### Post by slickymaster on 2014-12-22
Can you please now run the following and post back the output you get:```
sudo apt-get update
sudo apt-get install pidgin
```

---

### Post by panorain on 2014-12-22
```
paul@desk/paul-HP ~ $ sudo apt-get update
[sudo] password for paul: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) maya Release.gpg [198 B]                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg                      
Get:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) maya Release [18.6 kB]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/main i386 Packages [18.2 kB]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Get:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/upstream i386 Packages [10.6 kB]      
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/import i386 Packages [41.5 kB]        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release.gpg                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/import TranslationIndex                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/main TranslationIndex                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en          
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/upstream TranslationIndex               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release                           
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps i386 Packages                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/import Translation-en_US                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/import Translation-en                   
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/main Translation-en_US                  
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/main Translation-en                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/upstream Translation-en_US              
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya/upstream Translation-en                 
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps TranslationIndex             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en_US            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en               
Fetched 89.0 kB in 7s (12.1 kB/s)                                              
Reading package lists... Done
paul@desk/paul-HP ~ $ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pidgin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
paul@desk/paul-HP ~ $ 
```

Thank you for your help.

---

### Post by slickymaster on 2014-12-22
So, pidgin is in your system, as you can prove by running```
apt-cache policy pidgin
```

---

### Post by panorain on 2014-12-22
paul@desk/paul-HP ~ $ apt-cache policy pidgin
pidgin:
  Installed: 1:2.10.10-1ubuntu0+pidgin9.12.04
  Candidate: 1:2.10.10-1ubuntu0+pidgin9.12.04
  Version table:
 *** 1:2.10.10-1ubuntu0+pidgin9.12.04 0
        100 /var/lib/dpkg/status
     1:2.10.3-0ubuntu1.6 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages
     1:2.10.3-0ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main i386 Packages
paul@desk/paul-HP ~ $ 

It looks as if it is. It's the 'Key situation' because when I open up 'Pidgin GUI --> Help --> About' = unknown' - right underneath <--whereis it should display 'KEY' information. And yes the failure to import the key correctly as we all can see above -> via the prior postings.

Not a good situation to start importing any packages on a system without the correct keys in place.

paul@desk/paul-HP ~ $ apt-key list
gpg: failed to create temporary file `/home/paul/.gnupg/.#lk0x9bf28d0.desk/paul-HP.5460': No such file or directory
gpg: fatal: can't create lock for `/home/paul/.gnupg/trustdb.gpg'
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768

Thank you for your help.

---

### Post by slickymaster on 2014-12-22
If you're referring to this, I don't think it's related. I also see it:
[ATTACH=CONFIG]258729[/ATTACH]

---

### Post by panorain on 2014-12-22
Good to have a second opinion and I appreciate your time to take that snapshot definately. My issue here is with the 'importing of key/key's problem'. I am just seriously wondering if this desktop got botched somehow. I have an old old 10.04 system and that has the same .gnupg key errors as well. Yes I know 10.04 is no longer supported but 12.04 sure is. 

Any thoughts are appreciated,

Thank you for your time.

p.s your screen shot explains correctly.

---

