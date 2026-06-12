---
title: "Package Manager Broken"
date: 2006-11-26
forum: General Help
---

### Post by Homayoon on 2006-11-26
Seems my package manager just don't work. apt-get and synaptic are unable to resolve dependencies. Most of the time, I run into errors like this:

```

libgconf2-dev:
  Depends: libgconf2-4 (=2.12.0-0ubuntu1) but 2.14.0-1ubuntu2 is to be installed

```

apt-get also says something about broken packages. I used to use aptitude in these situations but it doesn't help anymore. Usually it gives a solution and when I confirm just does nothing. Something like this:

```

...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libbonobo2-dev [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  firefox firefox-gnome-support libdvdcss2 mozilla-thunderbird
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

```

This has grown very annoying. I like building from source, but I really don't like to build *EVERY* package from source.

---

### Post by Homayoon on 2006-11-26
Seems I copied the wrong results for aptitude. There are situations which (unlike this one) it suggests installing something but doesn't do that.

---

### Post by RAOF on 2006-11-26
Post your **/etc/apt/sources.list** file.  From the looks of those errors, it seems that it's badly broken, but it'll be easy to fix.

---

### Post by Homayoon on 2006-11-26
Here it is:

```

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
## You may replace "us" with your country code to get the closest mirror.

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free

deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main

```

---

### Post by RAOF on 2006-11-26
Hm.  Well, that doesn't seem too bad.  However, there are a couple of things which might be wrong:

1) You have Universe backports and security updates enabled, but not the actual Universe repository itself (it's on the same line as a comment).

2) You don't have breezy-updates Universe on there.  You could try adding "universe multiverse" to the end of each of the breezy-updates lines.

Do those two things, run an **sudo apt-get update** and try again?

And finally:  *Breezy*?? :p

---

### Post by David Corrales on 2006-11-27
The problem are these lines:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

Compiz/Beryl and XGL/AIGLX repos for dapper changed a -lot- of core packages in order to be useful. I also got some stupid breakage because of it. Since you're using Breezy it's even easier to break things by adding a repo from a different version. And THAT repo to boot =/
Try to force versions back (I couldn't), if not... did you use a separate partition for home :)?

---

### Post by Homayoon on 2006-11-27
I'm just now figuring out more of the problem. Actually I copy&pasted most of my sources.list and (shame on me!), I'm actually using dapper. The fact is that I installed a lot of packages using this sources.list. I know little about apt, but I suppose this should have caused installing a lot of packages with wrong versions. I tried replacing "breezy" with "dapper" and retrying. Many things changed but there are still many errors (probably because of the many packages I installed before that). Is it so? If so, is there *ANY* way I can recover?

---

### Post by RAOF on 2006-11-27
You could try:
1) Make sure your sources.list is correct.  Maybe even remove any non-Cannonical sources (plf, beerorkid, etc)
2) **sudo apt-get update; sudo apt-get dist-upgrade**.  If you haven't got any packages newer than Dapper, that should upgrade/install your packages to the Dapper versions
3) (possibly) Add the non-Cannonical repositories back in.

If the dist-upgrade doesn't work, try posting the errors here, and we'll do our best to help!

---

### Post by Homayoon on 2006-11-28
I tried that. When I ran "apt-get dist-update" I got a huge bunch of errors. I took a look at the errors and found out most of them are python related (python is one of the badly broken packages that has caused many programs not to run). I had already built a separate python in /mypy/bin, so I added this at the beginning of PATH and this time everything went on without any errors. But I still have problems. For example, I tried to install libgnome2-dev from Synaptic and I got this:

```

libgnome2-dev:
  Depends: libgnome2-0 (=2.12.0.1-0ubuntu1) but 2.14.1-0ubuntu2 is to be installed
 Depends: libbonobo2-dev but it is not going to be installed
 Depends: libgconf2-dev but it is not going to be installed
 Depends: libgnomevfs2-dev but it is not going to be installed

```

Many other packages get similar error messages. I tried aptitude too, but it doesn't do anything. It does suggest solutions, but nothing is actually installed.

---

### Post by Homayoon on 2006-11-28
Is *reinstall* the only option I have? It's too windowsy a solution! I hate it. :-|

---

### Post by RAOF on 2006-11-28
**Everything** in your sources.list says "dapper"?  Because this error:

> **Homayoon said:**
> ...
```

libgnome2-dev:
  Depends: libgnome2-0 (=2.12.0.1-0ubuntu1) but 2.14.1-0ubuntu2 is to be installed
 Depends: libbonobo2-dev but it is not going to be installed
 Depends: libgconf2-dev but it is not going to be installed
 Depends: libgnomevfs2-dev but it is not going to be installed

```
...

tells me that apt is trying to install the libgnome2-dev package from Breezy.

---

