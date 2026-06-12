---
title: "[URGENT] glibc-2.3.2.ds1-20ubuntu14"
date: 2005-10-10
forum: General Help
---

### Post by Vinze on 2005-10-10
A lot of programs depend on "locales", but when I try to install it I get the following:

> sudo apt-get install locales
Password:
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
  locales: Depends: glibc-2.3.2.ds1-20ubuntu14
E: Broken packages


So probably locales depends on glibc-2.3.2.ds1-20ubuntu14, but somehow I can't install that? Who knows the answer, because it is really annoying now being able to install something!

---

### Post by mlomker on 2005-10-10
Are you using Breezy?  Try replacing your sources.list with the one on [this message.]("http://www.ubuntuforums.org/showpost.php?p=397497&postcount=114")

---

### Post by Vinze on 2005-10-10
[QUOTE=mlomker]Are you using Breezy?  Try replacing your sources.list with the one on [this message.]("http://www.ubuntuforums.org/showpost.php?p=397497&postcount=114")[/QUOTE]

No, I still have Hoary.

---

### Post by mlomker on 2005-10-10
[QUOTE=Vinze]No, I still have Hoary.[/QUOTE]

Then you can use the list on the [ubuntuguide]("http://www.ubuntuguide.org/#extrarepositories") if you haven't done that already.  You should skip the Mirrormax entries because they aren't being used anymore.

---

### Post by Vinze on 2005-10-11
[QUOTE=mlomker]Then you can use the list on the [ubuntuguide]("http://www.ubuntuguide.org/#extrarepositories") if you haven't done that already.  You should skip the Mirrormax entries because they aren't being used anymore.[/QUOTE]

Well, these are my current reprositories:

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
#deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
#deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ 
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

  # debian (experimental)
  # deb [http://ftp.fr.debian.org/debian/](http://ftp.fr.debian.org/debian/) ../project/experimental main contrib non-free
  # deb-src [http://ftp.fr.debian.org/debian/](http://ftp.fr.debian.org/debian/) ../project/experimental main contrib non-free

  #debian (testing)
  #deb [ftp://ftp.debian.org/debian/](ftp://ftp.debian.org/debian/) testing main 
  #deb-src [ftp://ftp.debian.org/debian/](ftp://ftp.debian.org/debian/) testing main 

#deb [http://themind.altervista.org/debian](http://themind.altervista.org/debian) unstable main
#deb-src [http://themind.altervista.org/debian](http://themind.altervista.org/debian) unstable main 

#deb [http://debian.plentyfact.net/packages/](http://debian.plentyfact.net/packages/) ./


So I don't guess that will matter much...

---

### Post by mlomker on 2005-10-11
> So I don't guess that will matter much...

Looks the same.  Now that I re-read your message I'm wondering how you could have removed the locales package?  Are you sure that it isn't already installed?

```

sudo dpkg-reconfigure locales

```

It looks like the file is in the universe repo and is [here as well]("http://packages.ubuntu.com/hoary/doc/glibc-doc")

---

### Post by Vinze on 2005-10-11
[QUOTE=mlomker]Looks the same.  Now that I re-read your message I'm wondering how you could have removed the locales package?  Are you sure that it isn't already installed?

```

sudo dpkg-reconfigure locales

```

It looks like the file is in the universe repo and is [here as well]("http://packages.ubuntu.com/hoary/doc/glibc-doc")[/QUOTE]

How I removed it? Well, that's a long story...

When I did sudo dpkg -reconfigure locales I got the following: > sudo dpkg-reconfigure locales
Password:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/sbin/dpkg-reconfigure: locales is broken or not fully installed


Plus, I don't think installing it from a .deb would help.

---

### Post by mlomker on 2005-10-11
> Plus, I don't think installing it from a .deb would help.

Why do you say that?  Apt just downloads the .debs and installs them for you--like most things in linux it's just a front-end script for an old program (dpkg).  

```

sudo apt-get install --reinstall locales

```

Have you tried the -f switch?

```

sudo apt-get update
sudo apt-get -f upgrade

```

---

### Post by Vinze on 2005-10-11
With -f:

> sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


With reinstall:
> sudo apt-get install --reinstall locales
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
  locales: Depends: glibc-2.3.2.ds1-20ubuntu14
E: Broken packages


Depackaging locales:

> sudo dpkg -i /home/vincent/bin/Installers/locales_2.3.2.ds1-20ubuntu13_all.deb
Password:
Selecting previously deselected package locales.
(Reading database ... 97697 files and directories currently installed.)
Unpacking locales (from .../locales_2.3.2.ds1-20ubuntu13_all.deb) ...
dpkg: dependency problems prevent configuration of locales:
 locales depends on glibc-2.3.2.ds1-20ubuntu13; however:
  Package glibc-2.3.2.ds1-20ubuntu13 is not installed.
dpkg: error processing locales (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales


---

### Post by mlomker on 2005-10-11
> Depackaging locales:

Did you try to upgrade glibc at some point?  That's 'not good'.  Everything on the box depends upon it.  

The best option is probably to try to upgrade to Breezy, but [back up]("http://www.ubuntuforums.org/showpost.php?p=361622&postcount=4") your files first.

---

### Post by Vinze on 2005-10-11
I think you mean libc6. Well, it's complaining about glibc-2.3.2.ds1-20ubuntu13, but that's a virtual package provided by libc6. Libc6 though is already installed...  I don't know what to do! HELP!

---

### Post by mlomker on 2005-10-11
> I think you mean libc6.

That's what that package is.  There are a [number of posts]("http://ubuntuforums.org/showthread.php?t=42227") about that.    You're actually replying quicker than I finish editing my posts.  My recommendation is in my last post.  You're welcome to wait for a second opinion, of course.

---

### Post by Vinze on 2005-10-11
Sorry, it's just that I want to install some programs that need that so I reply quick :D 

I just downloaded linux-patch-ubuntu-2.6.10, that doesn't mean it's Breezy is it?  Breezy doesn't have a final release right? Because I do want to be sure it's totally stable because at right now I can't afford to get the computer crashed...

---

### Post by mlomker on 2005-10-11
> I do want to be sure it's totally stable because at right now I can't afford to get the computer crashed...

Your computer is already crashed.  Breezy is being released on Thursday, so it's pretty close.

If you have a fast Internet connection then you can edit your /etc/apt/sources.list to say Breezy instead of Hoary and then follow [these instructions.]("http://www.ubuntuforums.org/showthread.php?p=393315#post393315")  The alternative is to download or order a CD and upgrade from the CD using a similar process, but adding the CD-rom to your sources.list first.

I'd strongly recommend backing up what you can't afford to lose, though.  With your machine in the state that it is I'm not sure how it'll go for you.  You could end up having to format/reinstall.

I did work with someone a couple days ago that had the same problem and the Breezy upgrade worked for them.

---

### Post by Vinze on 2005-10-11
If it's released on Thursday, then can't I better wait till I can update it automatically?

And at least my computer is still working now so I can do my schoolwork...

---

### Post by mlomker on 2005-10-11
> If it's released on Thursday, then can't I better wait till I can update it automatically?


I don't know...you seem to be in a hurry to install something.  It won't automatically update--you'll just have to go through the same steps on Friday or whenever convenient.

---

### Post by Vinze on 2005-10-11
But then loads of people will do it, right? Indeed, I do really really want to install something, but I rather wait a bit than have the risk of my computer crashing...

---

### Post by mlomker on 2005-10-11
You seem to be under the misimpression that I'm trying to talk you into upgrading.  I'm just trying to help you with your problem, and that's one possible solution.

---

### Post by Vinze on 2005-10-11
Nah, I don't mind, it's just that I wonder whether it is risky to upgrade now or if I'd better wait till Thursday.

---

### Post by mlomker on 2005-10-11
[QUOTE=Vinze]Nah, I don't mind, it's just that I wonder whether it is risky to upgrade now or if I'd better wait till Thursday.[/QUOTE]

I upgraded on Sunday and I use my laptop for work (working hard right now...not).  If you want perfect then you could wait a few weeks.  A lot of people are running it already but the big rush will be the first few weeks after the official release.

---

### Post by Vinze on 2005-10-11
Well, I read a story about someone who couldn't get his computer to start up after he  upgraded, and had to hack his way through. Now, I don't really feel like doing so, and I don't know how much better Breezy is. Plus, I'm not sure if upgrading will solve the problem, though I think it might.

---

