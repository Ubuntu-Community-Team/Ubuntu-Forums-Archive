---
title: "Ubuntu Software Center error"
date: 2013-01-13
forum: General Help
---

### Post by 101kitty on 2013-01-13
```
"Package dependencies cannot be resolved"

"This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."
```

How can i fix this?

---

### Post by Anders Stroem on 2013-01-13
Have you added any external PPA:s recently?

You may want to follow the instructions in the first reply to [this post]("http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies") over at AskUbuntu.

---

### Post by ibjsb4 on 2013-01-13
If still having trouble, please post the output of ..

```
sudo apt-get update
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)


and :)

place output in code tags

[ATTACH]229989[/ATTACH]

---

### Post by 101kitty on 2013-01-13
```
sudo apt-get update
```Did not work, i'm trying to install playonlinux.

i could never find those things, i just type in the code my self.

---

### Post by 101kitty on 2013-01-13
```
kitty@ubuntu:~$ sudo wget http://deb.playonlinux.com/playonlinux_karmic.list -O /etc/apt/sources.list.d/playonlinux.list
[sudo] password for kitty: 
--2013-01-13 12:28:54--  http://deb.playonlinux.com/playonlinux_karmic.list
Resolving deb.playonlinux.com (deb.playonlinux.com)... 91.121.5.64, 2001:41d0:1:5840::1
Connecting to deb.playonlinux.com (deb.playonlinux.com)|91.121.5.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44 [text/plain]
Saving to: `/etc/apt/sources.list.d/playonlinux.list'

100%[======================================>] 44          --.-K/s   in 0s      

2013-01-13 12:28:55 (10.3 MB/s) - `/etc/apt/sources.list.d/playonlinux.list' saved [44/44]

kitty@ubuntu:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com quantal InRelease
Ign http://deb.playonlinux.com karmic InRelease                                
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Ign http://security.ubuntu.com quantal-security InRelease            
Ign http://ppa.launchpad.net quantal InRelease 
Hit http://us.archive.ubuntu.com quantal Release.gpg
Hit http://security.ubuntu.com quantal-security Release.gpg
Hit http://us.archive.ubuntu.com quantal-updates Release.gpg
Ign http://ppa.launchpad.net quantal InRelease 
Ign http://deb.playonlinux.com karmic Release.gpg
Hit http://us.archive.ubuntu.com quantal Release                     
Hit http://security.ubuntu.com quantal-security Release                        
Hit http://ppa.launchpad.net quantal Release.gpg                      
Hit http://us.archive.ubuntu.com quantal-updates Release
Ign http://deb.playonlinux.com karmic Release                                  
Hit http://security.ubuntu.com quantal-security/main Sources                   
Hit http://us.archive.ubuntu.com quantal/main Sources                
Hit http://ppa.launchpad.net quantal Release.gpg
Hit http://us.archive.ubuntu.com quantal/restricted Sources
Hit http://security.ubuntu.com quantal-security/restricted Sources
Hit http://ppa.launchpad.net quantal Release                         
Hit http://us.archive.ubuntu.com quantal/universe Sources                      
Hit http://security.ubuntu.com quantal-security/universe Sources               
Hit http://us.archive.ubuntu.com quantal/multiverse Sources          
Hit http://ppa.launchpad.net quantal Release                         
Hit http://us.archive.ubuntu.com quantal/main amd64 Packages                   
Hit http://security.ubuntu.com quantal-security/multiverse Sources             
Hit http://ppa.launchpad.net quantal/main Sources                    
Hit http://us.archive.ubuntu.com quantal/restricted amd64 Packages   
Hit http://security.ubuntu.com quantal-security/main amd64 Packages            
Hit http://us.archive.ubuntu.com quantal/universe amd64 Packages               
Hit http://ppa.launchpad.net quantal/main amd64 Packages             
Hit http://us.archive.ubuntu.com quantal/multiverse amd64 Packages   
Hit http://security.ubuntu.com quantal-security/restricted amd64 Packages
Hit http://security.ubuntu.com quantal-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com quantal/main Translation-en         
Hit http://security.ubuntu.com quantal-security/multiverse amd64 Packages
Hit http://ppa.launchpad.net quantal/main Sources                    
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en   
Hit http://security.ubuntu.com quantal-security/main Translation-en  
Hit http://ppa.launchpad.net quantal/main amd64 Packages             
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en             
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Hit http://us.archive.ubuntu.com quantal/universe Translation-en     
Hit http://us.archive.ubuntu.com quantal-updates/main Sources        
Hit http://us.archive.ubuntu.com quantal-updates/restricted Sources  
Hit http://us.archive.ubuntu.com quantal-updates/universe Sources    
Err http://deb.playonlinux.com karmic/main amd64 Packages            
  404  Not Found
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Sources  
Ign http://deb.playonlinux.com karmic/main Translation-en_US         
Hit http://us.archive.ubuntu.com quantal-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages
Ign http://deb.playonlinux.com karmic/main Translation-en            
Hit http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
W: Failed to fetch http://deb.playonlinux.com/dists/karmic/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
kitty@ubuntu:~$ sudo apt-get install playonlinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-unstable but it is not installable
E: Unable to correct problems, you have held broken packages.
kitty@ubuntu:~$ sudo apt-get install playonlinux^C

```


I even tried installing it using using codes, I'm going to see if it will work if i install wine first.

---

### Post by 101kitty on 2013-01-13
I hope you guys don't dont mind me posting everything i try, but it did not work it gave me the same error.

```
Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed
```

---

### Post by 101kitty on 2013-01-13
I tired using Synaptic package manger as well and it gave me this error massage.

```

Could not mark all packages for installation or upgrade

playonlinux:
 Depends: wine or
     wine-unstable  but it is not installable
```

---

### Post by ibjsb4 on 2013-01-13
Err [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main amd64 Packages

You have installed play-on-linux for karmic (9.10) and you are running 12.10, 
this will not work.  Remove it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Play-on-linux is in the software center.

---

### Post by 101kitty on 2013-01-13
i think i uninstalled it but not sure, still working on it and i dont see any amd64 there just a bunch of files.

---

### Post by ibjsb4 on 2013-01-14
Edit

---

### Post by ibjsb4 on 2013-01-14
Whats with this???

[http://ubuntuforums.org/showthread.php?t=2104813](http://ubuntuforums.org/showthread.php?t=2104813)

[http://ubuntuforums.org/showthread.php?t=2104694](http://ubuntuforums.org/showthread.php?t=2104694)

[http://ubuntuforums.org/showthread.php?t=2104626](http://ubuntuforums.org/showthread.php?t=2104626)

Multiple threads on same or similar problem leads to multiple answers with no interaction between threads and mass confusion for you and us.

---

