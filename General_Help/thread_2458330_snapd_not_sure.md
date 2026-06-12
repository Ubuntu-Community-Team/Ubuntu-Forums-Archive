---
title: "snapd? not sure"
date: 2021-02-22
forum: General Help
---

### Post by jfaberna on 2021-02-22
So I know this maybe just opinions, but what is it with snap and Ubuntu? I was not aware of it until my googling difference packages told me to install that package with snap.  In most cases I either got an older version of the software or software installed in weird places with a directory structure I could not figure out how to live with. Software development packages require you to know and work with their directory structure and it's different if I'm forced to install with Snap.

If I stay with Ubuntu, which is my preference, can I completely remove Snap and still get things done? I will not use it.

---

### Post by howefield on 2021-02-22
> **jfaberna said:**
> If I stay with Ubuntu, which is my preference, can I completely remove Snap and still get things done? I will not use it.

Running

```
sudo apt purge snapd
```

will remove snapd and all snap packages, if there are any installed.

For the most part your only issue would be if a particular piece of software is available only in the snap format.

You should be able to still get things done as the majority of software has alternative ways of being installed, removing snapd won't break your installation.

---

### Post by guiverc on 2021-02-22
I personally wouldn't purge `snapd`, but with a couple of commands you can disable it so it doesn't run (allowing you to enable it faster should you need it).

I primarily use Lubuntu, which being a Ubuntu family product, modern releases include `snapd`, however it installs without any snaps anyway.

I'm using an 11 year old desktop, so I've not exactly got loads of spare resources, but I still find *snaps* handy, and thus they're not disabled on this box. 

I do on occasion use much older laptops with single core processors, and a total of 1GB RAM (Lubuntu 18.04 LTS) and on those boxes stopping/disabling `snapd` sure makes sense to me, but Lubuntu 18.04 didn't come with `snapd` anyway, so I don't have to.

As the snaps run as containerized applications, the 'unique' or 'different' layout doesn't worry me at all, and when I've had issues with a *snap* (rare, and with `chromium` mostly), it wasn't really any harder to work out where my user data was than back when it was a *deb* package (chromium has been a *snap* package on my system for ~21 months now).

For developers, they make sense; snap (*package*) it once and it'll run on all releases, where as *deb* packages really need to be built for every release (*not that difficult if built on infrastructure, just click the releases you want to build for, but that's still a lot of packages that need testing, instead of a single snap*).

Snaps needing extra resources required (*mostly by containerization*) I'm no fan of (*especially with my aged hardware*), but they provides greater choices (*I can even find/use a chromium via deb package if I wanted to*) as there are programs only available as *snap* (which likely would never be packaged as *deb*).

---

### Post by jfaberna on 2021-02-22
My concern is that there are cases where Ubuntu turns an apt install into an excuse to use snap again like in Chromium. I run Linux Mint 20 on my laptop and it does not have snapd and their developers will not use it by default. That is based on Ubuntu so I'm safer, I think, with that. 
However on my development system I've switched to Archlinux with Cinnamon DE. A lot harder to install everything, but at least I know what I got and nothing automatic is going to happen; no auto-updates, no auto-downloads, and no livepatches.

---

### Post by dinkidonk on 2021-02-22
It would be quite nice if snap / snapstore / snapcraft was an optinal install in the *buntu system installer. However, in Kubuntu Discover you can clearly see which source a package is (or will be) installed from, which gives you the choice. Usually the snap packages are (much) newer versions compared to the apt packages and there is the benefit of having the snaps sandboxed, which may be quite nice for some third party packages (Android Studio, M$ VSCode etc.). Snaps are also giving convenient access to install software which is not available in the ordinary repos and would require either building them or installing them as cumbersome downloads which may not be an option for the average user. On the other hand, snaps are bulky and slow which is not really what you want when using Linux.

---

### Post by CatKiller on 2021-02-22
> **jfaberna said:**
> My concern is that there are cases where Ubuntu turns an apt install into **an excuse to use snap again** like in Chromium. 

No. 

[https://snapcraft.io/blog/chromium-in-ubuntu-deb-to-snap-transition](https://snapcraft.io/blog/chromium-in-ubuntu-deb-to-snap-transition)
> **Canonical]On Ubuntu, Chromium is not the default browser, and the package resides in the ‘universe’ section of the archive. Universe contains community-maintained software packages. Despite that, the Ubuntu Desktop Team is committed to packaging and maintaining Chromium because a significant number of users rely on it. 

Maintaining a single release of Chromium is a significant time investment for the Ubuntu Desktop Team working with the Ubuntu Security team to deliver updates to each stable release. As the teams support numerous stable releases of Ubuntu, the amount of work is compounded.

Comparing this workload to other Linux distributions which have a single supported rolling release misses the nuance of supporting multiple Long Term Support (LTS) and non-LTS releases.

Google releases a new major version of Chromium every six weeks, with typically several minor versions to address security vulnerabilities in between. Every new stable version has to be built for each supported Ubuntu release &#8722 said:**
> [*]It’s not the default browser in Ubuntu so has lower impact by virtue of having a smaller user-base 
[*]Snaps are explicitly designed to support a high frequency of stable updates
[*]The upstream project has three release channels (stable, beta, dev) that map nicely to snapd’s default channels (stable, beta, edge). This enables users to easily switch release of Chromium, or indeed have multiple versions installed in parallel
[*]Having the application strictly confined is an added security layer on top of the browser’s already-robust sand-boxing mechanism[/list] 

It's not "packages like Chromium," it's just Chromium. You can add a PPA and get Chromium as a deb maintained by someone else if you want it. 

> **dinkidonk said:**
> On the other hand, snaps are bulky and slow which is not really what you want when using Linux.

Snaps are no slower than software installed through deb packages. They are *slower to start the first time* than software installed through deb packages.

---

### Post by yaminb on 2021-02-22
I've learned to like snaps.
Though I agree there are new things to learn. I have also been unsure which files are used. Which configuration files are used...
I also 'dislike' Ubuntu hiding snap usage behind apt. I find things more confusing that way.

That said, things like the directory structure are workable.
[https://snapcraft.io/docs/system-snap-directory](https://snapcraft.io/docs/system-snap-directory)

Essentially, the snap would be located here: 
/snap/<snapname>/current   

Yet, as others have said there are ways to remove SNAP and you can always still use .deb or PPAs to get things installed. 

Yet, I'd encourage you to just learn to deal with SNAPs as any other part of a system. Ubuntu is going to choose certain packages to be on SNAP by default and away from the base repo. 
You're going to end up removing packages and having a fair bit of extra overhead maintaining PPAs and what not just to avoid snaps.

---

### Post by poorguy on 2021-02-22
> **guiverc said:**
> 
I'm using an 11 year old desktop, so I've not exactly got loads of spare resources, but I still find *snaps* handy, and thus they're not disabled on this box. 

I use a 14 year old desktop running Ubuntu 18.04 and have no problems with snaps.

I've only tried a few snaps and they were installed by default and they open a little slower but they run OK.

---

### Post by HermanAB on 2021-02-22
FWIIW, I always uninstall snap, cloud and mdns.  These are all mostly useless to me.

---

### Post by TheFu on 2021-02-22
> **CatKiller said:**
> 
It's not "packages like Chromium," it's just Chromium. You can add a PPA and get Chromium as a deb maintained by someone else if you want it. 

That is not my experience.  Can I get a non-snap version of lxd?  Please?
I used apt to install lxd, this is what happened ....

```
sudo apt install lxd
==> Installing the LXD snap from the 4.0 track for ubuntu-20.04
lxd (4.0/stable) 4.0.5 from Canonical&#10003; installed
=> Snap installation complete
==> Cleaning up leftovers
Failed to stop lxd.socket: Unit lxd.socket not loaded.
Failed to stop lxd.service: Unit lxd.service not loaded.
Failed to stop lxd-containers.service: Unit lxd-containers.service not loaded.
Failed to disable unit: Unit file lxd.socket does not exist.
Unpacking lxd (1:0.9) ...
Setting up lxd (1:0.9) ...
```

Checking .... 
```
$ dpkg -l lxd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-==================================>
ii  lxd            1:0.9        all          Transitional package - lxd -> snap
```

So it isn't just Chromium.  LXD is server infrastructure.  There is a non-snap version of lxd in prior releases - v1.x, but that is many years old and lacking features added since they moved to snap-only releases.

The ideal that snaps are run anywhere is great, but not true.  About 70-80% of the snaps I install won't run. Seems they don't include all the dependencies. Also, none with GUIs seem to work over X11 remote connections, which is almost always the way I work.

---

### Post by #&amp;thj^% on 2021-02-22
> **TheFu said:**
> That is not my experience.  Can I get a non-snap version of lxd?  Please?
The ideal that snaps are run anywhere is great, but not true.  About 70-80% of the snaps I install won't run. Seems they don't include the dependencies. Also, none seem to work over X11 remote connections, which is almost always the way I work.

+100, I also have no need for it, so it gets the boot (removed) right off the get go.

---

### Post by MartyBuntu on 2021-02-22
Snaps and flatpaks terrify me, so I hide under my bed because I read a scary and tersely worded screed on a blog a long time ago.

---

### Post by HermanAB on 2021-02-23
You jest, but if you get around to installing Slackware (or OpenBSD), which doesn't have any of the power sapping bloatware that comes by default with Ubuntu, you will be blown away by the newfound speed of your machine and will then appreciate why there are many people who do not want the mostly useless bloatware.

---

### Post by jfaberna on 2021-02-23
> **guiverc said:**
> I personally wouldn't purge `snapd`, but with a couple of commands you can disable it so it doesn't run (allowing you to enable it faster should you need it).

As the snaps run as containerized applications, the 'unique' or 'different' layout doesn't worry me at all, and when I've had issues with a *snap* (rare, and with `chromium` mostly), it wasn't really any harder to work out where my user data was than back when it was a *deb* package (chromium has been a *snap* package on my system for ~21 months now).

For developers, they make sense; snap (*package*) it once and it'll run on all releases, where as *deb* packages really need to be built for every release (*not that difficult if built on infrastructure, just click the releases you want to build for, but that's still a lot of packages that need testing, instead of a single snap*).

Snaps needing extra resources required (*mostly by containerization*) I'm no fan of (*especially with my aged hardware*), but they provides greater choices (*I can even find/use a chromium via deb package if I wanted to*) as there are programs only available as *snap* (which likely would never be packaged as *deb*).

I guess I got unlucky.  The first package I installed with Ubuntu Software app used snap and it was an obsolete package in Snap.  The apps main website didn't mention snap as even an option.  The second package was also from the Ubuntu Software app was VSCode. It was up to date, but the install location was totally messed up. I could not figure it out.  Luckily I could remove and install with apt. For now I'll use Linux Mint 20 where they will not allow snap apps to be installed.

---

### Post by dinkidonk on 2021-02-24
> **jfaberna said:**
> The second package was also from the Ubuntu Software app was VSCode. It was up to date, but the install location was totally messed up. I could not figure it out.  Luckily I could remove and install with apt.

I hope that you are not referring to Microsoft VS Code?

---

### Post by jfaberna on 2021-02-24
> **yaminb said:**
> I've learned to like snaps.
Though I agree there are new things to learn. I have also been unsure which files are used. Which configuration files are used...
I also 'dislike' Ubuntu hiding snap usage behind apt. I find things more confusing that way.

That said, things like the directory structure are workable.
[https://snapcraft.io/docs/system-snap-directory](https://snapcraft.io/docs/system-snap-directory)

Essentially, the snap would be located here: 
/snap/<snapname>/current   

Yet, as others have said there are ways to remove SNAP and you can always still use .deb or PPAs to get things installed. 

Yet, I'd encourage you to just learn to deal with SNAPs as any other part of a system. Ubuntu is going to choose certain packages to be on SNAP by default and away from the base repo. 
You're going to end up removing packages and having a fair bit of extra overhead maintaining PPAs and what not just to avoid snaps.

The problem with installing everything in /snap/<snapname>/current is that if <snapname> is a software development system, the world that uses that software has decades of knowledge and scripts that know where everything is supposed to be located and now it somewhere else taking up even more disk space with another directory that seems to have duplicates of current, in my case directory "50" at the same level as current.

I don't have a problem with the concept of snap putting things in their own "sandbox" or container. I use containers when I use Docker on my servers, but that's not forced on me my the OS maintainer.

---

### Post by jfaberna on 2021-02-24
> **dinkidonk said:**
> I hope that you are not referring to Microsoft VS Code?

VSCode is the preferred development platform for the new Raspberry Pi Pico microcontroller for C/C++ with SWD hardware debugging.  That's why I installed it.  Also ESP32 MCU development with Arduino AVR with JTAG debugging is the domain of PlatformIO which is a plugin to VSCode.

So like it or not, it's what I use.

---

### Post by dinkidonk on 2021-02-24
> **jfaberna said:**
> VSCode is the preferred development platform for the new Raspberry Pi Pico microcontroller for C/C++ with SWD hardware debugging.  That's why I installed it.  Also ESP32 MCU development with Arduino AVR with JTAG debugging is the domain of PlatformIO which is a plugin to VSCode.

So like it or not, it's what I use.

In case you've been living under a rock, [here's one for ya](https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=302591).

---

### Post by scottbomb on 2021-02-27
snapd is the first thing I remove after a new install. That and any google garbage I find.
```
sudo rm -rf /var/cache/snapd/; sudo apt autoremove --purge snapd gnome-software-plugin-snap kio-gdrive; sudo rm -rf ~/snap;sudo rm -rf /snap; sudo rm -rf /var/snap; sudo rm -rf /var/lib/snapd
```

---

