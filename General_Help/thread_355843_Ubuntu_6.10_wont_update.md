---
title: "Ubuntu 6.10 wont update"
date: 2007-02-07
forum: General Help
---

### Post by azazel00 on 2007-02-07
I've been trying to update my ubuntu distribution today, but I keep getting messages similar to this one:

E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.5-0ubuntu3.1_all.deb: files list file for package `libwxbase2.6-0' is missing final newline

All of them mention the libwxbase2.6-0

I've tried doing updates one by one, to see if the problem is the related to a particular package of the ones Im trying to install.

What can I do to fix this?

Regards,
az

---

### Post by taurus on 2007-02-07
What if you run

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by azazel00 on 2007-02-07
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libisc11_1%3a9.3.2-2ubuntu3.1_i386.deb (--unpack):
 files list file for package `libwxbase2.6-0' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libisc11_1%3a9.3.2-2ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

That's the out put of the third command. The first two do acheive their goal.

---

### Post by taurus on 2007-02-07
Can I have a look at your /etc/apt/sources.list?  Somehow you have downloaded a bad file!

```
cat /etc/apt/sources.list
```

---

### Post by azazel00 on 2007-02-07
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe


deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

# deb http://pr.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://pr.archive.ubuntu.com/ubuntu/ edgy universe

# deb http://pr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://pr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe

deb http://ubuntu.beryl-project.org edgy main

deb http://www.getautomatix.com/apt edgy main


# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://www.beerorkid.com/compiz edgy main-edgy

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

#WINE
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

deb http://getswiftfox.com/builds/debian unstable non-free

#AUTOMATIX BLEEDER REPOS START

deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
#AUTOMATIX BLEEDER REPOS END

deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable

```

I just tried reinstalling the libwx... package with Synaptic.. and even that failed.

---

### Post by dexter on 2007-02-07
Try disabling those automatix repositories, update and upgrade the list like mentioned above, does it work now ?

---

### Post by taurus on 2007-02-07
I would remove all the **us.** and the **pr.** from the repos in /etc/apt/sources.list.  Save it and run those three commands again.

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by jackrobinson on 2007-02-07
try this:
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.1.5_i386.deb
sudo dpkg -i libwxbase2.6-0_2.6.3.2.1.5_i386.deb
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by azazel00 on 2007-02-07
> **dexter said:**
> Try disabling those automatix repositories, update and upgrade the list like mentioned above, does it work now ?

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libisc11_1%3a9.3.2-2ubuntu3.1_i386.deb (--unpack):
 files list file for package `libwxbase2.6-0' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libisc11_1%3a9.3.2-2ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

---

### Post by jackrobinson on 2007-02-07
> **dexter said:**
> Try disabling those automatix repositories, update and upgrade the list like mentioned above, does it work now ?
if you notice carefully, the automatix repos are actually all official ubuntu repositories except the one for compiz which is not host to the offending package.

---

### Post by azazel00 on 2007-02-07
> **jackrobinson said:**
> try this:
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.1.5_i386.deb
sudo dpkg -i libwxbase2.6-0_2.6.3.2.1.5_i386.deb
sudo apt-get update
sudo apt-get upgrade
```

```
azazel@ubuntux:~$ sudo dpkg -i libwxbase2.6-0_2.6.3.2.1.5_i386.debdpkg - warning: downgrading libwxbase2.6-0 from 2.6.3.2.1.5ubuntu0.1 to 2.6.3.2.1.5.
(Reading database ... dpkg: error processing libwxbase2.6-0_2.6.3.2.1.5_i386.deb (--install):
 files list file for package `libwxbase2.6-0' is missing final newline
Errors were encountered while processing:
 libwxbase2.6-0_2.6.3.2.1.5_i386.deb
Processing was halted because there were too many errors.
azazel@ubuntux:~$ 

```

:confused:

---

### Post by jackrobinson on 2007-02-07
ok do the following:
```
sudo gedit /var/lib/dpkg/status
```
and in that file, search for the offending package (libwxbase2.6)and remove all information for it.
Now save and close the file and do:
```
sudo apt-get update
sudo apt-get -f install
```

---

### Post by azazel00 on 2007-02-07
> **jackrobinson said:**
> ok do the following:
```
sudo gedit /var/lib/dpkg/status
```
and in that file, search for the offending package (libwxbase2.6)and remove all information for it.
Now save and close the file and do:
```
sudo apt-get update
sudo apt-get -f install
```

The ```
sudo apt-get -f install
``` didnt do anything persay. But after removing every entry in the file, I managed to update my system.

I wonder, doesnt removing the package every where mess up my dependencies or something?

Anyway, works now.

Regards,
az

---

### Post by jackrobinson on 2007-02-07
> **azazel00 said:**
> The ```
sudo apt-get -f install
``` didnt do anything persay. But after removing every entry in the file, I managed to update my system.

I wonder, doesnt removing the package every where mess up my dependencies or something?

Anyway, works now.

Regards,
az
The status file is like a current log which apt blindly believes. Once you empty it, apt creates a new one and gets happy again. Nothing lost.

---

