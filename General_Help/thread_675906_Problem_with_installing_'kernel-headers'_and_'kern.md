---
title: "Problem with installing 'kernel-headers' and 'kernel-source' packages"
date: 2008-01-23
forum: General Help
---

### Post by giuffsalvo on 2008-01-23
Hi, I have a problem with installing those two packages...Basicly, when I type
```

sudo apt-get install kernel-headers

```
or 
```

sudo apt-get-install kernel-source

```

APT answers me that the packages are references in the repositories, but not available...Looks like there isn't the URL from which download them...
The content of my /etc/apt/sources.list is

```

deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multive
rse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse r
estricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiver
se restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse res
tricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse
 restricted

```

I tried to install directly 'kernel-headers-$(uname -r)', but the problem persists...
Thanks a lot to anyone who will try to help, I need those packages to install VMware Workstation...

---

### Post by por100pre1 on 2008-01-23
Do these searches:

```
aptitude search linux-headers
```

```
aptitude search linux-source
```

Hope this helps. :)

---

### Post by giuffsalvo on 2008-01-23
I did them, but...

 - I was able to install only linux-source (by typing 'sudo aptitude install linux-source')
 - I tried to install linux-headers, by typing
```

sudo aptitude install linux-headers-$(uname -r)

```

But the system responded
```

Reading state information... Fatto               
Reading extended state information      
Initializing package states... Fatto
Building tag database... Fatto      
No candidate version found for linux-headers-2.6.20-16-generic
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Fatto
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
Reading extended state information      
Initializing package states... Fatto
Building tag database... Fatto 

```

I'm running kernel 2.6.20-16, but I have headers of 2.6.22-14 in /usr/src/linux-headers-2.6.22-14 and /usr/src/linux-headers-2.6.22-14-generic...

---

### Post by capink on 2008-01-23
Upgrade to the latest kernel and headers ( the older versions get deleted from the repositories ):

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install linux-headers-generic linux-source
```

---

