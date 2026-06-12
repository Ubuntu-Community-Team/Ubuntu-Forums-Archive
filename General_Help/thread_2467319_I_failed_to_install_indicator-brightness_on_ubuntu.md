---
title: "I failed to install indicator-brightness on ubuntu 20"
date: 2021-09-23
forum: General Help
---

### Post by mstdmstd on 2021-09-23
Hello,
I tried to install indicator-brightness, but got errors :
```
master@master-laptop:/mnt/_work_sdb8/wwwroot/lar/Hostels4J$ sudo add-apt-repository ppa:indicator-brightness/ppa
[sudo] password for master: 
 PPA for the indicator-brightness for the Unity panel.
 More info: https://launchpad.net/~indicator-brightness/+archive/ubuntu/ppa
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 http://ua.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://ua.archive.ubuntu.com/ubuntu focal-updates InRelease                                                                                                                                        
Hit:3 http://ua.archive.ubuntu.com/ubuntu focal-backports InRelease                                                                                                                                      
Hit:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                   
Hit:5 http://ppa.launchpad.net/giuspen/ppa/ubuntu focal InRelease                                                                                   
Hit:6 https://deb.nodesource.com/node_14.x focal InRelease                                                                    
Ign:7 http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu focal InRelease                        
Hit:8 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:9 http://ppa.launchpad.net/ondrej/php/ubuntu focal InRelease
Err:10 http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu focal Release
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
master@master-laptop:/mnt/_work_sdb8/wwwroot/lar/Hostels4J$  sudo apt-get update 
Hit:1 http://ua.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://ua.archive.ubuntu.com/ubuntu focal-updates InRelease                                                                                                              
Hit:3 http://ua.archive.ubuntu.com/ubuntu focal-backports InRelease                                                                                                            
Hit:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                   
Hit:5 http://ppa.launchpad.net/giuspen/ppa/ubuntu focal InRelease                                                                                   
Hit:6 https://deb.nodesource.com/node_14.x focal InRelease                                                                    
Ign:7 http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu focal InRelease                        
Hit:8 http://security.ubuntu.com/ubuntu focal-security InRelease         
Hit:9 http://ppa.launchpad.net/ondrej/php/ubuntu focal InRelease         
Err:10 http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu focal Release
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
master@master-laptop:/mnt/_work_sdb8/wwwroot/lar/Hostels4J$ sudo apt-get install indicator-brightness
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package indicator-brightness

```



Searching in next I found additive option :
> --allow-unauthenticated

but looks lokie this option does not work now ?


Which is good and safe way to inmstall indicator-brightness ?

Thanks!

---

### Post by grahammechanical on 2021-09-23
> The repository  'http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu focal Release'  does not have a Release file.

PPA = Personal Package Archive and they are hosted on the Canonical Launchpad.net server.

[https://launchpad.net/~indicator-brightness/+archive/ubuntu/ppa](https://launchpad.net/~indicator-brightness/+archive/ubuntu/ppa)

As  you can see from the indicator-brightness Launchpad page the developer  last provided a version of indication-brightness for Ubuntu 18.10. There  is not a version for Ubuntu 20.04. Each version of Ubuntu has its own  repositories. When you ran this command

```
sudo add-apt-repository ppa:indicator-brightness/ppa
```

you  created a source of software to a repository in the 20.04 set of  repositories but the developer has not put any indicator-brightness  software in the 20.04 set of repositories. And so you get that error  message.

Regards

---

### Post by mstdmstd on 2021-09-23
Thanks! Are there some different apps with similar functionality ?

---

### Post by mstdmstd on 2021-09-23
Also now I got error message updating system :


[FONT=monospace]> [COLOR=#54FF54]**master@master-laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**/mnt/_work_sdb8/wwwroot/lar/Hostels4J**[/COLOR][COLOR=#000000]$ sudo apt-get update[/COLOR]
[sudo] password for master:  
Hit:1 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) focal-updates InRelease                                                                                                                                                              
Hit:3 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) focal-backports InRelease                                                                                                                                                            
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                                                                  
Hit:5 [http://ppa.launchpad.net/giuspen/ppa/ubuntu](http://ppa.launchpad.net/giuspen/ppa/ubuntu) focal InRelease                                                                                                                                  
Hit:6 [https://deb.nodesource.com/node_14.x](https://deb.nodesource.com/node_14.x) focal InRelease                                                                                                                   
Hit:7 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                                                                                                      
Ign:8 [http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu](http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu) focal InRelease                                                                       
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Hit:10 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) focal InRelease
Err:11 [http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu](http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu) focal Release        
  404  Not Found [IP: 91.189.95.85 80]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [27,6 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 c-n-f Metadata [8&#8239;716 B]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [61,1 kB]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [2&#8239;468 B]
Reading package lists... Done      
E: The method driver /usr/lib/apt/methods/ppa could not be found.
N: Is the package apt-transport-ppa installed?
E: The repository 'http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


Which is valid way to clear my reps from [/FONT]indicator-brightness ref ?

---

### Post by deadflowr on 2021-09-23
Run
```
sudo add-apt-repository --remove ppa:indicator-brightness/ppa
```
as the PPA is now dead.
It also only worked for the old unity desktop which Ubuntu no longer uses.

As for anything that might work look at gnome shell extensions: [https://extensions.gnome.org/]("https://extensions.gnome.org/")
As this is for Ubuntu 20.04 look at something that has versions available for  3.36.
Gnome is temperamental so it requires the exact same version as what you have.

---

### Post by mstdmstd on 2021-09-23
I can not remove it :
```
master@master-laptop:/mnt/_work_sdb8/wwwroot/lar/Hostels4J$ sudo add-apt-repository --remove ppa:indicator-brightness/ppa
 PPA for the indicator-brightness for the Unity panel.
 More info: [https://launchpad.net/~indicator-brightness/+archive/ubuntu/ppa](https://launchpad.net/~indicator-brightness/+archive/ubuntu/ppa)
Press [ENTER] to continue or Ctrl-c to cancel removing it.

```
I Press ENTER:

```
master@master-laptop:/mnt/_work_sdb8/wwwroot/lar/Hostels4J$ sudo apt-get update
Hit:1 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) focal-updates InRelease                                                                                                                                                           
Hit:3 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) focal-backports InRelease                                                                                                                                                         
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                                                                
Hit:5 [http://ppa.launchpad.net/giuspen/ppa/ubuntu](http://ppa.launchpad.net/giuspen/ppa/ubuntu) focal InRelease                                                                                                                               
Hit:6 [https://deb.nodesource.com/node_14.x](https://deb.nodesource.com/node_14.x) focal InRelease                                                                                                                
Hit:7 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) focal InRelease                                                                                  
Hit:8 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                                                                    
Hit:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Reading package lists... Done
E: The method driver /usr/lib/apt/methods/ppa could not be found.
N: Is the package apt-transport-ppa installed?
E: Failed to fetch ppa://indicator-brightness/ppa/dists/master/InRelease  
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

?

---

### Post by mstdmstd on 2021-09-23
I use KDE, so I search some KDE app like [COLOR=#000000][FONT=&quot]indicator-brightnes...[/FONT][/COLOR]

---

### Post by deadflowr on 2021-09-24
The error shown is different from before.
There is no longer an Error in the output, but this line 
> E: Failed to fetch ppa://indicator-brightness/ppa/dists/master/InRelease  
is new. And it is not normal.
Did you try to add the ppa manually or something?

Also, it is best to post what you are running as it always to be assumed it's the default Ubuntu unless stated otherwise.

---

### Post by mstdmstd on 2021-09-24
I tried to add docker support with command :
```
sudo vi /etc/apt/sources.list.d/docker.list
```


New file docker.list was created.


I deleted it manually , but I still got errors :

```

[EMAIL="root@master-laptop:/etc/apt/sources.list"]root@master-laptop:/etc/apt/sources.list[/EMAIL].d# sudo add-apt-repository --remove ppa:indicator-brightnes
Cannot add PPA: 'ppa:~indicator-brightnes/ubuntu/ppa'.
ERROR: '~indicator-brightnes' user or team does not exist.
[EMAIL="root@master-laptop:/etc/apt/sources.list"]root@master-laptop:/etc/apt/sources.list[/EMAIL].d# sudo apt-get update
Hit:1 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) focal-updates InRelease                                                                                                                                                                            
Hit:3 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) focal-backports InRelease                                                                                                                                                                          
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                                                               
Hit:5 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                                                                                                                                               
Hit:6 [http://ppa.launchpad.net/giuspen/ppa/ubuntu](http://ppa.launchpad.net/giuspen/ppa/ubuntu) focal InRelease                                                                                   
Hit:7 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) focal InRelease                                                                                         
Hit:8 [https://deb.nodesource.com/node_14.x](https://deb.nodesource.com/node_14.x) focal InRelease          
Hit:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Reading package lists... Done
E: The method driver /usr/lib/apt/methods/ppa could not be found.
N: Is the package apt-transport-ppa installed?
E: Failed to fetch ppa://indicator-brightness/ppa/dists/master/InRelease  
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by deadflowr on 2021-09-24
Let's look at your sources.
Post back what
```
cat /etc/apt/sources.list
tail /etc/apt/sources.list.d/*
```
output.
Something in there is not right.

The current output shows it is no longer trying to connect to the indicator-brightness ppa as shown in the actual Hit/Err outputs.
So something else has happened.

---

