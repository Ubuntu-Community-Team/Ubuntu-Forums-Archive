---
title: "What are holding back some update update"
date: 2023-01-26
forum: General Help
---

### Post by bigrockcrasher on 2023-01-26
Hello,
I have been trying to figure out why when I run apt-get dist-upgrade I have updates that are kept-back. According to multiple post, this is caused by conflicts with other installed software. I was wondering how can I find out what these conflicts are.  Fell free to redirect me to forum threads that discuss this. 
Thank you

---

### Post by TheFu on 2023-01-26
Usually it is packages that were manually installed from non-Canonical repos.  So, did you download any .deb files and install them?  Those are the packages that need to be removed.  Then you can patch.  

When you install .deb files directly, you are taking on manual maintenance of that software, so you need a monthly reminder to go see if there is any updates to those packages and to manually install those.  Of course, the how-to guide you followed to find the .deb package file didn't mention this aspect.

Some .deb packages will add a repo/PPA to your PPA list. Those are the nice ones.  Most don't, IME.  Not all PPAs are to be trusted. Be careful.

If you don't have a list of the .deb files manually installed, I don't have a good solution, except to perform a fresh install, restore your backups into that fresh install and load all the programs only use Canonical repos.  If you find any software missing, this time make a note about it then go off and hunt down the snap package or deb package or flatpak for it.  Add a monthly calendar reminder to look for fresh versions of the package if it isn't a snap package.  Snap packages are updated 4x a day, unless you do something to delay it.  I think the longest delay possible is by specifying which day of the week snap packages should be updated.  When I check, mine are set to update on Saturday, at 12.01am Saturday morning, I see the snap packages being updated.  I'd really like them updates at 5am on Saturdays, but that level of control isn't provided. Sigh.

Learn from this.  BTW, you are in what we call "APT Hell".  Avoiding it isn't hard, once you know the cause.

---

### Post by Impavidus on 2023-01-26
Packages can also be held back for phased updates. That's by design. It's somewhat new, so the older guides don't mention this.

How to check? On this site &#8594; [https://people.canonical.com/~ubuntu-archive/phased-updates.html](https://people.canonical.com/~ubuntu-archive/phased-updates.html)
you can see which packages are currently being phased. You can check from the terminal:```
apt-cache policy packagename
```That will tell you if a new version is available and still being phased. For example, right now:```
$ apt-cache policy libinput-bin
libinput-bin:
  Installed: 1.20.0-1ubuntu0.1
  Candidate: 1.20.0-1ubuntu0.2
  Version table:
     1.20.0-1ubuntu0.2 500 (phased 40%)
        500 http://nl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
 *** 1.20.0-1ubuntu0.1 500
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1.20.0-1 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```40% of the Ubuntu users already get this update when checking with apt, the others not.

If you wish, you can force the update:```
sudo apt upgrade packagename
```
Unfortunately, the package manager doesn't make it very clear when a package is held back for phasing and when for a package conflict.

---

### Post by monkeybrain20122 on 2023-01-26
Well I have these packages being held back (22.04)

gnome-remote-desktop, libinput0, libinput-bin, update-notifier, update-notifier-common, python3-software-properties, software-properties-gtk, software-properties-common, ubuntu-advantage-tools. They show up in synaptic but can't be updated.

```
apt -s upgrade
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
The following packages have been kept back:
  gnome-remote-desktop libinput-bin libinput10 python3-software-properties
  software-properties-common software-properties-gtk ubuntu-advantage-tools
  update-notifier update-notifier-common
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.


```
 I think it is upstream issue. I experienced that with other gnome packages earlier. They were updated a few weeks later.

---

### Post by ian-weisser on 2023-01-26
It's not an "upstream issue".

It's Phased Updates, as [[COLOR=#000000]Impavidus[/COLOR]]("https://ubuntuforums.org/member.php?u=1417721") demonstrated.

---

