---
title: "Updates fail"
date: 2018-02-24
forum: General Help
---

### Post by tonnes on 2018-02-24
When I run 'sudo apt-get update' I get a bunch of errors like this:

```

Hit:10 https://deb.nodesource.com/node_6.x yakkety InRelease                   
Err:11 http://us.archive.ubuntu.com/ubuntu yakkety Release  


E: The repository 'http://us.archive.ubuntu.com/ubuntu yakkety-proposed Release' does no longer have a Release file.N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```

This is the output of uname -a

uname -a
Linux myusername-system 4.8.0-59-generic #64-Ubuntu SMP Thu Jun 29 19:38:34 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


I haven't been able to update in some time.

---

### Post by #&amp;thj^% on 2018-02-24
Yakkety has reached EOL [s]update[/s] or better  to Install16.04 5 year LTS or Point Version 17.10

---

### Post by deadflowr on 2018-02-24
Yakkety is no longer supported and the archives have been moved.
You'll need to install a new release.
Unfortunately it seems to be rather hard to do a release upgrade from 16.10 (yakkety) (release upgrades are when you upgrade directly from one to another, as opposed to reinstalling a clean install of a new release, if that make sense)

At this point you can install either 16.04 or 17.10.

ninja'd

---

### Post by wildmanne39 on 2018-02-24
Because this version of ubuntu is no longer supported and the repositories have been moved, you need to install a supported version of ubuntu, but you will not be able to upgrade it will have to be a fresh install, I suggest backing up important data first.

---

### Post by Bashing-om on 2018-02-24
tonnes; Uh Huh ..

I be the harbinger if ill news :
> 
<ubottu> Ubuntu Ubuntu 16.10 (Yakkety Yak) was the 25th release of Ubuntu.  Support ended on July 20th, 2017. See !eol and 
               [https://ubottu.com/y/yakkety](https://ubottu.com/y/yakkety)

<ubottu> End-Of-Life is the time when security updates and support for an Ubuntu release stop, see 
               [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) for more information. Looking to upgrade from an EOL release? See 
               [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


[INDENT][INDENT]each good thing, comes to an end
[/INDENT][/INDENT]

---

### Post by tonnes on 2018-02-24
Aha. So there's no way to upgrade? I had assumed I could just upgrade later... I seriously have to fresh install?

---

### Post by deadflowr on 2018-02-24
> **tonnes said:**
> Aha. So there's no way to upgrade? I had assumed I could just upgrade later... I seriously have to fresh install?

A few posters have tried an [EOLUpgrade]("https://help.ubuntu.com/community/EOLUpgrades") from 16.10 but ultimately failed since the next release is also dead.

Best we can offer is to suggest backing up you important data and installing a clean version.
At least to save the pain.

---

### Post by tonnes on 2018-02-24
Yikes. That is... surprisingly bad. I'm used to saying 'god damnit Linux' fairly often, but this is a new one haha.

Alright, well, thanks very much! I'll back up my system and perform a full install I guess.

---

### Post by coffeecat on 2018-02-24
@tonnes, are you aware of the difference between the interim and LTS releases? You really need to keep in mind the very short lifespan of interim release. 16.10, 17.04 and 17.10 were/are all interim releases, supported only for 9 months.

---

### Post by tonnes on 2018-02-24
Yep, I'm aware. I definitely accept some of the blame, but not having reasonable upgrade paths is weak.

---

### Post by DuckHook on 2018-02-24
> **tonnes said:**
> Aha. So there's no way to upgrade? I had assumed I could just upgrade later... I seriously have to fresh install?
It *was* possible to upgrade Yaketty prior to its end-of life, but not after it became obsolete. For reasons I don't understand, the developers decided to nerf the standard method for upgrading obsolete releases in Yaketty. So while such upgrading is possible with Zesty, it doesn't work with Yaketty. Nor do I know of an alternate method.

---

### Post by tonnes on 2018-02-24
Right, I put off upgrading because I hadn't backed up my system and didn't want to lose data. And then it stopped bugging me about it... and apparently they stopped supporting the upgrade path.

---

### Post by deadflowr on 2018-02-24
ftr, this is what you would end up with if you tried an upgrade:
```
do-release-upgrade

Reading cache

Checking package manager

Can not upgrade 

An upgrade from 'yakkety' to 'artful' is not supported with this 
tool. 
```

(running the upgrade through the update-manager will output similar results.)

Basically it tries to hop over the zesty 17.04 dead release, but the tool was never made to do that.

---

### Post by tonnes on 2018-02-24
Hm. Well I'll just have to get a usb drive or dvd or something and try to back up the important stuff.

---

### Post by tonnes on 2018-02-24
I've gone ahead and marked this topic [Solved]. I appreciate the speedy responses, thanks everyone.

---

### Post by slackartist2 on 2018-02-24
> **tonnes said:**
> Hm. Well I'll just have to get a usb drive or dvd or something and try to back up the important stuff.

yea i found it super useful to avoid this strategy rather having a nice twenty gig root partition for my system files and a partition for my home path. possibly a couple extra partitions for var and tmp but that isn't necessary. hope this helps gl

---

