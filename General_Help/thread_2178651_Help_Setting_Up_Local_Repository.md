---
title: "Help Setting Up Local Repository"
date: 2013-10-04
forum: General Help
---

### Post by sunveer on 2013-10-04
I have setup a local repository for LAN using vsftpd server at /srv/ftp/pub/packages.

I have created Packages and Packages.gz in /srv/ftp/pub/packages and and also created Release (with hash of Packages and Packages.gz) and Release.gpg.

The problem is that whenever, I try to use  "deb file:/srv/ftp/pub  packages/"  then, I am successfully able to install packages using apt-get install but when I use "deb [ftp://localhost/pub](ftp://localhost/pub)  packages/", I get the following error with  $sudo apt-get update

```
Get:1 ftp://localhost packages/ Release.gpg [490 B]
Get:2 ftp://localhost packages/ Release [227 B]
Get:3 ftp://localhost packages/ Packages [11.1 kB]
Get:4 ftp://localhost packages/ Translation-en_US
Get:5 ftp://localhost packages/ Translation-en      
Get:6 ftp://localhost packages/ Translation-en_US   
Get:7 ftp://localhost packages/ Translation-en      
Get:8 ftp://localhost packages/ Translation-en_US    
Get:9 ftp://localhost packages/ Translation-en
Get:10 ftp://localhost packages/ Translation-en_US
Get:11 ftp://localhost packages/ Translation-en
Get:12 ftp://localhost packages/ Translation-en_US
Ign ftp://localhost packages/ Translation-en_US
Get:13 ftp://localhost packages/ Translation-en
Ign ftp://localhost packages/ Translation-en
Fetched 11.8 kB in 0s (81.2 kB/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/localhost_pub_packages_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

I have tried to remove all files from /var/lib/apt/lists/ and then updating again, but the same results appear.

---

