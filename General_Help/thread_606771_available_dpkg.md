---
title: "available dpkg"
date: 2007-11-08
forum: General Help
---

### Post by weasel7711 on 2007-11-08
I had to hard powerdown during an update because the computer locked up and now when i try to update or install anything it says
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

So i typed in "sudo dpkg --configure -a" into the terminal and it said something about files having parse errors, so I removed those files, then it had an issue with available, so i removed that per advice of another thread and it recreated itself as i expected
NOW it says when I try to update:

```
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory

```

and also
```

E: /var/cache/apt/archives/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb: files list file for package `libmagick9' is missing final newline
```

what do i do?

---

### Post by p_quarles on 2007-11-08
So you deleted /var/lib/dpkg/available? That's unfortunate, since the parsing errors are usually easy to fix. Anyway, in the future, never *delete* a config file: it's much safer to rename it as a backup file, like so:
```
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.bak
```

</lecture>

Anyway, I just spent a few minutes recreating this problem in a virtual machine, and I found a way to fix it at least temporarily. After I ran the following two commands:
```
sudo touch /var/lib/dpkg/available
sudo apt-get update[/code
```
I was then able to run 
```
sudo apt-get upgrade
```
without any problems. 

That said, I obviously wasn't able to test how this fix would work over the long term, so I don't know what to expect with regard to that. In any case, give that a try, and let us know how it goes.

---

### Post by weasel7711 on 2007-11-08
I did what you said and this is what I got:
```

mvanella@mvanella-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bsdutils cupsys cupsys-bsd cupsys-client cupsys-common firefox
  firefox-gnome-support hpijs hplip hplip-data libcupsimage2 libcupsys2
  libmysqlclient15off libnspr4 libnss3 libpng12-0 libssl0.9.8 mount
  mysql-common openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-math openoffice.org-style-human
  openoffice.org-writer openssl python-uno tzdata util-linux
  util-linux-locales
37 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/97.6MB of archives.
After unpacking 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb (--unpack):
 files list file for package `libmagick9' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by p_quarles on 2007-11-08
What does it say when you run this?:
```
sudo apt-get check
```

---

### Post by weasel7711 on 2007-11-08
```
mvanella@mvanella-desktop:~$ sudo apt-get check
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

### Post by p_quarles on 2007-11-08
Okay, that didn't find any errors. My next suggestion would be to go ahead and *atttempt* to fix the broken package anyway:
```
sudo apt-get -f install
```
The apt-get update/upgrade to see if it worked. 

If that fails, try this:
1) Move and rename the offending file:
```
sudo mv /var/cache/apt/archives/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb /var/cache/apt/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb.bak
```
Then, download the package manually from this link: [http://packages.ubuntu.com/feisty/editors/openoffice.org-style-human](http://packages.ubuntu.com/feisty/editors/openoffice.org-style-human)

Now move this new from whatever directory you downloaded it from to where it needs to be:
```
sudo mv openoffice.org-style-human_2.2.0-1ubuntu5_all.deb /var/cache/apt/archives
```
Then, run the update/upgrade cycle again, and cross your fingers. :)

---

### Post by weasel7711 on 2007-11-08
I downloaded the file (about 200 megs) and extracted it but aside from searching each folder seperately, how do I find that file you are talking about?

---

### Post by p_quarles on 2007-11-08
I'm not sure I understand. You don't need to extract the file, you just need to save it in your download directory, go to that directory, and then run the third terminal command I mentioned in my last message.

---

### Post by weasel7711 on 2007-11-09
I saved the compressed file to the desktop so was this what i was supposed to do?
openoffice.org_2.2.0.orig.tar.gz is the file you told me to download

```
mvanella@mvanella-desktop:~$ sudo mv /home/mvanella/Desktop/openoffice.org_2.2.0.orig.tar.gz/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb /var/cache/apt/archives
Password:
mv: cannot stat `/home/mvanella/Desktop/openoffice.org_2.2.0.orig.tar.gz/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb': Not a directory

```

---

### Post by p_quarles on 2007-11-09
I think you downloaded the wrong file. From the looks of it, you got the source code rather than the binary package. 

Anyway, here's what to do:
First open a terminal. and then paste this:
```
wget http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb

```After the file is finished downloading, type or paste this:
```
sudo mv openoffice.org-style-human_2.2.0-1ubuntu5_all.deb /var/cache/apt/archives
```And lastly:
```
sudo apt-get update && sudo apt-get upgrade
```
Post the errors you get from any of these commands here.

---

### Post by weasel7711 on 2007-11-09
It did a lot more extracting/installing this time before an error but this is the error I recieved:
```

mvanella@mvanella-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bsdutils cupsys cupsys-bsd cupsys-client cupsys-common firefox
  firefox-gnome-support hpijs hplip hplip-data libcupsimage2 libcupsys2
  libmysqlclient15off libnspr4 libnss3 libpng12-0 libssl0.9.8 mount
  mysql-common openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-math openoffice.org-style-human
  openoffice.org-writer openssl python-uno tzdata util-linux
  util-linux-locales
37 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 18.0MB/97.6MB of archives.
After unpacking 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com feisty-updates/main openoffice.org-calc 2.2.0-1ubuntu5 [5062kB]
Get:2 http://us.archive.ubuntu.com feisty-updates/main python-uno 2.2.0-1ubuntu5 [120kB]
Get:3 http://us.archive.ubuntu.com feisty-updates/main openoffice.org-writer 2.2.0-1ubuntu5 [5714kB]
Get:4 http://us.archive.ubuntu.com feisty-updates/main openoffice.org-impress 2.2.0-1ubuntu5 [653kB]
Get:5 http://us.archive.ubuntu.com feisty-updates/main openoffice.org-draw 2.2.0-1ubuntu5 [2312kB]
Get:6 http://us.archive.ubuntu.com feisty-updates/main openoffice.org-base 2.2.0-1ubuntu5 [3495kB]
Get:7 http://us.archive.ubuntu.com feisty-updates/main openoffice.org-gtk 2.2.0-1ubuntu5 [214kB]
Get:8 http://us.archive.ubuntu.com feisty-updates/main openoffice.org-gnome 2.2.0-1ubuntu5 [56.5kB]
Get:9 http://us.archive.ubuntu.com feisty-updates/main openoffice.org-evolution 2.2.0-1ubuntu5 [87.7kB]
Get:10 http://us.archive.ubuntu.com feisty-updates/main openoffice.org-math 2.2.0-1ubuntu5 [299kB]
Get:11 http://us.archive.ubuntu.com feisty-updates/main openoffice.org 2.2.0-1ubuntu5 [3092B]
Fetched 18.0MB in 24s (730kB/s)                                                
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb (--unpack):
 files list file for package `libmagick9' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-style-human_2.2.0-1ubuntu5_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by weasel7711 on 2007-11-09
bump

---

### Post by weasel7711 on 2007-11-10
I just tried to install opera and I got a similar error
```

.
```

---

