---
title: "Apt-get update giving 404's for breezy badger repo's"
date: 2007-06-26
forum: General Help
---

### Post by farpoint on 2007-06-26
I installed Kubuntu 5.10 a while back, and have been getting updates until quite recently. The last 3 times I've booted it up, and run apt-get update, I've been getting 404's for the repos listed in /etc/apt/sources.list.

Are the repos no longer available for breezy badger?

I've recently upgraded Debian Sarge to Etch, and also have another Etch install on testing (Lenny), so if I need to upgrade Kubuntu, then so be it. Ive put my current /etc/apt/sources.list below. If someone could tell me the changes I need to make on the URL's to upgrade, I'll have a go.

#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

Thanks for any help.

Nigel. aka farpoint.

---

### Post by Shutdownrunner on 2007-06-26
You have to change all breezy occurences into whatever release you feel like using e.g. 

```

deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

```


should look like this for gutsy
```

deb http://gb.archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu gutsy main restricted

```

You should do this for all the remaining entries.

One remark though. If you're not compiling from source packages, you don't need any of the lines starting with deb-src. You can safely remove them

---

### Post by mikewhatever on 2007-06-26
5.10 is no longer supported, time to upgrade to 6.06 or reinstall.

---

### Post by bapoumba on 2007-06-26
Several members have already reported that hoary and breezy repos have just vanished. They are not there any more, even from a browser.
That these are not longer supported means no more updates, no more security updates. I could not find anywhere that it meant no more repos. I may not have looked enough, but it sounds like a good idea to fill a bug report.

---

### Post by dholl2000 on 2007-07-18
Is it a pre-requisite to upgrade from Breezy before changing 'Breezy' to 'Dapper' or 'Gutsy' in /etc/apt/sources.list?

Or, is it safe (and stable) to install dapper/gutsy packages on a breezy based system?

---

### Post by bapoumba on 2007-07-18
> **dholl2000 said:**
> Is it a pre-requisite to upgrade from Breezy before changing 'Breezy' to 'Dapper' or 'Gutsy' in /etc/apt/sources.list?

Or, is it safe (and stable) to install dapper/gutsy packages on a breezy based system?
It is not recommended to mix up releases in the sources.list.
If you are going to dist-upgrade, you should not skip a release either.

But have a look here:
[http://ubuntuforums.org/showpost.php?p=3026621&postcount=13]("http://ubuntuforums.org/showpost.php?p=3026621&postcount=13")
[http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

So you can, if you prefer to, change your sources.list and keep breezy, provided you are aware of the drawbacks mentioned by fugitsu.

---

