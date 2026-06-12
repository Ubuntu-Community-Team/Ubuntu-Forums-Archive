---
title: "Problem updating repositories in 16.04"
date: 2017-07-06
forum: General Help
---

### Post by checoimg on 2017-07-06
I tried to update and I feared an error before doing ```
apt-get upgrade 
```


This if from the Dominican Repubic server
Errors:
```
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:4 http://do.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:6 http://do.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:7 http://repository.spotify.com stable InRelease                           
Get:8 http://do.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:9 http://do.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [572 kB]
Err:9 http://do.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
  Hash Sum mismatch
Get:11 http://do.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [493 kB]
Get:12 http://do.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [474 kB]
Fetched 878 kB in 2s (365 kB/s)     
Reading package lists... Done
E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-amd64/by-hash/SHA256/592cfced5172bd5f68af115e45b54a1384339de16e17ba6e17c04215d1b23979  Hash Sum mismatch
E: Failed to fetch http://do.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-i386/by-hash/SHA256/cce8828c92c8850e8fa2fbc622b3d4fda81f2a890f7de54f5257bd48707578d7  
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

This what I got by checking the sha256sum on the files
```

sha256sum 592cfced5172bd5f68af115e45b54a1384339de16e17ba6e17c04215d1b23979 
1448fe8b9d3873d74daaf3cc07c7cba79c32d7b22a0a085b22c03f3a8e19333a  592cfced5172bd5f68af115e45b54a1384339de16e17ba6e17c04215d1b23979

sha256sum cce8828c92c8850e8fa2fbc622b3d4fda81f2a890f7de54f5257bd48707578d7 
3251739d080d5bc0fa9f0d4fd8025c185bfa386996a6206b756d72ff3647a6ec  cce8828c92c8850e8fa2fbc622b3d4fda81f2a890f7de54f5257bd48707578d7
```

From md5sums I get that this should be it's sum **2ec7efbe6fb07154aa1d1028d838941d  indices/md5sums.gz**[URL="http://do.archive.ubuntu.com/ubuntu/indices/md5sums.gz"]

[/URL]But it is [B]d98904176d81d7dcdacddaa3fe3fc370  md5sums

[/B]Finally I found that changing the server to the main server in software sources fixed my problem.```
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release     
Hit:3 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]       
Hit:6 http://repository.spotify.com stable InRelease    
Get:7 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Fetched 306 kB in 1s (210 kB/s)   
Reading package lists... Done
```

---

### Post by deadflowr on 2017-07-06
> Finally I found that changing the server to the main server in software sources fixed my problem.
So, solved?

---

