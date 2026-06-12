---
title: "apt-get update fails for restricted and universe repositories but works for main"
date: 2018-02-19
forum: General Help
---

### Post by amukher on 2018-02-19
I am using Ubuntu 14.04 LTS Trusty Tahr.
When I try to update by doing sudo apt-get update, I get the following error
```
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages 
Fetched 310 kB in 4s (75.2 kB/s)                              
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
Here is my sources.list file:
```
###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted universe

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe

###### Ubuntu Security Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe
```

I have done the following to solve the problem
```
sudo rm -vfr /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
```

However, it does not solve the problem. But, if I remove restricted and universe and only leave main in sources.list, then there is no error. I have also tried with the India mirror, but I get the same error.

Could someone please help me.

---

### Post by wildmanne39 on 2018-02-19
*Thread moved to **General Help, a more appropriate forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use normal fonts unless drawing attention to a specific line of text.

---

