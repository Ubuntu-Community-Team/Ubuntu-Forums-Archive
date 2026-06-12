---
title: "issue with python3-aptdaemon.gtk3widgets"
date: 2019-03-29
forum: General Help
---

### Post by ray field on 2019-03-29
Been having assorted Python issues am trying to debug -- squashed one this morning, another one remains: neither Synaptic nor Software Updater can deal with python3-aptdaemon.gtk3widgets at the moment:

```
Depends: python3-aptdaemon (=1.1.1+bzr982-0ubuntu16) but 1.1.1+bzr982-0ubuntu14 is to be installed
```

does this mean something is stuck on 14.04? how do I fix? (have tried sudo apt-get -f install, apt clean, etc.)

thanks --

---

### Post by deadflowr on 2019-03-29
Do you have any 3rd party packages or repos added or installed?
python3-aptdaemon-1.1.1+bzr982-0ubuntu14 is the correct version required for the python3-aptdaemon.gtk3widgets  package.
(At least for Ubuntu 16.04)
Not sure where the blah-16 version is from.
(Is it in proposed repo maybe?)

---

### Post by #&amp;thj^% on 2019-03-29
It's been so long since I have used trusty, but make sure package gir1.2-vte-2.91 is installed.
```
apt-cache policy gir1.2-vte-2.90 
```

---

### Post by deadflowr on 2019-03-29
> **1fallen said:**
> It's been so long since I have used trusty, but make sure package gir1.2-vte-2.91 is installed.
```
apt-get policy gir1.2-vte-2.91 
```

I think you meant apt policy instead of apt-get policy.

But with that in mind what about
```
apt policy python3-aptdaemon
apt policy python3-aptdaemon.gtk3widgets
```
what do those output?

---

### Post by #&amp;thj^% on 2019-03-29
> **deadflowr said:**
> I think you meant apt policy instead of apt-get policy.


See how long it's been. :)
But on trusty I think it works as:
```
apt-cache policy
```
I only test about 5 different distros, and all have different syntax usage Ubuntu is the only Debian based I test.
Thanks deadflowr, corrected my code text in my above post.

---

### Post by ray field on 2019-03-29
> **deadflowr said:**
> Do you have any 3rd party packages or repos added or installed?


quite a few -- in fact a candidate for the cause of this is Jonathon F's Python 3.6 at [https://launchpad.net/~jonathonf/+archive/ubuntu/python-3.6](https://launchpad.net/~jonathonf/+archive/ubuntu/python-3.6)

I can't remember why I installed it, think maybe because I was already having issues with Python.

---

### Post by ray field on 2019-03-29
> **1fallen said:**
> It's been so long since I have used trusty, but make sure package gir1.2-vte-2.91 is installed.
```
apt-cache policy gir1.2-vte-2.90 
```

```
raphael@Swann-Ubuntu:~$ sudo apt-cache policy gir1.2-vte-2.90
[sudo] password for raphael: 
gir1.2-vte-2.90:
  Installed: (none)
  Candidate: (none)
  Version table:

```

so, tried installing:

```
raphael@Swann-Ubuntu:~$ sudo apt install gir1.2-vte-2.90
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gir1.2-vte-2.90 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gir1.2-vte-2.90' has no installation candidate
```

---

### Post by ray field on 2019-03-29
> **deadflowr said:**
> ...
But with that in mind what about
```
apt policy python3-aptdaemon
apt policy python3-aptdaemon.gtk3widgets
```
what do those output?

```
raphael@Swann-Ubuntu:~$ apt policy python3-aptdaemon
python3-aptdaemon:
  Installed: 1.1.1+bzr982-0ubuntu14
  Candidate: 1.1.1+bzr982-0ubuntu16
  Version table:
     1.1.1+bzr982-0ubuntu16 500
        500 http://shaggytwodope.github.io/repo ./ Packages
 *** 1.1.1+bzr982-0ubuntu14 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status

```

and likewise

```
raphael@Swann-Ubuntu:~$ apt policy python3-aptdaemon.gtk3widgets
python3-aptdaemon.gtk3widgets:
  Installed: 1.1.1+bzr982-0ubuntu14
  Candidate: 1.1.1+bzr982-0ubuntu16
  Version table:
     1.1.1+bzr982-0ubuntu16 500
        500 http://shaggytwodope.github.io/repo ./ Packages
 *** 1.1.1+bzr982-0ubuntu14 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by #&amp;thj^% on 2019-03-29
> **ray field said:**
> 
so, tried installing:

```
raphael@Swann-Ubuntu:~$ sudo apt install gir1.2-vte-2.90
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gir1.2-vte-2.90 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gir1.2-vte-2.90' has no installation candidate
```
Well now I'm confused then, you stated "does this mean something is stuck on 14.04? how do I fix?
But appears your using Xenial 16.04, and if this is case try "gir1.2-vte-2.91"  
Or just search using:
```
apt search gir1.2-vte
```

---

### Post by ray field on 2019-03-29
> **1fallen said:**
> Well now I'm confused then, you stated "does this mean something is stuck on 14.04? how do I fix?
But appears your using Xenial 16.04, and if this is case try "gir1.2-vte-2.91"  
Or just search using:
```
apt search gir1.2-vte
```

tbh, I have only a dim understanding of what we are trying to do here, but -- apologies for the earlier confusion: what I meant to say was that there might be version conflict since I think this 16.04 may be upgraded from 14.04 (may be, I really can't remember).

at any rate:

```
raphael@Swann-Ubuntu:~$ apt search gir1.2-vte
Sorting... Done
Full Text Search... Done
gir1.2-vte-2.91/xenial,now 0.42.5-1ubuntu1 amd64 [installed]
  GObject introspection data for the VTE library

```

but

```
raphael@Swann-Ubuntu:~$ sudo apt install gir1.2-vte-2.91
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gir1.2-vte-2.91 is already the newest version (0.42.5-1ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
raphael@Swann-Ubuntu:~$ 

```

---

### Post by #&amp;thj^% on 2019-03-30
Your showing 3 not upgraded, If it were me I would remove Those PPA's and get as close to stock install as possible.
let's see if everything is installed correctly then:
```

dpkg -l python3
```
Mine just as an EXAMPLE:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-===================================
ii  python3        3.7.3-1      amd64        interactive high-level object-orien

```

And:
```
dpkg -l python3-aptdaemon
```
EXAMPLE on mine:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version                Architecture Description
+++-=================-======================-============-======================
ii  python3-aptdaemon 1.1.1+bzr982-0ubuntu21 all          Python 3 module for 

```
And last one:
```
dpkg -l python3-aptdaemon.gtk3widgets
```
What we want is the last bit of info: "ii" this means it's a clean install with no problems.

---

### Post by monkeybrain20122 on 2019-03-30
> **ray field said:**
> quite a few -- in fact a candidate for the cause of this is Jonathon F's Python 3.6 at [https://launchpad.net/~jonathonf/+archive/ubuntu/python-3.6](https://launchpad.net/~jonathonf/+archive/ubuntu/python-3.6)

I can't remember why I installed it, think maybe because I was already having issues with Python.

Not knowing really how to solve your problem. But just want to point out that this is generally a bad idea that may break your system. If you need different versions of python the standard way is to get [anaconda]("https://www.anaconda.com/"). Personally I don't like it much since it installs a bunch of other stuffs I don't need and as a result subject to rather strict version control. I install python3.7 (I compiled it myself) in my Ubuntu16.04 box locally and use a script to set the environmental variables which I run when using python3.7, otherwise it is completely separated from the system, it is by far the most satisfying solution.

---

### Post by deadflowr on 2019-03-30
> Not knowing really how to solve your problem. 
Yep, me too.
I do see the -aptdaemon packages are coming from a 3rd party repo (shaggytwodope?)
I'm not sure what relation that has to what's going on overall, but maybe you can try pinning the package versions
[https://help.ubuntu.com/community/PinningHowto]("https://help.ubuntu.com/community/PinningHowto")
Probably set the Ubuntu repo version as the priority over the shaggy repo version.

Again though, not sure if that will solve anything or cause more issues.
But it's something to ponder.
If it does cause more harm, no problem, just delete the created files and entries and start over again.

(Unfortunately this feels like a rabbit hole since it's not clear what the various PPAs and 3rd party repos require,
and it's not clear how far far deep it goes)

---

### Post by ray field on 2019-04-03
thanks for the thoughtful and helpful responses.

I'm on the road at the moment (using a nice little Asus 302 Chromebook running GalliumOS on which Pythons are nicely tamed) but will remove that PPA and start from scratch. I have a nagging suspicion the reason I used the PPA to begin with was a permissions issue with pip -- at any rate, more than once I've found myself wishing someone had written a script to check on Python versions, files, and libraries -- the only problem being, naturally, that it would run best on Python.

anyway, will check again when I'm at the big box, thanks once again.

---

### Post by ray field on 2019-04-13
thanks, guys. all I needed to do was purge that PPA.

```
raphael@Swann-Ubuntu:~$ dpkg -l python3
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python3        3.5.1-3      amd64        interactive high-level object-ori
raphael@Swann-Ubuntu:~$ dpkg -l python3-aptdaemon
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python3-aptdae 1.1.1+bzr982 all          Python 3 module for the server an
raphael@Swann-Ubuntu:~$ dpkg -l python3-aptdaemon.gtk3widgets
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python3-aptdae 1.1.1+bzr982 all          Python 3 GTK+ 3 widgets to run an

``` 

I will come clean with what I figured out was the problem: I thought I was having a hard time with sncli, a nice little CLI Simplenote client which just wouldn't seem to update. I convinced myself the problem was somehow with pip3: in fact, the issue was I'd been running it off a shell script in a folder in my home directory, while pip3 had been dutifully updating it in /usr/local/bin... much obliged for the patient & understanding responses.

---

