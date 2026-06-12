---
title: "In  the Terminal with 12.10"
date: 2012-12-19
forum: General Help
---

### Post by Frankiewizard on 2012-12-19
Why am I getting this message in the terminal after I do an up date ?

dpkg: error processing libgnomeui-0:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libbonoboui2-0:amd64
 libgnomeui-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

:confused:

---

### Post by wladypauly on 2012-12-19
Try ```
sudo apt-get -f install
``` in a Terminal to force the configuration of those packages. It will give you two options: either to remove the packages left unconfigured, or to install some additional packages needed by them (the unconfigured ones). 
P.S. Sorry for my English, I'm a non-native speaker :)

---

### Post by Frankiewizard on 2012-12-19
I have tryed it but am getting

 E: Sub-process /usr/bin/dpkg returned an error code (1)

By the way your english is fine.

---

### Post by Bucky Ball on 2012-12-19
Perhaps:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```... one at a time, in that order. The last command will not upgrade your Ubuntu release to the next one, just upgrade whatever you have installed and their dependencies ...

(ps: pretty cool looking wizard in that avatar ... ;))

---

### Post by Frankiewizard on 2012-12-19
Cheers Bucky Ball,
after using>
[HTML]sudo apt-get autoremove[/HTML]

I got this

[HTML]dpkg: error processing libgnomeui-0:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libbonoboui2-0:amd64
 libgnomeui-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ 
[/HTML]

I am not sure if it is a real problem. Everything on the computer works perfectly with the > error <. I just thought the forum should be a aware of it.

Any way thanks for all the help. Cheers.

---

### Post by Frogs Hair on 2012-12-19
Try the following.```
sudo dpkg --configure -a
```

If there are no errors. ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Frankiewizard on 2012-12-19
[HTML]frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ sudo dpkg --configure -a
[sudo] password for frankiewizard: 
dpkg: dependency problems prevent configuration of libgnomeui-0:amd64:
 libgnomeui-0:amd64 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0:amd64 is not installed.

dpkg: error processing libgnomeui-0:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnomeui-0:amd64
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ 
[/HTML]


[HTML]frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ sudo apt-get update && sudo apt-get upgrade
Ign http://extras.ubuntu.com quantal InRelease
Ign http://archive.canonical.com quantal InRelease                             
Ign http://security.ubuntu.com quantal-security InRelease                      
Ign http://fr.archive.ubuntu.com quantal InRelease                             
Hit http://extras.ubuntu.com quantal Release.gpg                               
Hit http://archive.canonical.com quantal Release.gpg                           
Ign http://fr.archive.ubuntu.com quantal-updates InRelease                     
Get:1 http://security.ubuntu.com quantal-security Release.gpg [933 B]          
Ign http://dl.google.com stable InRelease                                      
Ign http://deb.opera.com stable InRelease                                      
Ign http://fr.archive.ubuntu.com quantal-backports InRelease                   
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://archive.canonical.com quantal Release                               
Get:2 http://security.ubuntu.com quantal-security Release [49.6 kB]            
Hit http://dl.google.com stable Release.gpg                                    
Hit http://fr.archive.ubuntu.com quantal Release.gpg                           
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://fr.archive.ubuntu.com quantal-updates Release.gpg                   
Hit http://archive.canonical.com quantal/partner amd64 Packages                
Hit http://dl.google.com stable Release                                        
Hit http://extras.ubuntu.com quantal/main amd64 Packages                       
Hit http://fr.archive.ubuntu.com quantal-backports Release.gpg                 
Hit http://deb.opera.com stable Release                                        
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Hit http://fr.archive.ubuntu.com quantal Release                               
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://fr.archive.ubuntu.com quantal-updates Release                       
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://fr.archive.ubuntu.com quantal-backports Release                     
Get:3 http://security.ubuntu.com quantal-security/main Sources [22.4 kB]       
Hit http://fr.archive.ubuntu.com quantal/main Sources                          
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://fr.archive.ubuntu.com quantal/restricted Sources                    
Hit http://fr.archive.ubuntu.com quantal/universe Sources                      
Hit http://fr.archive.ubuntu.com quantal/multiverse Sources                    
Hit http://fr.archive.ubuntu.com quantal/main amd64 Packages                   
Hit http://fr.archive.ubuntu.com quantal/restricted amd64 Packages             
Get:4 http://security.ubuntu.com quantal-security/restricted Sources [14 B]    
Hit http://fr.archive.ubuntu.com quantal/universe amd64 Packages               
Get:5 http://security.ubuntu.com quantal-security/universe Sources [9,109 B]   
Hit http://fr.archive.ubuntu.com quantal/multiverse amd64 Packages             
Ign http://archive.canonical.com quantal/partner Translation-en_GB             
Ign http://extras.ubuntu.com quantal/main Translation-en_GB                    
Ign http://archive.canonical.com quantal/partner Translation-en                
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Get:6 http://security.ubuntu.com quantal-security/multiverse Sources [699 B]   
Get:7 http://security.ubuntu.com quantal-security/main amd64 Packages [62.2 kB]
Hit http://fr.archive.ubuntu.com quantal/main i386 Packages                    
Hit http://fr.archive.ubuntu.com quantal/restricted i386 Packages              
Hit http://fr.archive.ubuntu.com quantal/universe i386 Packages                
Hit http://fr.archive.ubuntu.com quantal/multiverse i386 Packages              
Hit http://fr.archive.ubuntu.com quantal/main Translation-en_GB                
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://fr.archive.ubuntu.com quantal/main Translation-en                   
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Hit http://fr.archive.ubuntu.com quantal/multiverse Translation-en_GB          
Ign http://dl.google.com stable/main Translation-en                            
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://fr.archive.ubuntu.com quantal/multiverse Translation-en             
Hit http://fr.archive.ubuntu.com quantal/restricted Translation-en_GB
Hit http://fr.archive.ubuntu.com quantal/restricted Translation-en
Hit http://fr.archive.ubuntu.com quantal/universe Translation-en_GB
Hit http://fr.archive.ubuntu.com quantal/universe Translation-en       
Get:8 http://security.ubuntu.com quantal-security/restricted amd64 Packages [14 B]
Hit http://fr.archive.ubuntu.com quantal-updates/main Sources          
Hit http://fr.archive.ubuntu.com quantal-updates/restricted Sources
Get:9 http://security.ubuntu.com quantal-security/universe amd64 Packages [22.2 kB]
Hit http://fr.archive.ubuntu.com quantal-updates/universe Sources
Hit http://fr.archive.ubuntu.com quantal-updates/multiverse Sources
Get:10 http://security.ubuntu.com quantal-security/multiverse amd64 Packages [1,150 B]
Get:11 http://security.ubuntu.com quantal-security/main i386 Packages [61.8 kB]
Hit http://fr.archive.ubuntu.com quantal-updates/main amd64 Packages
Hit http://fr.archive.ubuntu.com quantal-updates/restricted amd64 Packages
Hit http://fr.archive.ubuntu.com quantal-updates/universe amd64 Packages
Hit http://fr.archive.ubuntu.com quantal-updates/multiverse amd64 Packages
Hit http://fr.archive.ubuntu.com quantal-updates/main i386 Packages
Hit http://fr.archive.ubuntu.com quantal-updates/restricted i386 Packages
Hit http://fr.archive.ubuntu.com quantal-updates/universe i386 Packages
Hit http://fr.archive.ubuntu.com quantal-updates/multiverse i386 Packages
Hit http://fr.archive.ubuntu.com quantal-updates/main Translation-en
Get:12 http://security.ubuntu.com quantal-security/restricted i386 Packages [14 B]
Hit http://fr.archive.ubuntu.com quantal-updates/multiverse Translation-en
Get:13 http://security.ubuntu.com quantal-security/universe i386 Packages [22.9 kB]
Hit http://fr.archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://fr.archive.ubuntu.com quantal-updates/universe Translation-en
Get:14 http://security.ubuntu.com quantal-security/multiverse i386 Packages [1,391 B]
Hit http://fr.archive.ubuntu.com quantal-backports/main Sources         
Hit http://fr.archive.ubuntu.com quantal-backports/restricted Sources
Hit http://security.ubuntu.com quantal-security/main Translation-en
Hit http://fr.archive.ubuntu.com quantal-backports/universe Sources
Hit http://fr.archive.ubuntu.com quantal-backports/multiverse Sources
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en
Hit http://fr.archive.ubuntu.com quantal-backports/main amd64 Packages
Hit http://fr.archive.ubuntu.com quantal-backports/restricted amd64 Packages
Hit http://fr.archive.ubuntu.com quantal-backports/universe amd64 Packages
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit http://fr.archive.ubuntu.com quantal-backports/multiverse amd64 Packages
Hit http://fr.archive.ubuntu.com quantal-backports/main i386 Packages
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Hit http://fr.archive.ubuntu.com quantal-backports/restricted i386 Packages
Hit http://fr.archive.ubuntu.com quantal-backports/universe i386 Packages
Hit http://fr.archive.ubuntu.com quantal-backports/multiverse i386 Packages
Hit http://fr.archive.ubuntu.com quantal-backports/main Translation-en
Hit http://fr.archive.ubuntu.com quantal-backports/multiverse Translation-en
Hit http://fr.archive.ubuntu.com quantal-backports/restricted Translation-en
Hit http://fr.archive.ubuntu.com quantal-backports/universe Translation-en
Ign http://security.ubuntu.com quantal-security/main Translation-en_GB
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_GB
Ign http://security.ubuntu.com quantal-security/universe Translation-en_GB
Ign http://fr.archive.ubuntu.com quantal-updates/main Translation-en_GB
Ign http://fr.archive.ubuntu.com quantal-updates/multiverse Translation-en_GB
Ign http://fr.archive.ubuntu.com quantal-updates/restricted Translation-en_GB
Ign http://fr.archive.ubuntu.com quantal-updates/universe Translation-en_GB
Ign http://fr.archive.ubuntu.com quantal-backports/main Translation-en_GB
Ign http://fr.archive.ubuntu.com quantal-backports/multiverse Translation-en_GB
Ign http://fr.archive.ubuntu.com quantal-backports/restricted Translation-en_GB
Ign http://fr.archive.ubuntu.com quantal-backports/universe Translation-en_GB
Fetched 254 kB in 5s (49.7 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0 B/189 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libbonoboui2-0:amd64 (--configure):
 package libbonoboui2-0:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
dpkg: dependency problems prevent configuration of libgnomeui-0:amd64:
 libgnomeui-0:amd64 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0:amd64 is not installed.

dpkg: error processing libgnomeui-0:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libbonoboui2-0:amd64
 libgnomeui-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ 
[/HTML]

---

### Post by Frogs Hair on 2012-12-19
The package you are having problems with is successfully installed on my 12.10 installation. Was the installation an upgrade or clean installation ?

---

### Post by Bashing-om on 2012-12-19
Frankiewizard; Hi !

Before delving deeper into this, try this to resolve package conflicts:
```
sudo apt-get dist-upgrade
```[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by Frankiewizard on 2012-12-20
> **Frogs Hair said:**
> The package you are having problems with is successfully installed on my 12.10 installation. Was the installation an upgrade or clean installation ?

It was indeed an upgrade from 12.04 LTS

---

### Post by Frankiewizard on 2012-12-20
> **Bashing-om said:**
> Frankiewizard; Hi !

Before delving deeper into this, try this to resolve package conflicts:
```
sudo apt-get dist-upgrade
```[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]


[HTML]frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ sudo apt-get dist-upgrade
[sudo] password for frankiewizard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/189 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libbonoboui2-0:amd64 (--configure):
 package libbonoboui2-0:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
dpkg: dependency problems prevent configuration of libgnomeui-0:amd64:
 libgnomeui-0:amd64 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0:amd64 is not installed.

dpkg: error processing libgnomeui-0:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libbonoboui2-0:amd64
 libgnomeui-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$[/HTML]

Ho dear what could be going wrong ?

---

### Post by Bucky Ball on 2012-12-20
> **Bashing-om said:**
> 
```
sudo apt-get dist-upgrade
```

ALWAYS run:

```
sudo apt-get update
```... before you run the dist-upgrade command ...

---

### Post by Bashing-om on 2012-12-20
@Bucky Ball ..Will try and keep that in mind, thanks heaps.

@Frankiewizard; .. What are you looking like now ?

[INDENT]progressing on ==> BDQ

[/INDENT]

---

