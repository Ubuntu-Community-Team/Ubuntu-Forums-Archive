---
title: "Need Help removing PPA"
date: 2014-05-27
forum: General Help
---

### Post by SuperFreak on 2014-05-27
Using the instructions [HERE]("http://linuxg.net/the-cinnamon-stable-ppa-has-been-disabled-but-cinnamon-2-2-0-can-still-be-installed-on-ubuntu-14-04-trusty-tahr/") I tried to install Cinnamon DE on my desktop but stuck at this first command:
```
sudo sh -c 'echo "deb http://packages.linuxmint.com/ qiana main upstream import" >> /etc/sources.list'

```
and could get no further. I am thinking now these instructions are messed up and possibly dangerous. If I open Sources.list in etc I get the options listed in my screenshot. How do I get rid of that (thereby undoing the above command)so adding/install only are not offered for that PPA. The actual PPA does not show up in my list of other software under software and updates

---

### Post by papibe on 2014-05-27
Hi SuperFreak.

You did not added a ppa, but added a repository directly to your sources file.

To remove it, open your sources file:
```
gksudo gedit /etc/apt/sources.list
```
Go to the end of the file and remove the line you added:
```
deb http://packages.linuxmint.com/ qiana main upstream import
```
Save the file, and then update your sources:
```
sudo apt-get update
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by SuperFreak on 2014-05-27
Thank you for your help. The file contained only : deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) qiana main upstream import (repeated twice as I tried the command twice)
I removed the entries and now the file is 0 bytes and if I click on it I get results shown in screenshot. Is this as it should be. All my PPAs still seem to be intact.

---

### Post by papibe on 2014-05-27
Not good.

What version are you running? We can post the proper sources so you can paste them back.

Regards.

---

### Post by Bashing-om on 2014-05-27
SuperFreak; Hi !

Nope, something definitely went south.
Let's see if we can move the backup sources.list file back into place of the sources.list file that was removed.

Post back the output - between code tags - of terminal command:
```

ls -la /etc/apt/sources*

```
just to make sure that backup file exist.

If you are comfortable, and that file is still in existence, do:
```

sudo cp -p /etc/apt/sources.list~ /etc/apt/sources.list

```

Still have to deal with the Cinnamon DE. Now that  Cinnamon has been pulled from the official repository, I am not sure of a good means myself to proceed.

this is but my little bit to
[INDENT][INDENT][INDENT]try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by SuperFreak on 2014-05-28
Thanks
@Bashing-Om
Here is out put of ls -la /etc/apt/sources*
```
ls -la /etc/apt/sources*
-rw-rw-r-- 1 root root 3106 May 26 13:23 /etc/apt/sources.list
-rw-rw-r-- 1 root root 3106 May 26 13:23 /etc/apt/sources.list.save

/etc/apt/sources.list.d:
total 108
drwxr-xr-x 2 root root 4096 May 24 18:44 .
drwxr-xr-x 6 root root 4096 May 23 09:03 ..
-rw-r--r-- 1 root root  170 May 26 13:23 danielrichter2007-grub-customizer-trusty.list
-rw-r--r-- 1 root root  170 May 26 13:23 danielrichter2007-grub-customizer-trusty.list.save
-rw-r--r-- 1 root root    0 May 26 13:23 diesch-testing-trusty.list
-rw-r--r-- 1 root root    0 May 26 13:23 diesch-testing-trusty.list.save
-rw-r--r-- 1 root root  126 May 26 13:23 flozz-flozz-trusty.list
-rw-r--r-- 1 root root  126 May 26 13:23 flozz-flozz-trusty.list.save
-rw-r--r-- 1 root root    0 May 26 13:20 gwendal-lebihan-dev-cinnamon-nightly-trusty.list
-rw-r--r-- 1 root root    0 May 26 13:20 gwendal-lebihan-dev-cinnamon-nightly-trusty.list.save
-rw-r--r-- 1 root root    0 May 21 20:06 gwendal-lebihan-dev-cinnamon-stable-trusty.list
-rw-r--r-- 1 root root    0 May 21 20:06 gwendal-lebihan-dev-cinnamon-stable-trusty.list.save
-rw-r--r-- 1 root root  118 May 26 13:23 jfi-ppa-trusty.list
-rw-r--r-- 1 root root  118 May 26 13:23 jfi-ppa-trusty.list.save
-rw-r--r-- 1 root root    0 May 26 13:23 libdvdcss.list
-rw-r--r-- 1 root root   58 May 26 13:23 libdvdcss.list.save
-rw-r--r-- 1 root root    0 May  6 12:43 michael-astrapi-ppa-trusty.list
-rw-r--r-- 1 root root    0 May  6 12:43 michael-astrapi-ppa-trusty.list.save
-rw-r--r-- 1 root root  416 May 26 13:23 opera.list
-rw-r--r-- 1 root root  416 May 26 13:23 opera.list.save
-rw-r--r-- 1 root root  150 May 26 13:23 otto-kesselgulasch-gimp-trusty.list
-rw-r--r-- 1 root root  150 May 26 13:23 otto-kesselgulasch-gimp-trusty.list.save
-rw-r--r-- 1 root root    0 May 15 19:08 peterlevi-ppa-trusty.list
-rw-r--r-- 1 root root    0 May 15 19:08 peterlevi-ppa-trusty.list.save
-rw-r--r-- 1 root root  126 May 26 13:23 shutter-ppa-trusty.list
-rw-r--r-- 1 root root  126 May 26 13:23 shutter-ppa-trusty.list.save
-rw-r--r-- 1 root root  132 May 26 13:23 teejee2008-ppa-trusty.list
-rw-r--r-- 1 root root  132 May 26 13:23 teejee2008-ppa-trusty.list.save
-rw-r--r-- 1 root root  134 May 26 13:23 ubuntu-wine-ppa-trusty.list
-rw-r--r-- 1 root root  134 May 26 13:23 ubuntu-wine-ppa-trusty.list.save
-rw-r--r-- 1 root root  222 May 26 13:23 videolan-stable-daily-trusty.list
-rw-r--r-- 1 root root  222 May 26 13:23 videolan-stable-daily-trusty.list.save
-rw-r--r-- 1 root root  140 May 26 13:23 webupd8team-gnome3-trusty.list
-rw-r--r-- 1 root root  140 May 26 13:23 webupd8team-gnome3-trusty.list.save
-rw-r--r-- 1 root root  136 May 26 13:23 webupd8team-java-trusty.list
-rw-r--r-- 1 root root  136 May 26 13:23 webupd8team-java-trusty.list.save
-rw-r--r-- 1 root root  146 May 26 13:23 yannubuntu-boot-repair-trusty.list
-rw-r--r-- 1 root root  146 May 26 13:23 yannubuntu-boot-repair-trusty.list.save
```


Output from cp command is this:
```
david@MainSqueeze:~$ sudo cp -p /etc/apt/sources.list~ /etc/apt/sources.list
[sudo] password for david: 
cp: cannot stat ‘/etc/apt/sources.list~’: No such file or directory
david@MainSqueeze:~$ 

```

There is a 3 kb file in that directory called sources.list but no sources.list~

Cinnamon DE was added from the nightly PPAs and then I removed the PPA

> Not good.

What version are you running? We can post the proper sources so you can paste them back.

Regards. 

I am running Ubuntu 14.04 64 bit

---

### Post by SuperFreak on 2014-05-28
I have a backup of my installation from ReDo(pre Cinnamon). Worst case scenario  I will install that. As I haven't tested the backup I would like to avoid that if possible

---

### Post by papibe on 2014-05-28
This is the sources.list file for Ubuntu 14.04 Trusty Tahr:
```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
```

---

### Post by SuperFreak on 2014-05-28
Thanks Papibe,
for helping me out of this mess. I have copied the code you gave into my sources.list file. Is there any need for additional code to reflect existing PPAs in that file?


EDIT: I had a look at sources.list file on my other PC and see that the PPAs are not included in that file so I guess the file is as it should be....Again Thanks

---

### Post by papibe on 2014-05-28
PPA's are not added to that file.

When you add a ppa, a single source file is created on '/etc/apt/sources.list.d'. For instance, I see that you have added the webupd8team ppa, so you have the file:
```
/etc/apt/sources.list.d/webupd8team-gnome3-trusty.list
```
Does that help?
Regards.

---

### Post by SuperFreak on 2014-05-28
Thanks...Yes that folder seems to contain all the PPAs

---

