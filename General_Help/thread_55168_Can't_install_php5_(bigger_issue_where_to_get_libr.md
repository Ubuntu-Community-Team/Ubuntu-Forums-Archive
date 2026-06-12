---
title: "Can't install php5 (bigger issue: where to get libraries?)"
date: 2005-08-07
forum: General Help
---

### Post by greyhound4334 on 2005-08-07
Hi All,

I'm new to ubuntu, but have some experience with debian.

I ran into a problem earlier today trying to get a required version of libc6 in the official ubuntu repositories ([http://ubuntuforums.org/showthread.php?p=291010#post291010](http://ubuntuforums.org/showthread.php?p=291010#post291010))

I was able to work around that problem by getting a different version of java, but relief was only short-lived.

I've run into the same problem again, this time trying to install php5.

```
root@delbert:/ # apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: apache2-common (>= 2.0.54-4) but 2.0.53-5ubuntu5.2 is to be installed
                       Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

```

Once again, the problem is that I need a version of libc6 more current than seems to be available anywhere in the ubuntu repositories (I've got universe and multiverse in my sources.list; I posted the full sources.list in the thread referred to above if anyone wants to see it).

So the question remains: what should I do about getting that libc6?  Is it dangerous for me to go get it from one of the debian repositories?  I'm trying very hard to avoid creating an unstable system, like I ended up with in my last debian system which mixed stable, unstable, and testing.  So I'm nervous about going and adding this libc6 from outside the ubuntu world.  

Any advice greatly appreciated!

---

### Post by DJ_Max on 2005-08-07
I wouldn't touch libc, and do not use Debian repositories. Ubuntu is not Debian.

Where is the package libapache2-mod-php5 from, I don't think it's in the Ubuntu repositories (may be wrong). If so, thats why your getting errors, because Debian packages are built against Debian. You want to build PHP5 from source.

---

### Post by greyhound4334 on 2005-08-07
DJMax,

You're right.  I pulled php5 in from a debian repos.

I had trouble building it on my old (debian) system, which is why, I guess, I thought about downloading the .deb instead of building it.  Will follow your advice and go try to build it.

Thanks for the caution about staying away from debian repositories.

---

### Post by DJ_Max on 2005-08-08
[QUOTE=greyhound4334]DJMax,

You're right.  I pulled php5 in from a debian repos.

I had trouble building it on my old (debian) system, which is why, I guess, I thought about downloading the .deb instead of building it.  Will follow your advice and go try to build it.

Thanks for the caution about staying away from debian repositories.[/QUOTE]
 If you need help installing PHP5 let me know. It's fairly easy. I believe there's a how-to around, I'll try ti find it.

---

### Post by greyhound4334 on 2005-08-09
Thanks for the help.

At this point, things have unravelled a little bit.  I'm about ready to give up on this machine, which was unstable (I attributed it to my mixed debian install, but I'm now convinced it's the machine), so I'm focused on building a new one.  Probably won't get back to trying to get my ubuntu environment working until I get the machine built in a couple of weeks.  I"ll check back then.

john

---

