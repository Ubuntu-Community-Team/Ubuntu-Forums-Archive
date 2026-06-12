---
title: "Cannot install packages in Lubuntu 12.04"
date: 2014-07-27
forum: General Help
---

### Post by AAEIV on 2014-07-27
[COLOR=#333333][FONT=UbuntuRegular]I've just installed lubuntu 12.04 on an Acer aspire one netbook. I've noticed that although chromium-browser is installed, it doesn't come with a flash-player. I tried to install it using[/FONT][/COLOR]
```
sudo apt-get install flashplugin-installer
```[COLOR=#333333][FONT=UbuntuRegular]but I get the error[/FONT][/COLOR]
```
E: Unable to locate package flashplugin-installer
```[COLOR=#333333][FONT=UbuntuRegular]I also tried to install some other basic packages like gedit, deluge, kate, geany but I get the same error. Then I tried to update all repositories using[/FONT][/COLOR]
```
sudo apt-get update && sudo apt-get upgrade
```[COLOR=#333333][FONT=UbuntuRegular]but while it's running there are some errors like[/FONT][/COLOR]
```
Err http://gr.archive.ubuntu.com quantal-updates/main Sources
404  Not Found
```[COLOR=#333333][FONT=UbuntuRegular]or[/FONT][/COLOR]
```
W: Failed to fetch     http://gr.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources  404  Not Found[COLOR=#333333][FONT=UbuntuRegular]
```
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
Why is this happening? I've checked my internet connection and it's fine. I also tried to install chromeusing GDebi package installer` but I get an error[/FONT][/COLOR]
```
[FONT=Ubuntu Mono]Dependency is not satisfiable : libnns3(>=3.14.3)[/FONT]
```
[COLOR=#333333][FONT=UbuntuRegular]
I believe that somehow I cannot see the repositories. What can I do to fix this?[/FONT][/COLOR]

---

### Post by westie457 on 2014-07-27
Lubuntu 12.04 is no longer supported, It went EOL around October 2013.

Suggest you go for Lubuntu 14.04 LTS, this is supported for at least 2 years.
It may even be supported for 5 years in line with the other *buntu distros.

Edit.
Just checked here [http://lubuntu.net/](http://lubuntu.net/) 1404 is supported for 3 years.

---

### Post by bapoumba on 2014-07-27
@westie457 ?? 
AAEIV : you said you installed, did you fresh install from a downloaded DVD or did you release upgrade ?
I think you upgraded because you have quantal repositories. Please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by AAEIV on 2014-07-27
> **westie457 said:**
> Lubuntu 12.04 is no longer supported, It went EOL around October 2013.

Suggest you go for Lubuntu 14.04 LTS, this is supported for at least 2 years.
It may even be supported for 5 years in line with the other *buntu distros.

Edit.
Just checked here [http://lubuntu.net/](http://lubuntu.net/) 1404 is supported for 3 years.

The thing is that will it run on my low spec netbook? It has 1gb of RAM and an atom 1.3GHz cpu...

---

### Post by AAEIV on 2014-07-27
> **bapoumba said:**
> @westie457 ?? 
AAEIV : you said you installed, did you fresh install from a downloaded DVD or did you release upgrade ?
I think you upgraded because you have quantal repositories.

I didn't upgrade. I've installed it from a live usb, that I downloaded from lubuntu's website...

```
cat -n /etc/apt/sources.list

     1	# deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ quantal main multiverse restricted universe
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://archive.ubuntu.com/ubuntu quantal main restricted
     6	deb-src http://archive.ubuntu.com/ubuntu quantal main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://archive.ubuntu.com/ubuntu quantal-updates main restricted
    11	deb-src http://archive.ubuntu.com/ubuntu quantal-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://archive.ubuntu.com/ubuntu quantal universe
    17	deb-src http://archive.ubuntu.com/ubuntu quantal universe
    18	deb http://archive.ubuntu.com/ubuntu quantal-updates universe
    19	deb-src http://archive.ubuntu.com/ubuntu quantal-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://archive.ubuntu.com/ubuntu quantal multiverse
    27	deb-src http://archive.ubuntu.com/ubuntu quantal multiverse
    28	deb http://archive.ubuntu.com/ubuntu quantal-updates multiverse
    29	deb-src http://archive.ubuntu.com/ubuntu quantal-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://archive.ubuntu.com/ubuntu quantal-backports main restricted universe multiverse
    37	deb-src http://archive.ubuntu.com/ubuntu quantal-backports main restricted universe multiverse
    38	
    39	deb http://archive.ubuntu.com/ubuntu quantal-security main restricted
    40	deb-src http://archive.ubuntu.com/ubuntu quantal-security main restricted
    41	deb http://archive.ubuntu.com/ubuntu quantal-security universe
    42	deb-src http://archive.ubuntu.com/ubuntu quantal-security universe
    43	deb http://archive.ubuntu.com/ubuntu quantal-security multiverse
    44	deb-src http://archive.ubuntu.com/ubuntu quantal-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb http://archive.canonical.com/ubuntu quantal partner
    51	# deb-src http://archive.canonical.com/ubuntu quantal partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb http://extras.ubuntu.com/ubuntu quantal main
    56	deb-src http://extras.ubuntu.com/ubuntu quantal main 
```



```
ls -la /etc/apt/sources.list.d

total 8
drwxr-xr-x 2 root root 4096 Oct 16  2012 .
drwxr-xr-x 6 root root 4096 Jul 27 13:01 ..

```


```
tail -v -n +1 /etc/apt/sources.list.d/*

tail: cannot open `/etc/apt/sources.list.d/*' for reading: No such file or directory

```

---

### Post by bapoumba on 2014-07-27
This is Quantal 12.10 you have installed here. Please install lubuntu 14.04. I have a 1 GB ram, 1.66 GHz laptop that runs both 14.04 and 14.10 great. You should be fine.
[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

---

