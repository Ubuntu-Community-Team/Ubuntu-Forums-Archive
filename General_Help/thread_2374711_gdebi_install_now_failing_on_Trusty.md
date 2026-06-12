---
title: "gdebi install now failing on Trusty"
date: 2017-10-18
forum: General Help
---

### Post by timtrs on 2017-10-18
Up until the end of September our scripts were working fine - though a little long winded.

```
  sudo apt-get install -y aptitude 
  sudo aptitude install -y gdebi
  wget http://www.princexml.com/download/prince_10r7-1_ubuntu14.04_amd64.deb
  sudo gdebi --non-interactive prince_10r7-1_ubuntu14.04_amd64.deb
``` 

Since October, the last command now fails because gdebi is not fully installing. Upon inspecting the console logs we see this key difference in the aptitude install of gdebi since October:

```
  Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main gdebi-core all 0.9.5.3ubuntu2
  404  Not Found [IP: 91.189.88.162 80]
``` 

It seems that the gdebi-core has fallen out of the trusty-updates repository!

My questions are:

i) Does anyone know who I speak to to get it re-instated?, or

ii) Does anyone know a better way to do an unattended install of a deb package not in the Ubuntu repositories, than going through the aptitude/gdebi route above (for info, we are stuck on Ubuntu 14.04)?

Thanks,

---

### Post by &amp;KyT$0P# on 2017-10-18
Just add
```
sudo apt-get update
```
at the top of your script.

> **timtrs said:**
> ii) Does anyone know a better way to do an unattended install of a deb package not in the Ubuntu repositories, than going through the aptitude/gdebi route above (for info, we are stuck on Ubuntu 14.04)?
Why do you need to use aptitude here?

Assuming you do need aptitude for other things, and assuming you want this script to install aptitude, I would write it like this -
```
  sudo apt-get update
  sudo apt-get install -y aptitude gdebi
  wget http://www.princexml.com/download/prince_10r7-1_ubuntu14.04_amd64.deb
  sudo gdebi --non-interactive prince_10r7-1_ubuntu14.04_amd64.deb
```

---

### Post by ian-weisser on 2017-10-18
1) > ```
  Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main gdebi-core all 0.9.5.3ubuntu2
  404  Not Found [IP: 91.189.88.162 80]
``` 

gdebi and gdebi-core are still there.
Your source URL is wrong.
Try opening it in a web browser, and you will see.


2) In the longer term, once you migrate to something newer than 14.04 you can simply do:

```
  wget http://url/package_name.deb
  sudo apt install -y /path/to/package_name.deb
``` 

Of course, it would work better (and safer) if the package were in the Debian/Ubuntu repositories instead of some website on the dirty, dirty internet.

---

### Post by deadflowr on 2017-10-18
> It seems that the gdebi-core has fallen out of the trusty-updates repository!

+1 to halogen2's post.
The version it's looking for it no longer viable.
the current version is
0.9.5.3ubuntu3
an apt-get update would have fixed that.

---

### Post by timtrs on 2017-10-24
Many thanks indeed to all you guys for your help.  
And sorry for not replying earlier - I don't seem to get email notifications of replies.

---

