---
title: "Problem upgrading / reinstalling xfce power manager"
date: 2015-01-17
forum: General Help
---

### Post by rdh61 on 2015-01-17
On Lubuntu 14.04 LTS I noticed xfce power manager was not being upgraded. I went to synaptic and it told be some dependencies were not satisfied, but it didn't tell me which. I uninstalled it and tried to reinstall, and got:

```
xfce4-power-manager:
  Depends: upower (>=0.99) but 0.9.23-2ubuntu1 is to be installed
```

What does this mean and how do I resolve it?

Many thanks.

---

### Post by Bucky Ball on 2015-01-17
Try:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install xfce4-power-manager
```

Please report any and all errors.

---

### Post by kerry_s on 2015-01-17
why would you tell someone to distribution upgrade when there using 14.04.1 lts, that defeats the purpose of installing a lts right?
just wondering?

i would have went with:
sudo apt-get -f install

see if it could fix itself.

---

### Post by Bucky Ball on 2015-01-17
Distribution upgrade? This:

```
sudo apt-get dist-upgrade
```

... doesn't upgrade 14.04 LTS to 14.10, if that's what you mean. It upgrades any apps or packages in the current install that need to be after running the other commands I gave. The 14.04 install will then be as up to date as it can be and the power manager might then install.

There could be an issue because the 14.04 install is not up to date and things are missing. By all means, issue the command you suggest also. I wouldn't suggest the OP upgrade to 14.10, and I wasn't. ;)

Please read the explanation of the commands I gave [HERE]("http://askubuntu.com/questions/222348/what-does-sudo-apt-get-update-do"). That might clear things up. dist-upgrade has nothing to do with upgrading to a newer release.

---

### Post by rdh61 on 2015-01-17
> **Bucky Ball said:**
> Try:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install xfce4-power-manager
```

After the other 3 commands, sudo apt-get dist-upgrade gave: 0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

Then:

```
robert@robert-P4i65GV:~$ sudo apt-get install xfce4-power-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 xfce4-power-manager : Depends: upower (>= 0.99) but 0.9.23-2ubuntu1 is to be installed
                       Recommends: xfce4-power-manager-plugins but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
robert@robert-P4i65GV:~$ 
```

---

### Post by rdh61 on 2015-01-17
> **kerry_s said:**
> i would have went with:
sudo apt-get -f install

see if it could fix itself.

Also tried this but it gave: "0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade."

---

### Post by kerry_s on 2015-01-17
> **Bucky Ball said:**
> Distribution upgrade? This:

```
sudo apt-get dist-upgrade
```

... doesn't upgrade 14.04 LTS to 14.10, if that's what you mean. It upgrades any apps or packages in the current install that need to be after running the other commands I gave. The 14.04 install will then be as up to date as it can be and the power manager might then install.

There could be an issue because the 14.04 install is not up to date and things are missing. By all means, issue the command you suggest also. I wouldn't suggest the OP upgrade to 14.10, and I wasn't. ;)

Please read the explanation of the commands I gave [HERE]("http://askubuntu.com/questions/222348/what-does-sudo-apt-get-update-do"). That might clear things up. dist-upgrade has nothing to do with upgrading to a newer release.

There are several ways to upgrade from one Ubuntu release to another.
[https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)

---

### Post by kerry_s on 2015-01-17
> **rdh61 said:**
> Also tried this but it gave: "0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade."

are all your apt sources activated? i'm on debian so no point in showing you mine.

---

### Post by rdh61 on 2015-01-17
All the boxes are ticked in Software and Updates.

---

### Post by kerry_s on 2015-01-17
you've tried removing xfce power manager , did you remove all the dependencys with it?

in this order:
sudo apt-get purge xfce4-power-manager && sudo apt-get autoremove && sudo apt-get autoclean

that should remove everything, that has to do with xfce4-power-manager.
then can try installing it fresh:
sudo apt-get install xfce4-power-manager

---

### Post by ian-weisser on 2015-01-17
> **rdh61 said:**
> 

```

The following packages have unmet dependencies.
 xfce4-power-manager : Depends: upower (>= 0.99) but 0.9.23-2ubuntu1 is to be installed
                       Recommends: xfce4-power-manager-plugins but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Take a look at upower in the various releases of Ubuntu:
```
$ rmadison -u ubuntu upower
 upower | **0.9.23-2ubuntu1**       | trusty           | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 upower | 0.9.23-2ubuntu2       | utopic           | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 upower | **0.99.2-1**              | vivid            | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

So you are running Trusty (14.04), but xfce4-power-manager wants a newer version (15.04).
That usually indicates that you have added an inappropriate repository to your Software Sources and created a version conflict.

Generally, it's easy to fix, once we discover the inappropriate source.
Please run the following two commands, and post the entire output here.
```
apt-cache policy xfce4-power-manager
apt-cache policy upower
```

---

### Post by rdh61 on 2015-01-19
> **kerry_s said:**
> you've tried removing xfce power manager , did you remove all the dependencys with it?

in this order:
sudo apt-get purge xfce4-power-manager && sudo apt-get autoremove && sudo apt-get autoclean

that should remove everything, that has to do with xfce4-power-manager.
then can try installing it fresh:
sudo apt-get install xfce4-power-manager

Thank you but this produced the same error as before.

---

### Post by rdh61 on 2015-01-19
@ ian-weisser

```
robert@robert-P4i65GV:~$ apt-cache policy xfce4-power-manager
xfce4-power-manager:
  Installed: (none)
  Candidate: 1.4.2+git-0~1659~ubuntu14.04.1
  Version table:
     1.4.2+git-0~1659~ubuntu14.04.1 0
        500 [http://ppa.launchpad.net/xubuntu-dev/xubuntu-staging/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xubuntu-staging/ubuntu/) trusty/main i386 Packages
     1.2.0-3ubuntu4.1 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty-updates/universe i386 Packages
     1.2.0-3ubuntu4 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
robert@robert-P4i65GV:~$ apt-cache policy upower
upower:
  Installed: 0.9.23-2ubuntu1
  Candidate: 0.9.23-2ubuntu1
  Version table:
 *** 0.9.23-2ubuntu1 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by raptir on 2015-01-19
> **rdh61 said:**
> @ ian-weisser

```
robert@robert-P4i65GV:~$ apt-cache policy xfce4-power-manager
xfce4-power-manager:
  Installed: (none)
  Candidate: 1.4.2+git-0~1659~ubuntu14.04.1
  Version table:
     1.4.2+git-0~1659~ubuntu14.04.1 0
        **500 [http://ppa.launchpad.net/xubuntu-dev/xubuntu-staging/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xubuntu-staging/ubuntu/) trusty/main i386 Packages**
     1.2.0-3ubuntu4.1 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty-updates/universe i386 Packages
     1.2.0-3ubuntu4 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
robert@robert-P4i65GV:~$ apt-cache policy upower
upower:
  Installed: 0.9.23-2ubuntu1
  Candidate: 0.9.23-2ubuntu1
  Version table:
 *** 0.9.23-2ubuntu1 0
        500 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status
```

That's likely the issue. You have the xubuntu-staging PPA enabled, which is trying to install xfce4-power-manager 1.4.2 while ubuntu 14.04 provides 1.2.0. I would remove the PPA:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xubuntu-dev/xubuntu-staging
```

If you know for certain you have not installed any other packages from xubuntu-staging (you can check this using synaptic) you can just remove it from your software sources without using ppa-purge.

---

### Post by rdh61 on 2015-01-19
Thank you, that has solved the problem and I have been able to install xfce power manager.

---

