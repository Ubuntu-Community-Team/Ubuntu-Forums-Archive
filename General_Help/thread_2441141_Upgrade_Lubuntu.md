---
title: "Upgrade Lubuntu"
date: 2020-04-19
forum: General Help
---

### Post by bigpappajohn1984 on 2020-04-19
LSB_RELEASE -a shows Ubuntu 19.04 - when i try to run
```

sudo apt-get update

```

I get these errors.  What do I need to do so that I can get updates and update to the most recent version?
[IMG]https://ibb.co/R9j8hby[/IMG]
[IMG]https://ibb.co/R9j8hby[/IMG]
[https://ibb.co/R9j8hby](https://ibb.co/R9j8hby)

---

### Post by CatKiller on 2020-04-19
19.04 hasn't been supported since January. Non-LTS releases get nine months.

A fresh install of a supported release or the release candidate of 20.04, which is due to be released on the 23rd, are your options.

---

### Post by bigpappajohn1984 on 2020-04-19
A fresh install?   Meaning wipe what i've got?

---

### Post by CelticWarrior on 2020-04-19
> **bigpappajohn1984 said:**
> A fresh install?   Meaning wipe what i've got?

Pretty much, yes.

Online upgrades can be done while the release is still under support. That's why there's a new release each 6 months and each release has at least 9 months of support (spring editions as in April in even years are LTS - 5 years support).

---

### Post by guiverc on 2020-04-19
Please refer [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

After a release reaches EOL ([http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/) or [https://lubuntu.me/lubuntu-19-04-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-19-04-end-of-life-and-current-support-statuses/)) mirrors will drop the release (so if using a mirror, even country that will require change), and the main archive is moved to `old-releases`.

If you make that change manually (see EOLUpgrades link) you'll be able to ensure you system is fully-upgraded (ie. `sudo apt update && sudo apt full-upgrade` should run without errors), you can reboot if needed (probably better to do that anyway; but it's required for some upgrade eg. kernel upgrades), then you can `do-release-upgrade` or move to the next release (refer [https://wiki.ubuntu.com/EoanErmine/ReleaseNotes](https://wiki.ubuntu.com/EoanErmine/ReleaseNotes) for this step, or even better the Lubuntu documentation being [https://manual.lubuntu.me/stable/D/upgrading.html](https://manual.lubuntu.me/stable/D/upgrading.html)).

A re-install (I'd opt for 'Manual Partitioning', use existing partitions & ensure you don't have format checked) will be far faster, and doesn't cause loses of packages/data (unless you format, your existing software is noted & packages you added are re-installed after install) assuming you didn't format your partitions, but you should definitely backup your data first as it's easy to make mistakes (ie. select format, install to wrong partitions etc).

---

### Post by bigpappajohn1984 on 2020-04-19
> **guiverc said:**
> A re-install (I'd opt for 'Manual Partitioning', use existing partitions & ensure you don't have format checked) will be far faster, and doesn't cause loses of packages/data (unless you format, your existing software is noted & packages you added are re-installed after install) assuming you didn't format your partitions, but you should definitely backup your data first as it's easy to make mistakes (ie. select format, install to wrong partitions etc).

That's my concern is we are using this as a web host and can not loose any sites and need very very very minimal downtime.

and no way of editing
```

/etc/apt/sources.lst

```

---

### Post by TheFu on 2020-04-19
> That's my concern is we are using this as a web host and can not loose any sites and need very very very minimal downtime.

a) Backup.   This is not optional.

b) Don't run servers on non-LTS installs.

c) Never run a release that is out of support.

d) if you need minimal downtime, get another server, set it up as a VM host and run each website either in a VM or some Linux container.  Then you can use the power of VMs to have load balanced upgrades with just a few seconds of downtime.  People stopped running websites directly on HW around 2006.

e) backup again and at least every week going forward, just before you patch the system.

Seems people with backups seldom need to use them, but people without backups are always caught in bad situations wasting many hours trying to fix trivial issues if backups had existed.  i have daily, automatic backups and use them at some level probably 4 times a year. Usually for file corruption or due to an operator error.  Every few years, a HDD will fail. That's when we're really happy we have backups.

What happens if all the data is lost?

---

### Post by guiverc on 2020-04-19
It is also sounds like you're using your Lubuntu (a desktop release) as a *server* system. 

The re-install I mentioned assumes desktop use, as all (desktop) user application store their data in $HOME, however it's common for some server applications to store *config* files in system directories that get wiped by the re-installation method I mentioned, yes they are re-installed using your new release, however modified config files for some server applications can get returned to default. 

I assumed you were talking about a desktop (**Lubuntu is a desktop release**) which doesn't include any server applications which can store data inside system directories.

---

