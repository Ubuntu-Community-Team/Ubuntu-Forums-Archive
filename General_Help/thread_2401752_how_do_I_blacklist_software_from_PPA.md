---
title: "how do I blacklist software from PPA?"
date: 2018-09-22
forum: General Help
---

### Post by ardouronerous on 2018-09-22
I'm running Lubuntu 18.04 64-bit and I want to install Palemoon Web Browser and keep it updated via Lubuntu's software updater, by following these commands:

> For **xUbuntu 18.04** run the following:

                  ```
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04/ /' > /etc/apt/sources.list.d/home:stevenpusser.list"
sudo apt-get update
sudo apt-get install palemoon
```

You can add the repository key to apt. Keep in mind that the owner  of the key may distribute updates, packages and repositories that your  system will trust (more information). To add the key, run:
                  
```
wget -nv https://download.opensuse.org/repositories/home:stevenpusser/xUbuntu_18.04/Release.key -O Release.key
sudo apt-key add - < Release.key
sudo apt-get update
```

I've tried to install Palemoon in the past when I was on Xubuntu 14.04 and I've experienced a problem when installing this PPA, the Firejail included in this PPA is an updated version of the Firejail in Ubuntu's own repos, so when I executed this PPA, the PPA tried to update Firejail, however, it tried to uninstall the Xfce desktop environment, so I didn't proceed to install it anymore.

Here's the contents of the PPA:
[http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04/](http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04/)

```
all/
-firejail-profiles_0.9.54-1~obs_all.deb
-fonts-ancient-scripts_2.60-0.1~obs_all.deb
-fonts-symbola_2.60-0.1~obs_all.deb
-ttf-ancient-fonts-symbola_2.60-0.1~obs_all.deb
-ttf-ancient-fonts_2.60-0.1~obs_all.deb

amd64/
-firejail_0.9.54-1~obs_amd64.deb
-firetools_0.9.52-1~obs_amd64.deb
-gtk2-engines-oxygen_1.4.6-2_amd64.deb
-mozplugger_1.14.5-3~obs_amd64.deb
-palemoon_28.1.0~repack-1_amd64.deb

i386/
-firejail_0.9.54-1~obs_i386.deb
-firetools_0.9.52-1~obs_i386.deb
-gtk2-engines-oxygen_1.4.6-2_i386.deb
-mozplugger_1.14.5-3~obs_i386.deb
-palemoon_28.1.0~repack-1_i386.deb

firejail_0.9.54-1~obs.debian.tar.xz
firejail_0.9.54-1~obs.dsc
firejail_0.9.54.orig.tar.xz
firetools_0.9.52-1~obs.debian.tar.xz
firetools_0.9.52-1~obs.dsc
firetools_0.9.52.orig.tar.xz
gtk2-engines-oxygen_1.4.6-2.debian.tar.xz
gtk2-engines-oxygen_1.4.6-2.dsc
gtk2-engines-oxygen_1.4.6.orig.tar.bz2
mozplugger_1.14.5-3~obs.debian.tar.xz
mozplugger_1.14.5-3~obs.dsc
mozplugger_1.14.5.orig.tar.gz
Packages
Packages.gz
palemoon_28.1.0~repack-1.debian.tar.xz
palemoon_28.1.0~repack-1.dsc
palemoon_28.1.0~repack.orig.tar.xz
Release
Release.gpg
Release.key
Sources
Sources.gz
ttf-ancient-fonts_2.60-0.1~obs.debian.tar.xz
ttf-ancient-fonts_2.60-0.1~obs.dsc
ttf-ancient-fonts_2.60.orig.tar.xz
```

So, how do I blacklist all the software in this PPA, all but Palemoon?

---

### Post by monkeybrain20122 on 2018-09-22
You can't blacklist package. Just disable the ppa after you installed palemoon and re-enable it once in a while to check for update. You can use the software&update interface to disable the ppa by simply unchecking it, alternative you can use synaptic's repository tab.

---

### Post by ardouronerous on 2018-09-22
I found a way to do it through here: [https://askubuntu.com/questions/170235/how-do-i-cherry-pick-packages-from-a-ppa/170558#170558](https://askubuntu.com/questions/170235/how-do-i-cherry-pick-packages-from-a-ppa/170558#170558)

> You can actually "cherry pick" certain packages via Synaptic and it's *very* easy. It works like this:
 
[LIST]
[*]If you want to do that for certain PPAs only, chose "Origin"  (lower left corner) in the Synaptic-window and then choose the PPA you  want to change 
[*]choose all the packages you don't want to upgrade automatically any more. 
[*]choose menu "Package/Lock Version". All the packages you chose  won't be upgraded automatically anymore until you unlock them again. 
[/LIST]
 
However, choosing "Origin" didn't work as it only showed Palemoon after I've installed it, so what I did was, I did a search on Synaptic for the PPA's maintainer Steven Pusser and it showed me all the packages maintained by him, so I "Package/Lock Version" all the packages maintained by him, all but Palemoon.

Is this a valid way to blacklist packages off PPAs?

---

### Post by mc4man on 2018-09-22
> **ardouronerous said:**
> I found a way to do it through here: [https://askubuntu.com/questions/170235/how-do-i-cherry-pick-packages-from-a-ppa/170558#170558](https://askubuntu.com/questions/170235/how-do-i-cherry-pick-packages-from-a-ppa/170558#170558)

 
However, choosing "Origin" didn't work as it only showed Palemoon after I've installed it, so what I did was, I did a search on Synaptic for the PPA's maintainer Steven Pusser and it showed me all the packages maintained by him, so I "Package/Lock Version" all the packages maintained by him, all but Palemoon.

Is this a valid way to blacklist packages off PPAs?
Locking packages in synaptic is ok as long as you don't update/upgrade by any other means. Only synaptic knows about packages locked/pinned via synaptic.

However if you are only using synaptic then don't lock, just pay attention when updating packages (if a package is locked in synaptic you'll never be informed of any upgrades to that package (from Ubuntu or ppa repos.) Unless you know you never want to update the locked packages..

---

### Post by ardouronerous on 2018-09-22
Okay, does this affect Lubuntu's software updater in anyway?

Also, there other other ways to update/upgrade on Ubuntu? I've only heard of Ubuntu's bullt-in updater and updating via Synaptic.

---

### Post by mc4man on 2018-09-22
> **ardouronerous said:**
> Okay, does this affect Lubuntu's software updater in anyway?

Also, there other other ways to update/upgrade on Ubuntu? I've only heard of Ubuntu's bullt-in updater and updating via Synaptic.
From the cli, i.e
sudo apt update
sudo apt upgrade

---

### Post by ardouronerous on 2018-09-22
so  sudo apt update and upgrade will not recognize the packages that I locked via Synaptic?

---

### Post by monkeybrain20122 on 2018-09-22
I know about locking packages from synaptic but aside from what mc4man said (sudo apt upgrade won't respect it, you can pin package in apt though, but it still have the problems below) There are a few other issues in your scenario:
1) pin package is only efficient if you have one or two packages in the ppa you don't want to upgrade,  but if you have many packages in the ppa and you only want upgrading one, instead of pinning a bunch of packages I would rather just disable/enable the ppa as needed 2) you may not want to upgrade packages A from the ppa, but what if there is an upgrade from the official repo? In that case if the ppa is activated and the official update has lower version synaptic won't show it and if the package is pinned (even if you disable ppa) it still won't be upgraded if one exists and come from channel other than your ppa.

---

### Post by ardouronerous on 2018-09-22
So it would be better to just remove Pale Moon and this PPA then, because it's more trouble then it's worth.  There has to be a way to blacklist versions of software instead of locking the entire software all together.

---

