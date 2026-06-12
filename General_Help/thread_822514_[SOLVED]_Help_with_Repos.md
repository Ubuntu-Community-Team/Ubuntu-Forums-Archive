---
title: "[SOLVED] Help with Repos"
date: 2008-06-08
forum: General Help
---

### Post by Patrick793 on 2008-06-08
Hello. I'm using Ubuntu 8.04 on my Eee PC 2G surf. Ubuntu is on a 250GB External Hard drive, and everything was going smoothly. Until today, that is.

I tried installing a java plugin from firefox, and I got an error saying that it couldn't find the file to download, so I ran sudo apt-get update, and here was the outcome.

```
patrick@patrick-laptop:~$ sudo apt-get update
Ign http://ca.archive.ubuntu.com hardy Release.gpg
Ign http://ca.archive.ubuntu.com hardy/main Translation-en_CA       
Ign http://ca.archive.ubuntu.com hardy/restricted Translation-en_CA 
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA   
Ign http://ca.archive.ubuntu.com hardy/multiverse Translation-en_CA 
Ign http://ca.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://ca.archive.ubuntu.com hardy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_CA 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com hardy Release                       
Hit http://archive.canonical.com hardy Release.gpg                   
Ign http://archive.canonical.com hardy/partner Translation-en_CA     
Ign http://ca.archive.ubuntu.com hardy-updates Release               
Ign http://ca.archive.ubuntu.com hardy/main Packages
Ign http://ca.archive.ubuntu.com hardy/restricted Packages           
Ign http://ca.archive.ubuntu.com hardy/universe Packages             
Ign http://ca.archive.ubuntu.com hardy/multiverse Packages           
Ign http://security.ubuntu.com hardy-security/universe Translation-en_CA
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com hardy-security Release                
Ign http://ca.archive.ubuntu.com hardy-updates/main Packages         
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Packages
Ign http://ca.archive.ubuntu.com hardy-updates/universe Packages
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://archive.canonical.com hardy Release                      
Err http://ca.archive.ubuntu.com hardy/main Packages                
  404 Not Found
Err http://ca.archive.ubuntu.com hardy/restricted Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy/universe Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy/multiverse Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/main Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/restricted Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/universe Packages
  404 Not Found
Err http://ca.archive.ubuntu.com hardy-updates/multiverse Packages
  404 Not Found
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://archive.canonical.com hardy/partner Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.canonical.com hardy/partner Sources
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
patrick@patrick-laptop:~$ 

```

I haven't tried anything on my Desktop yet. So, I don't know if it's something I did, or if it's everywhere. It was working perfectly yesterday, so I don't know what happened. How can I fix this?

Thanks!

---

### Post by Patrick793 on 2008-06-08
Please help me!

---

### Post by Nepherte on 2008-06-08
A 404 error means that the files were not found on the server. This is a mirror server related issue. Change your mirror and try again.

---

### Post by drs305 on 2008-06-08
> **Nepherte said:**
> A 404 error means that the files were not found on the server. This is a mirror server related issue. Change your mirror and try again.

In synaptic, try Settings > Repositories, Download from: > Other, Select Best Server. Choose Server, Close. After doing this try running your commands again.

---

### Post by mikewhatever on 2008-06-08
You seem to be not the only one: [http://ubuntuforums.org/showthread.php?t=822656](http://ubuntuforums.org/showthread.php?t=822656). Try using another server.

---

### Post by Patrick793 on 2008-06-08
Thanks! It works now!

---

