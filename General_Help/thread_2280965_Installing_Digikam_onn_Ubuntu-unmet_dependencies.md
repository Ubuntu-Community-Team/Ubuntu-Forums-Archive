---
title: "Installing Digikam onn Ubuntu-unmet dependencies"
date: 2015-06-03
forum: General Help
---

### Post by SuperFreak on 2015-06-03
I am trying to install Digikam on Ubuntu 14.04 with the following commands
```
sudo apt-add-repository ppa:philip5/extra

sudo apt-get update

sudo apt-get install digikam
```

I am getting the following error message after the last command

```
david@MainSqueeze:~$ sudo apt-get install digikam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 digikam : Depends: libkgeomap2 (>= 1.0~digikam4.10.0) but it is not going to be installed
           Recommends: kipi-plugins but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
david@MainSqueeze:~$ sudo apt-get install digikam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 digikam : Depends: libkgeomap2 (>= 1.0~digikam4.10.0) but it is not going to be installed
           Recommends: kipi-plugins but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by v3.xx on 2015-06-03
What happens if you try to install libkgeomap2 with apt-get?

Its available for install?
```
apt-cache policy libkgeomap2
```

I have a habit of throwing caution to the wind.  You could force the install using dpkg.

Is there a possibility of another ppa messing with you?

---

### Post by SuperFreak on 2015-06-03
```
david@MainSqueeze:~$ apt-cache policy libkgeomap2
libkgeomap2:
  Installed: (none)
  Candidate: 1.0~digikam4.10.0-trusty~ppa4kde414
  Version table:
     1.0~digikam4.10.0-trusty~ppa4kde414 0
        500 http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu/ trusty/main amd64 Packages
     1.0~digikam4.10.0-trusty~ppa4 0
        500 http://ppa.launchpad.net/philip5/extra/ubuntu/ trusty/main amd64 Packages

```
When I try to install it I get more unmet dependencies. I don't want to install a large number of KDE packages just to install Digikam so I may give up and find another program.

---

### Post by v3.xx on 2015-06-03
> I don't want to install a large number of KDE packages just to install Digikam
Its a big download, but I would think peanuts to your i7.  I have done kde packages before and you can end up with more in the menu.

I take it that the digikam package in the repositories is not to your liking.

---

### Post by SuperFreak on 2015-06-03
> **v3.xx said:**
> Its a big download, but I would think peanuts to your i7.  I have done kde packages before and you can end up with more in the menu.

I take it that the digikam package in the repositories is not to your liking.

It looks like a good program but I am unsure of the number of dependencies I need to install. I am trying Nomacs and Darkroom at present instead and I may try Shotwell. Nomacs and Darkroom installed without issue.
I tried downloading through software center and the PPA (Digikam) and unmet dependencies both times

On a chance I installed ShowFoto and it installed Digikam also without any problems so I can try it out now. Thanks for your help

---

### Post by v3.xx on 2015-06-03
Ok, I added the digikam ppa to a vanilla mate 14o4 install.  600M download, funny :) I now have some kde apps in my menu, but it installed and boots.

Edit
Just seen your edit..
Good show

---

