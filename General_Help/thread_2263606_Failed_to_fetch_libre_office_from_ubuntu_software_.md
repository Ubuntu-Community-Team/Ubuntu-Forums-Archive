---
title: "Failed to fetch libre office from ubuntu software center"
date: 2015-02-02
forum: General Help
---

### Post by matt18 on 2015-02-02
Ello all. I finished installing xubuntu in vmplayer and now i am testing it out by installing some basic software. So far i have run into this issue twice. Once with libreoffice and the other with sweet home 3d.

With libre office it will get about half way and then throw an error message saying:

Failed to download package files
Check your internet connection.

Under the details tab:
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre-headless_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre-headless_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb) 404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb) 404  Not Found [IP: 91.189.91.13 80]

Same with sweethome 3d from software center.

Internet works or i wouldnt be able to post this forum thread haha.

Was Xubuntu released with wrong repos in it?

thanks

---

### Post by deadflowr on 2015-02-02
You've installed, but have you run a system update yet?
Open the Update Manager, or what ever it's called on Xubuntu, and install the updates.

Then try to install those packages.
A normal behavior when things don't install is to check that the system is up-to-date.

See if that helps.

---

### Post by ibjsb4 on 2015-02-02
I am not finding any .deb file.

[http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/)

Did you install from the software center?

---

### Post by ian-weisser on 2015-02-02
> **matt18 said:**
> Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre-headless_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre-headless_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb) 404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb) 404  Not Found [IP: 91.189.91.13 80]

Your system is telling you the truth.
```
$ rmadison -u ubuntu openjdk-7-jre-headless
[...]
 openjdk-7-jre-headless | 7u71-2.5.3-0ubuntu0.12.04.1 | precise-security/universe | amd64, armel, armhf, i386, powerpc
[...]
```

You are trying to download 7u71-2.5.3-0ubuntu0.**14**.04.1, while the Ubuntu repos have 7u71-2.5.3-0ubuntu0.**12**.04.1 (which is indeed appropriate for a 12.04 system)

Try the following command to find out where that request is coming from. Please post the entire output here.
```
apt-cache policy openjdk-7-jre-headless
```

---

### Post by matt18 on 2015-02-03
I am trying this from the software center. i have not added any repos or anything of the sorts. 

it just starts to download and then says failed. haha. 

I have not installed libreoffice or sweethome 3d yet because it wont let me. this is a new install of xubuntu 14.04 not 12.04

---

### Post by matt18 on 2015-02-03
> **ian-weisser said:**
> Your system is telling you the truth.
```
$ rmadison -u ubuntu openjdk-7-jre-headless
[...]
 openjdk-7-jre-headless | 7u71-2.5.3-0ubuntu0.12.04.1 | precise-security/universe | amd64, armel, armhf, i386, powerpc
[...]
```

You are trying to download 7u71-2.5.3-0ubuntu0.**14**.04.1, while the Ubuntu repos have 7u71-2.5.3-0ubuntu0.**12**.04.1 (which is indeed appropriate for a 12.04 system)

Try the following command to find out where that request is coming from. Please post the entire output here.
```
apt-cache policy openjdk-7-jre-headless
```

here is the output of the requested command:

matt@ubuntu:~$ apt-cache policy openjdk-7-jre-headless
openjdk-7-jre-headless:
  Installed: (none)
  Candidate: 7u71-2.5.3-0ubuntu0.14.04.1
  Version table:
     7u71-2.5.3-0ubuntu0.14.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages
     7u51-2.4.6-1ubuntu4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
matt@ubuntu:~$ 

It still fails to download and install libre office and some other packages via software center in version 14.04.

---

### Post by matt18 on 2015-02-03
I just tried to update the system using software updater and it says exact same error. How can they claim it to be stable whne it cant even download updates normally? haha. It is ubuntu lts 14.04 running xfce environment. haha it is a fresh install and im just trying to get this to work for some basic users. haha

---

### Post by deadflowr on 2015-02-03
Post the output of 
```
sudo apt-get update
```

use code tags, please.

[s]Then re-run the 
apt-cache policy openjdk-7-jre-headless command
Post that as well.[/s]

Ignore the second command for now, and only post the output for the first.

You posted again before I posted, just barely.

---

### Post by matt18 on 2015-02-03
```
matt@ubuntu:~$ sudo apt-get update
[sudo] password for matt: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [62.0 kB]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                          
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [64.8 kB]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [62.0 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources              
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [2,061 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [17.5 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [1,915 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [190 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [160 kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [2,061 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [99.6 kB]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [85.2 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [4,464 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [401 kB] 
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,629 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [101 kB] 
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [1,580 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [46.8 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [8,846 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [243 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [11.3 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [196 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [5,508 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [125 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 1,907 kB in 23s (81.6 kB/s)                                            
Reading package lists... Done
matt@ubuntu:~$ 
```



it looks normal. i checked software updater and even though it failed last time, the amount of MB in size for download size has dropped from 204MB to 48MB. Now when i hit update, it says failed cant fetch. So it seems its either the repo for the firefox or the base. haha

---

### Post by deadflowr on 2015-02-03
What is it saying it's failing to fetch?

---

### Post by matt18 on 2015-02-03
Failed to fetch [http://security.ubuntu.com/ubuntu/po....04.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre-headless_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb") 404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/po....04.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-7/openjdk-7-jre_7u71-2.5.3-0ubuntu0.14.04.1_i386.deb") 404  Not Found [IP: 91.189.91.13 80]

that is the output from ubuntu software center when i click install for libreoffice and other programs. some install some dont..

i try to use updater and it says samething when trying to download the recommended updates

---

### Post by deadflowr on 2015-02-03
After the apt-get update command, does the apt-cache policy openjdk-7-jre-headless, still show the EXACT same info as before.
Or does it look like this
```
openjdk-7-jre-headless:  
  Installed: (none)
  Candidate: 7u75-2.5.4-1~trusty1
  Version table:
     7u75-2.5.4-1~trusty1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     7u51-2.4.6-1ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages



```

Notice the new candidate.

---

### Post by ian-weisser on 2015-02-03
Fascinating.
Looking at the second URL...

openjdk-7-jre_7u**71-2.5.3-0ubuntu0.14.04.1**_i386.deb in the url. That version was superseded on Jan 27, 2015.
7u**75-2.5.4-1~trusty1** is what is actually in the repositories right now.

Were I suffering from this problem, I would stop using three different methods of installing and updating (apt-get, software updater, software center) until this is sorted. I would stick to one (apt-get) for a couple days to see if I can get the problem to recur. I think apt-get has the most useful error messages.

Six or seven days past...and an apt-get update since.... I wonder if this is a bug caused by phased updates?

---

