---
title: "installing in terminal."
date: 2007-07-16
forum: General Help
---

### Post by sdmike on 2007-07-16
I only have access to the terminal in ubuntu and I need to install a program called wakeonlan. How do I go about downloading and installing this via the terminal.

This did not work: sudo apt-get install wakeonlan

So I guess I have to download it from there site here: [http://gsd.di.uminho.pt/jpo/software/wakeonlan/](http://gsd.di.uminho.pt/jpo/software/wakeonlan/)

But I have no idea how to download and install it.

---

### Post by pak33m on 2007-07-16
You could try using wget:

wget [http://gsd.di.uminho.pt/jpo/software/wakeonlan/downloads/wakeonlan-0.41.tar.gz](http://gsd.di.uminho.pt/jpo/software/wakeonlan/downloads/wakeonlan-0.41.tar.gz)

The you would have to install it from there:

3. Installation

Choose one of the following methods: 
Simply extract the Perl script wakeonlan from the archive file.
From version 0.40 onwards you can just follow standard CPAN procedures: 
tar zxvf wakeonlan-0.41.tar.gz
cd wakeonlan-0.41
cpansign -v (optional step; requires Module::Signature)
perl Makefile.PL
make
make install

---

### Post by sdmike on 2007-07-16
I got this error when I tried to download it.


PC:~/Desktop# wget [http://gsd.di.uminho.pt/jpo/software...an-0.41.tar.gz](http://gsd.di.uminho.pt/jpo/software...an-0.41.tar.gz)
--11:59:54--  [http://gsd.di.uminho.pt/jpo/software...an-0.41.tar.gz](http://gsd.di.uminho.pt/jpo/software...an-0.41.tar.gz)
           => `software...an-0.41.tar.gz'
Resolving gsd.di.uminho.pt... 193.136.19.96
Connecting to gsd.di.uminho.pt|193.136.19.96|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:59:56 ERROR 404: Not Found.

---

### Post by aysiu on 2007-07-16
Are you connected to the internet?

The .deb is probably easier to install than the .tar.gz: ```
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/w/wakeonlan/wakeonlan_0.41-9_all.deb
sudo dpkg -i wakeonlan_0.41-9_all.deb
```

---

### Post by sdmike on 2007-07-16
Yes I am.

I think I might need a key for that download.

Then again I don't know how to add keys.

:(

---

### Post by pak33m on 2007-07-16
sudo apt-key add <key>

---

### Post by alftoo on 2007-07-16
wget [http://gsd.di.uminho.pt/jpo/software/RPMS/jpo.gpgkey.asc](http://gsd.di.uminho.pt/jpo/software/RPMS/jpo.gpgkey.asc) -O- | sudo apt-key add -
wget [http://gsd.di.uminho.pt/jpo/software/wakeonlan/downloads/wakeonlan-0.41.tar.gz](http://gsd.di.uminho.pt/jpo/software/wakeonlan/downloads/wakeonlan-0.41.tar.gz)

---

### Post by sdmike on 2007-07-16
So should it look like this:

wget [http://gsd.di.uminho.pt/jpo/software...jpo.gpgkey.asc](http://gsd.di.uminho.pt/jpo/software...jpo.gpgkey.asc) -O- | sudo apt-key - add F9B6 8D87 859D 1C94 48F0 84C0 9749 9EB5 91BD 851B

because I'm still getting a 404 error.

and I trust me it is hooked up to the internet.

---

### Post by sdmike on 2007-07-16
> **aysiu said:**
> Are you connected to the internet?

The .deb is probably easier to install than the .tar.gz: ```
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/w/wakeonlan/wakeonlan_0.41-9_all.deb
sudo dpkg -i wakeonlan_0.41-9_all.deb
```

I was able to download the .deb file above but then again how do I extract and install it?

---

### Post by sdmike on 2007-07-16
Does this mean it installed it or extracted it:

root@Bob:~/Desktop# dpkg -i /home/Bob/Desktop/wakeonlan_0.41-9_all.deb
Selecting previously deselected package wakeonlan.
(Reading database ... 106694 files and directories currently installed.)
Unpacking wakeonlan (from .../wakeonlan_0.41-9_all.deb) ...
Setting up wakeonlan (0.41-9) ...

?????????

---

### Post by rklauco on 2007-07-16
> **sdmike said:**
> Does this mean it installed it or extracted it:

root@Bob:~/Desktop# dpkg -i /home/Bob/Desktop/wakeonlan_0.41-9_all.deb
Selecting previously deselected package wakeonlan.
(Reading database ... 106694 files and directories currently installed.)
Unpacking wakeonlan (from .../wakeonlan_0.41-9_all.deb) ...
Setting up wakeonlan (0.41-9) ...

?????????

It is already installed, the second row did the job.

By the way, your 404 problem was caused by the forum. It shortens the URL, so instead of some long URL it enters dots (...) and you can click on that url and it will work. But, if you copy-paste the shorten version, it will not.
You should right click the link and select copy link location.
And than paste it to the terminal.
Otherwise you are trying to download from wrong link.

---

### Post by pak33m on 2007-07-16
sdmike,

I believe you can check the installation in the database with dpkg -s | --status <package-name>

---

