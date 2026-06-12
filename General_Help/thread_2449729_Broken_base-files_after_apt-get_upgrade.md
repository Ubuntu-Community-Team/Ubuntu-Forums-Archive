---
title: "Broken base-files after apt-get upgrade"
date: 2020-09-01
forum: General Help
---

### Post by person3 on 2020-09-01
After running now  ```
sudo apt-get install wmctrl
``` the command fails with the following messages:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  wmctrl
0 to upgrade, 1 to newly install, 0 to remove and 125 not to upgrade.
2 not fully installed or removed.
Need to get 131 kB of archives.
After this operation, 80.9 kB of additional disk space will be used.
Get:1 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 base-files amd64 9.6ubuntu13.1 [59.1 kB]
Get:2 http://old-releases.ubuntu.com/ubuntu zesty/main amd64 resolvconf all 1.79ubuntu4 [50.0 kB]
Get:3 http://old-releases.ubuntu.com/ubuntu zesty/universe amd64 wmctrl amd64 1.07-7 [21.8 kB]
Fetched 131 kB in 1s (100 kB/s)   

dpkg: error processing package base-files (--configure):
 package base-files is not ready for configuration
 cannot configure (current status 'half-installed')
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I believe this has been happening since ```
 apt-get upgrade
``` failed yesterday with some weird error, unfortunately I didn't save that error ):
I have tried ```
dkpg --configure -a
``` but didn't seem to help.

---

### Post by CelticWarrior on 2020-09-01
Welcome.

"[COLOR=#000000][FONT=&quot]zesty" means Ubuntu 17.04. This release is End of Life.
Please install a supported release, thank you.[/FONT][/COLOR]

---

### Post by deadflowr on 2020-09-01
Cut your losses and upgrade to a supported release.

---

### Post by person3 on 2020-09-01
I thought that's what the apt-get upgrade did but that failed

---

### Post by coffeecat on 2020-09-01
> **person3 said:**
> I thought that's what the apt-get upgrade did but that failed

It's not surprising it failed. apt-get upgrade does not upgrade your operating system to a supported release. It never did; it never will. apt-get upgrade updates installed packages within the same release in order to apply bug fixes and security patches. But only when the repositories for that release are open. 17.04/Zesty went end of life in January 2018, and the Zesty repositories would have closed soon after. That means that you will not have been able to get updates or install new packages for well over 2½ years. I truly hope your system has not been connected to the internet during that time. It will have many unpatched vulnerabilies.

When deadflowr mentioned upgrading to a supported release, they would have meant getting to a supported release by whatever means is practicable. It is theoretically possible to upgrade 17.04 to a supported release, but that way is almost certainly doomed to failure after such a long time. Your only sane option is to make a fresh installation of, preferably, a LTS release such as 20.04.

Last point. 17.04 was an interim release, supported for 9 months only. In future you may want to rely on LTS (long-term support) releases, supported for 5 years.

---

### Post by TheFu on 2020-09-01
> **person3 said:**
> I thought that's what the apt-get upgrade did but that failed

Nope.  System Maintenance for Ubuntu desktops: [https://blog.jdpfu.com/linsysmaint](https://blog.jdpfu.com/linsysmaint) Please check it out.

Non-LTS releases are supported for 9 months. Moving to the next release BEFORE support ends is necessary to avoid being stuck.  LTS releases are April of even years. Any other release is not LTS.   For most choices of LTS desktops, expect 3 yrs of support. Only the stock gnome3 ubuntu desktop has the full 5 yrs of support ==== from the release date ====  not when you install.

Because 17 is so long ago, those repos ave been gone a while. The only viable way forward is a fresh install. 2-3 yrs ago, an upgrade may have been possible. Unlikely now.

---

### Post by person3 on 2020-09-01
Thanks everyone for your answers. I suppose I am stuck with this version for now, only real option is to download and install a new version of ubuntu and make sure it's an LTS this time.

---

### Post by TheFu on 2020-09-01
Please don't use any 17.xx release on the internet. it isn't safe.  There are remote access methods with complete pwn'ership possible. by some bad people.  BTW, 19.xx releases aren't safe either and support ended for those a few months ago too.

LTS - even year, April (04). Assume support for 3 yrs for any desktop.  So a supported LTS is 20.04 or 18.04 today.  Those are safe rules of thumb.  For most people, moving from LTS to LTS desktop releases provides plenty of time to plan and do it. Really cautious people, like me, can wait until the fall after the LTS was released to migrate.  So in October, moving my 18.04 desktops to 20.04 would be a plan, if I had any 18.04 desktops.

---

### Post by Impavidus on 2020-09-02
I would guess that you were already aware of the fact that you use a dead release, as you tried to get updates from the old-releases server. What's more, there are 125 of those updates, all at least 2 1/2 years old, available.

I doubt you're stuck with this version for now, as you can download and install 20.04 LTS (the latest release and an LTS release) today. That is, if you've got a somewhat decent internet connection, a small usb drive to use as a live disk and another external drive to backup your files. And you should have those anyway.

---

