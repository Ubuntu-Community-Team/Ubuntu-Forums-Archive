---
title: "Error opening the cache E:malformed entry 53"
date: 2020-02-08
forum: General Help
---

### Post by rjain19 on 2020-02-08
Error message appears when attempting to install new programs and
sudo apt-get update

E: Malformed entry 53 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.


I have already browsed the couple of relevant posts about this, without any success. Though this may be due to my inexperience with Ubuntu.

Otherwise Ubuntu is great!!

I have used to code sudo -H gedit /etc/apt/sources.list

The result I have pasted here

```
deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-proposed main universe multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionicmultiverse
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionicmultiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic multiverse
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) bionic partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) bionic partner

```

---

### Post by CatKiller on 2020-02-08
```
deb http://archive.canonical.com/ubuntu bionicmultiverse
# deb-src http://archive.canonical.com/ubuntu bionicmultiverse
```

You need a space between bionic and multiverse.

---

### Post by rjain19 on 2020-02-08
rahul@rahul-HP-Pavilion-dv5-Notebook-PC:~$ sudo -H gedit/etc/apt/sources.list
[sudo] password for rahul: 
sudo: gedit/etc/apt/sources.list: command not found

---

### Post by jeremy31 on 2020-02-08
Try ```
gedit admin:///etc/apt/sources.list
```

---

### Post by rjain19 on 2020-02-08
In terminal i have got the message

rahul@rahul-HP-Pavilion-dv5-Notebook-PC:~$ sudo -H gedit admin:///etc/apt/sources.list

** (gedit:2072): WARNING **: 19:24:17.008: Operation not supported

and one note pad open which stated "Could not open the file "admin:///etc/apt/sources.list"
unable to handle "admin:" locations

---

### Post by rjain19 on 2020-02-08
Now the issue got resolved.

Thanks for your prompt response and support.

---

### Post by CatKiller on 2020-02-08
> **rjain19 said:**
> rahul@rahul-HP-Pavilion-dv5-Notebook-PC:~$ sudo -H gedit/etc/apt/sources.list
[sudo] password for rahul: 
sudo: gedit/etc/apt/sources.list: command not found

Is your space bar broken? That's the same mistake you've got in the file.

---

### Post by ajgreeny on 2020-02-08
Once again you missed a space, but in the command this time.
If you want to use gedit as the editor
**sudo -H gedit/etc/apt/sources.list**
should be
**sudo -H gedit /etc/apt/sources.list**

However, for safety's sake it is worth getting to know nano (a command-line text editor, but very simple to use) for editing system files.

I note also that you have the ***deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted*** uncommented (ie enabled) which is unusual unless you are still using the DVD install medium as part of your sources.  I suggest you add a # at the start of that line.

---

