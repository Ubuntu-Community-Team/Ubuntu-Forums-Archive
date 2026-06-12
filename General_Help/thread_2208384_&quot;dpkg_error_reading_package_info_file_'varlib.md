---
title: "&quot;dpkg: error: reading package info file '/var/lib/dpkg/status': Input/output error&quot;"
date: 2014-02-28
forum: General Help
---

### Post by Hrvoje_Herceg on 2014-02-28
After installing squid i cant install nothing anymore.
H am new in ubuntu and cant understand what is going on.
when i try update heres what i get:

```
herc@herc-MacBook ~ $ sudo apt-get update
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                               
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                                           
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                    
Hit [http://dist.bitcasa.com](http://dist.bitcasa.com) debian Release.gpg                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                        
Hit [http://dist.bitcasa.com](http://dist.bitcasa.com) debian Release                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                                              
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                        
Hit [http://dist.bitcasa.com](http://dist.bitcasa.com) debian/main i386 Packages                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release                                          
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [192 kB]                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main i386 Packages                                       
Get:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia Release.gpg [198 B]                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted i386 Packages                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe i386 Packages                                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                             
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia Release [18.6 kB]                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse i386 Packages                                 
Get:6 [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia/main i386 Packages [22.3 kB]                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en                                      
Ign [http://dist.bitcasa.com](http://dist.bitcasa.com) debian/main Translation-en_US                                      
Get:7 [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia/upstream i386 Packages [11.3 kB]                     
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [3,531 B]           
Ign [http://dist.bitcasa.com](http://dist.bitcasa.com) debian/main Translation-en                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en                                
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US                             
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [71.1 kB]             
Get:10 [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia/import i386 Packages [44.3 kB]                      
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en                                
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,727 B]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe i386 Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia/import Translation-en_US                               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia/import Translation-en                                  
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia/main Translation-en_US                                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia/main Translation-en                                    
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia/upstream Translation-en_US                             
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia/upstream Translation-en                                
Fetched 416 kB in 9s (45.2 kB/s)                                                               
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
```

so when i do it:

```
herc@herc-MacBook ~ $ sudo dpkg --configure -a
[sudo] password for herc: 
dpkg: error: reading package info file '/var/lib/dpkg/status': Input/output error
```

PLEASE HELP!
THANK YOU!

---

### Post by jeanjd63 on 2014-02-28
Hello
You can try this :
[B]sudo  mv  [COLOR=#000000]/var/lib/dpkg/status [/COLOR][COLOR=#000000]/var/lib/dpkg/status.ko
sudo  cp  [/COLOR][COLOR=#000000]/var/lib/dpkg/status-old  [/COLOR][COLOR=#000000]/var/lib/dpkg/status
sudo  dpkg  --configure -a[/COLOR][/B]

---

### Post by Hrvoje_Herceg on 2014-02-28
Thanky you for quick reply...
now i have to choose to keep current version or install maintainers?
what should i choose?

---

### Post by Hrvoje_Herceg on 2014-02-28
this is how it looks:
herc@herc-MacBook ~ $ sudo dpkg --configure -a
Setting up desktop-file-utils (0.20-0.1ubuntu1) ...

Configuration file `/etc/gnome/defaults.list'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** defaults.list (Y/I/N/O/D/Z) [default=N] ?

---

### Post by jeanjd63 on 2014-02-28
I think you can keep the file and simply do "Enter"

---

### Post by Hrvoje_Herceg on 2014-02-28
Wow thank you!It worked.
I just made update and it worked.Great
You are KING!

---

### Post by jeanjd63 on 2014-02-28
May be "Solved" 
By

---

### Post by Hrvoje_Herceg on 2014-02-28
Sorry to bother you but i cant install anything with apt-get install 
sudo apt-get install gparted
[sudo] password for herc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  squid-langpack squid3 squid3-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgtkmm-2.4-1c2a
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils ntfsprogs yelp kpartx dmraid gpart
The following NEW packages will be installed:
  gparted libgtkmm-2.4-1c2a
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 1,553 kB of archives.
After this operation, 5,837 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main libgtkmm-2.4-1c2a i386 1:2.24.2-1ubuntu2 [1,018 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main gparted i386 0.12.1-1 [535 kB]            
Fetched 1,553 kB in 11s (136 kB/s)                                                             
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

Can u help me again?

---

### Post by jeanjd63 on 2014-02-28
You can do this :
[B]sudo  cp  [COLOR=#000000]/var/lib/dpkg/available-old  [/COLOR][COLOR=#000000]/var/lib/dpkg/available
[/COLOR][/B][COLOR=#000000]and after [/COLOR][B][COLOR=#000000]
sudo  apt-get  install -f
[/COLOR][/B]**[COLOR=#000000][/COLOR]**[COLOR=#000000]and[/COLOR][B][COLOR=#000000]
sudo  apt-get  update
sudo  apt-get  upgrade
sudo  apt-get  autoremove[/COLOR][/B]

---

### Post by Hrvoje_Herceg on 2014-02-28
Unfortunally i dont have that file available or available-old in folder..can understand!I cant find it and error is:

sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
[sudo] password for herc: 
cp: cannot stat `/var/lib/dpkg/available-old': No such file or directory

---

### Post by jeanjd63 on 2014-02-28
What gave :
**sudo  ls  -l  [COLOR=#000000]/var/lib/dpkg/[/COLOR]**

---

### Post by Hrvoje_Herceg on 2014-02-28
this:
herc@herc-MacBook ~ $ sudo ls -l /var/lib/dpkg/
total 6308
drwxr-xr-x 2 root root    4096 Feb 23 15:52 alternatives
-rw-r--r-- 1 root root       8 Oct 17  2012 cmethopt
-rw-r--r-- 1 root root     603 Feb 23 15:52 diversions
-rw-r--r-- 1 root root     497 Feb 23 15:52 diversions-old
drwxr-xr-x 2 root root  401408 Feb 28 12:19 info
-rw-r----- 1 root root       0 Feb 28 12:21 lock
-rw-r----- 1 root root       0 Feb 28 06:55 lock1
drwxr-xr-x 2 root root    4096 Oct  1  2012 parts
-rw-r--r-- 1 root root     135 Oct 17  2012 statoverride
-rw-r--r-- 1 root root 2002930 Feb 28 12:19 status
-rw-r--r-- 1 root root 2009783 Feb 26 22:23 status.ko
-rw-r--r-- 1 root root 2004154 Feb 28 11:28 status-old
drwxr-xr-x 2 root root    4096 Feb 26 22:23 triggers
drwxr-xr-x 2 root root    4096 Feb 28 12:19 updates

---

### Post by jeanjd63 on 2014-02-28
do a :
**[COLOR=#000000]sudo  rm  /var/lib/dpkg/lock*[/COLOR]**
[B]sudo  dpkg --clear-avail
[/B]and :
[B]sudo apt-get  install -f
sudo apt-get  autoremove
sudo apt-get  update
sudo  apt-get upgrade[/B]

---

### Post by Hrvoje_Herceg on 2014-02-28
I just didi it but whan i install for example gparted i get error in line:

Processing triggers for man-db ...
/usr/bin/mandb: can't read from /var/cache/man/index.db: Input/output error

but instalatiomis complete now..
Is that ok?

---

### Post by Hrvoje_Herceg on 2014-02-28
and i cant start gparted i just installed...nothing happens?

---

### Post by jeanjd63 on 2014-02-28
You have a problem with your disk.
You can try :
[B]sudo -i
[/B][COLOR=#111111][FONT=Consolas]**touch /forcefsck**
and reboot[/FONT][/COLOR]

---

