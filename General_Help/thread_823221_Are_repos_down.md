---
title: "Are repos down?"
date: 2008-06-09
forum: General Help
---

### Post by uberlube on 2008-06-09
ARe some of the repos down? I just installed hardy and I cant get anything useful installed. Here is the output of update:

```
manaburn@manaburn:~$ sudo apt-get update
Ign http://ca.archive.ubuntu.com hardy Release.gpg
Ign http://ca.archive.ubuntu.com hardy/main Translation-en_CA       
Hit http://archive.canonical.com hardy Release.gpg                  
Ign http://archive.canonical.com hardy/partner Translation-en_CA     
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_CA 
Ign http://ca.archive.ubuntu.com hardy/restricted Translation-en_CA  
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA    
Ign http://ca.archive.ubuntu.com hardy/multiverse Translation-en_CA  
Ign http://ca.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://ca.archive.ubuntu.com hardy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy Release                       
Ign http://ca.archive.ubuntu.com hardy-updates Release               
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_CA
Ign http://security.ubuntu.com hardy-security/universe Translation-en_CA
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com hardy-security Release                
Hit http://archive.canonical.com hardy Release                       
Ign http://ca.archive.ubuntu.com hardy/main Packages               
Ign http://ca.archive.ubuntu.com hardy/restricted Packages           
Ign http://ca.archive.ubuntu.com hardy/main Sources                  
Ign http://ca.archive.ubuntu.com hardy/restricted Sources            
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://archive.canonical.com hardy/partner Packages              
Ign http://ca.archive.ubuntu.com hardy/universe Packages
Ign http://ca.archive.ubuntu.com hardy/universe Sources
Ign http://ca.archive.ubuntu.com hardy/multiverse Packages
Ign http://ca.archive.ubuntu.com hardy/multiverse Sources
Ign http://ca.archive.ubuntu.com hardy-updates/main Packages         
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Packages   
Ign http://ca.archive.ubuntu.com hardy-updates/main Sources          
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Sources    
Ign http://ca.archive.ubuntu.com hardy-updates/universe Packages     
Ign http://ca.archive.ubuntu.com hardy-updates/universe Sources      
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Packages   
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Sources    
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://archive.canonical.com hardy/partner Sources               
Err http://ca.archive.ubuntu.com hardy/main Packages                 
  404 Not Found
Err http://ca.archive.ubuntu.com hardy/restricted Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy/main Sources
  404 Not Found
Err http://ca.archive.ubuntu.com hardy/restricted Sources
  404 Not Found
Err http://ca.archive.ubuntu.com hardy/universe Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy/universe Sources
  404 Not Found
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Err http://ca.archive.ubuntu.com hardy/multiverse Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy/multiverse Sources
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/main Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/restricted Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/main Sources
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/restricted Sources
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/universe Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/universe Sources
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/multiverse Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/multiverse Sources
  404 Not Found
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by uberlube on 2008-06-09
Switch from Canadian server to main server and its working now. Thank God.

---

### Post by ThreeLies on 2008-06-09
Some mirrors can come and go but they usually have quite good uptimes hence why they are official mirrors.

You may be interested in this page for mirror status.. [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by Fraoch on 2008-06-09
It's easy to do this in the Synaptic GUI, but I'm using a command line over SSH. (Long story)

Is there any way to change this over CLI?  Do I have to manually edit /etc/apt/sources.list, putting the main repo URLs in here?

---

### Post by kpkeerthi on 2008-06-09
Change ```
http://ca.archive.ubuntu.com
``` to ```
http://archive.ubuntu.com
``` in the source.list file.

---

### Post by Fraoch on 2008-06-09
Awesome, that was really easy.  Thank you.

---

