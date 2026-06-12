---
title: "Download Package Issue"
date: 2007-02-05
forum: General Help
---

### Post by voltage on 2007-02-05
Hi,

    As we know the command #sudo apt-get update is to retrieve the current list of package from all server while connected to internet, then doing #sudo apt-get install ***package***. 

    But due to those are facing difficulty connecting to internet to download the current list of package from all server, so what should they do ? Do anyway to download (could you please tell us where is the URL) from other pc, then burn to the cd. After that would execute which command to doing the update / install like #sudo apt-get update and #sudo apt-get install ***package***. 

Please Advice.
Thanks.
Rg,
Frank Ong

---

### Post by taurus on 2007-02-05
Look here and download whatever you need from another computer.  Then, transfer them to yours and install them with 

```
sudo dpkg -i *.deb
```

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by voltage on 2007-02-05
> **taurus said:**
> Look here and download whatever you need from another computer.  Then, transfer them to yours and install them with 

```
sudo dpkg -i *.deb
```

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Hi,

I have go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/). That have soo many of package. So may I know how do download on it .. ?? because I were unable to get it..:confused:

---

### Post by taurus on 2007-02-05
You need to know what you want to install and the package will tell you what else does it need, dependencies.  Of course, you have to know whether you have breezy, dapper, or edgy.

---

### Post by voltage on 2007-02-05
> **taurus said:**
> You need to know what you want to install and the package will tell you what else does it need, dependencies.  Of course, you have to know whether you have breezy, dapper, or edgy.

ok .. currently I migth need to run #sudo apt-get install build-essentials, so may I know which package I need ? Then currently I'm using Ubuntu 6.10.

Thanks..

---

### Post by taurus on 2007-02-05
If you have the install CD, build-essential is already on the CD.

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by voltage on 2007-02-10
> **taurus said:**
> If you have the install CD, build-essential is already on the CD.

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

Hi,

 due to the require package for build-essential, I have complete download ... but I have facing the error below .. 

 [I][B][COLOR="Green"]   dpkg : dependency problems prevent configuration of build-essential :
      build-essential depends on g++ (>=4:4.1.1); however :
        package g++ is not configured yet.[/COLOR][/B][/I]

[COLOR="Red"]***P/S : I have try to install the g++-4.1_4.1.1-13ubuntu5_i386.deb and g++_4.1.1-6ubuntu3_i386.deb. But still not work.***[/COLOR]

Please Advice .. Thanks

---

### Post by Bleky on 2007-03-25
Helou to everyone!
I'm new in Ubuntu so i have this question:

I have 6 PC at home and I planing to muve to one simple OS
4 of this PC it's an old P2-P3 PC
on this 4 i planing to install xubuntu, but i interested how to upgrade all 4
i have adsl but it's possible to upgrade only one PC then downloaded files burn to a CD then upgrade other's pc from CD?

---

