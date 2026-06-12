---
title: "Cannot use add-apt-repository in Ubuntu 17.04 development branch"
date: 2018-02-16
forum: General Help
---

### Post by coder91 on 2018-02-16
My Ubuntu updated a month back to Ubuntu 17.04 and is now stuck in  the development branch. I am trying to update it to Ubuntu 17.10, but I  get the error ```
ppa.launchpad.net/ubuntu-wine/ppa/ubuntu yakkety Release' does not have a Release file


```  To solve this issue, I followed the first answer on [this]("https://askubuntu.com/questions/858374/apt-get-update-missing-release-file") and I cannot manually add PPA from [launchpad PPA page]("https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa") as my Ubuntu version is not listed. It otherwise suggests that I use the command ```
sudo add-apt-repository ppa:ubuntu-wine/ppa
``` but when I run this, I get the following error:

```
Traceback (most recent call last):
File "/usr/bin/add-apt-repository", line 95, in <module>
sp = SoftwareProperties(options=options)
File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 114, in __init__
self.reload_sourceslist()
File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 607, in reload_sourceslist
self.distro.get_sources(self.sourceslist)    
File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
(self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/zesty
```

Now for this issue, I followed [Apt "could not find a distribution template" error]("https://askubuntu.com/questions/49040/apt-could-not-find-a-distribution-template-error") and turns out that on using ```
lsb_release -a 
```I get:
```
LSB Version:    core-9.20160110ubuntu5-amd64:core-9.20160110ubuntu5-noarch:security-9.20160110ubuntu5-amd64:security-9.20160110ubuntu5-noarch
Distributor ID: Ubuntu
Description:    Ubuntu Zesty Zapus (development branch)
Release:    17.04
Codename:   zesty
```
For this issue, I followed the [thread]("https://ubuntuforums.org/showthread.php?t=2361810&page=2") but he doesn't seem to describe how he finally manages to achieve 
```
natesnape@A-Toaster:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty
natesnape@A-Toaster:~$
```
I also followed the first answer on [12.04 reports itself as quantal after installing the toolchain-test-ppa?]("https://askubuntu.com/questions/126498/12-04-reports-itself-as-quantal-after-installing-the-toolchain-test-ppa/135472#135472") but after following all the steps when I try ```
sudo apt-get upgrade
``` I get the following output:```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  aptitude-common
The following packages will be DOWNGRADED:
  base-files
1 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 894 kB of archives.
After this operation, 856 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Err:1 http://archive.ubuntu.com/ubuntu yakkety/main amd64 base-files amd64 9.6ubuntu5
  404  Not Found
Err:2 http://archive.ubuntu.com/ubuntu yakkety/main amd64 aptitude-common all 0.8.3-1ubuntu1
  404  Not Found
Err:2 http://archive.ubuntu.com/ubuntu yakkety/main i386 aptitude-common all 0.8.3-1ubuntu1
  404  Not Found
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_9.6ubuntu5_amd64.deb  404  Not Found
E: ailed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/aptitude/aptitude-common_0.8.3-1ubuntu1_all.deb  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

And thus upgrade fails and I am again stuck. I think I need to get out  of development branch as I cannot find base files for it, but I can't  figure out a way to get out of it and desperately need some help. Thanks  in advance!

---

### Post by DuckHook on 2018-02-17
Yakkety has been dead for a year and Zesty died last month. Both repos have been retired. That is why you cannot do anything with it using *apt*. Moreover, if you want to salvage what you can and have any chance to successfully upgrade, you should eliminate all PPAs; not add them. The rule of thumb is: back out all PPAs before trying to *do-release-upgrade*.

Instructions for end-of-life upgrades: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by deadflowr on 2018-02-17
17.04 is no where near development anymore.
It's no longer even supported.
You need to update to a new release.
(Or reinstall an older supported release like 14.04 or 16.04)

See: [https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

In the long and short of it, you'd probably be better off reinstalling a new release like 17.10.


Ninja'd by Duckhook.

---

