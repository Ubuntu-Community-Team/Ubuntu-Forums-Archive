---
title: "Gimp, PPA: Dependency errors"
date: 2013-02-10
forum: General Help
---

### Post by benhofb on 2013-02-10
Hey guys, I'm new to the forums, and I need some help. 

I was curious to see what Gimp 2.8 was, so I tried to install it on my netbook running Xubuntu 11.10 with Cinnamon interface. 

I originally has Gimp 2.6... 

I went to a few websites and added some other PPAs, once I had done that, I went into Synaptic and updated a few packages. Then, I noticed the package for Gimp was removed in one of the other package updates. 

Stumped, I went into the Terminal and tried to install Gimp from the new repository. (Might I add that it said that the newest version was 2.7.x?) and got multiple dependency errors. 

```
benhofb@ben-AOA150:~$ sudo apt-get install gimp
[sudo] password for benhofb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (>= 2.7.5) but it is not going to be installed
        Depends: libgimp2.0 (<= 2.7.5-z) but it is not going to be installed
        Depends: libgegl-0.0-0 (>= 0.1.3-2) but it is not going to be installed
        Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages.
benhofb@ben-AOA150:~$ 
 
```I am pretty new to Xubuntu/Ubuntu, so If I messed something up completely, I am at a loss. If any one knows how I can fix this error, please let me know. I am a graphics editor for my school newspaper and need my gimp! :cry:

Thanks in advance, 
Benhofb

---

### Post by ibjsb4 on 2013-02-10
You should be able to revert back to 2.6 by using ppa-purge, its in the software center.

[http://www.google.com/search?client=ubuntu&channel=fs&q=ppa+purge+ubuntu&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ppa+purge+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by stinkeye on 2013-02-11
If you don't understand how to use ppa-purge you can use  y-ppa-manager
to purge an added ppa.

Install using terminal...
```
sudo add-apt-repository ppa:webupd8team/y-ppa-manager
sudo apt-get update
sudo apt-get install y-ppa-manager
```

In y-ppa-manager choose "Manage PPAs", then select a ppa to purge and hit the purge button.
If your unsure what's in the ppa, choose the "list packages" button first.
It will show all the packages in the ppa, not just what you have installed

---

### Post by ibjsb4 on 2013-02-11
Hay stinkeye

Are you saying it does the same as ppa-purge, just has a nice GUI?

Guess I need to check this out.

---

### Post by rewyllys on 2013-02-11
You can find easy-to-follow instructions for installing Gimp 2.8 at the following URL:

[http://askubuntu.com/questions/134035/how-do-i-get-gimp-2-8#134039](http://askubuntu.com/questions/134035/how-do-i-get-gimp-2-8#134039)

Good luck!

---

### Post by stinkeye on 2013-02-11
> **ibjsb4 said:**
> Hay stinkeye

Are you saying it does the same as ppa-purge, just has a nice GUI?

Guess I need to check this out.
Yep, it installs ppa-purge as a dependency if it's not already installed.
Also has a handy search in all launchpad ppa's to find a package you may want or need to upgrade.
I've used the search quite often when someones having trouble compiling
from source.

---

### Post by benhofb on 2013-02-11
> **stinkeye said:**
> Yep, it installs ppa-purge as a dependency if it's not already installed.
Also has a handy search in all launchpad ppa's to find a package you may want or need to upgrade.
I've used the search quite often when someones having trouble compiling
from source.

If it installs PPA-Purge as a dependency, why am I getting a dependency error when I try to install it? 
```
benhofb@ben-AOA150:~$ sudo apt-get install y-ppa-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 y-ppa-manager : Depends: ppa-purge but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```So I tried installing just PPA-Purge via terminal and got this:
```
benhofb@ben-AOA150:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ppa-purge : Depends: aptitude but it is not installable
E: Unable to correct problems, you have held broken packages.

```Ugh. This is annoying... Any new suggestions? :confused: Haha, I am just a simpleton wanting to re-install gimp 2.6!

---

### Post by stinkeye on 2013-02-11
> **benhofb said:**
> If it installs PPA-Purge as a dependency, why am I getting a dependency error when I try to install it? 
```
benhofb@ben-AOA150:~$ sudo apt-get install y-ppa-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 y-ppa-manager : Depends: ppa-purge but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```So I tried installing just PPA-Purge via terminal and got this:
```
benhofb@ben-AOA150:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ppa-purge : Depends: aptitude but it is not installable
E: Unable to correct problems, you have held broken packages.

```Ugh. This is annoying... Any new suggestions? :confused: Haha, I am just a simpleton wanting to re-install gimp 2.6!

Try to fix your broken packages first...
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
```

Some third party ppas contain all sorts of packages for testing and whatnot.
It may be ok to install a package from one of these ppas but if you don't then disable the ppa,
you could mess your system up by upgrading packages to packages from that ppa if
you don't check the source of the upgrade when you run an update.
Some ppas contain numerous packages not related to what you were originally trying to install.

eg the aptitude package may depend on a certain version of another program, but you may have inadvertently upgraded that package and now aptitude can't be installed and thus neither can ppa-purge.

---

### Post by benhofb on 2013-02-12
> **stinkeye said:**
> 
eg the aptitude package may depend on a certain version of another program, but you may have inadvertently upgraded that package and now aptitude can't be installed and thus neither can ppa-purge.

Unfortunately, I tried this and was still having the same dependency errors. Any new suggestions? If I have to resort to it, I suppose I would re-install Xubuntu on my netbook, but that is absolutely worst-case scenario. 

I am still unclear if my PPAs are all messed up, therefore messing up my dependencies, or if something else is amiss. :confused:

---

### Post by ibjsb4 on 2013-02-12
You do have your universe sources open?  If not sure about that, please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by benhofb on 2013-02-13
Okay, here we go... 

```
benhofb@ben-AOA150:~$ cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://repository.spotify.com stable non-free
deb-src http://repository.spotify.com stable non-free
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu oneiric main
deb-src http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu oneiric main
benhofb@ben-AOA150:~$ 

```

---

### Post by schragge on 2013-02-13
To install ppa-purge try
```

sudo apt-get clean
sudo apt-get -d --no-upgrade install ppa-purge aptitude
sudo dpkg --force-all -i /var/cache/apt/archives/*.deb

```
You'll get again an error message from apt-get about unmet dependencies, but ppa-purge will be installed nevertheless.

[color=blue]**Update.**[/color] Then do
```

sudo ppa-purge ppa:matthaeus123/mrw-gimp-svn
sudo apt-get upgrade

```

---

### Post by benhofb on 2013-02-13
> **schragge said:**
> To install ppa-purge try
```

sudo apt-get clean
sudo apt-get -d --no-upgrade install ppa-purge aptitude
sudo dpkg --force-all -i /var/cache/apt/archives/*.deb

```


Hmm... Is this what it should be displaying? 
```
benhofb@ben-AOA150:~$ sudo apt-get -d --no-upgrade install ppa-purge aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package aptitude is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'aptitude' has no installation candidate
benhofb@ben-AOA150:~$ sudo dpkg --force-all -i /var/cache/apt/archives/*.deb
dpkg: error processing /var/cache/apt/archives/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/*.deb
benhofb@ben-AOA150:~$ 

```

---

### Post by mc4man on 2013-02-13
There are no current successful gimp builds for 11.10 in that ppa.
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric)
Additionally if there were you would have needed to add 2 other ppa's to get a higher glib & gtk.
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)

So just open Software Sources > Other Software & disable both ppa entries in question.
The reload your sources & see where you stand. (sudo apt-get update

After above if any gimp/babl/gegl packages are installed from that ppa remove, refresh sources again & install gimp for 11.10 from normal 11.10 ubuntu repo

---

### Post by benhofb on 2013-02-13
> **mc4man said:**
> There are no current successful gimp builds for 11.10 in that ppa.
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric)
Additionally if there were you would have needed to add 2 other ppa's to get a higher glib & gtk.
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)

So just open Software Sources > Other Software & disable both ppa entries in question.
The reload your sources & see where you stand. (sudo apt-get update

After above if any gimp/babl/gegl packages are installed from that ppa remove, refresh sources again & install gimp for 11.10 from normal 11.10 ubuntu repo

Huzaah! It works now! I successfully re-installed gimp 2.6! Woot! Thank you everyone who helped, and thank you very much to mc4man! 

I shall now be on my way.:-D

---

### Post by DuckHook on 2013-02-14
As a final note and bit of a warning: adding PPAs cause untold misery to many new users because of the way they break dependencies. Would highly recommend that people stick to the repositories unless:

1. They really know what they are doing and know how to recover from broken dependencies, or
2. Absolutely need an app/functionality that can only be satisfied with a PPA

Another thing about PPAs is increased security risk. Most users do not comb through source code but download binaries. This is a serious risk vector that one must consider much more carefully than most users typically do.

---

