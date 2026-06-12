---
title: "Tons of apt-get problems"
date: 2005-08-20
forum: General Help
---

### Post by erikpiper on 2005-08-20
Hey! On my new (24 HRS old) Ubuntu installation, I have had a few problems, most easily fixed. However Apt-get is now acting very scewy. See below. Sources list, and lots of errors.

First, sources.list

> 
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe multiver$deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe mult$
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted

deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports) hoary-backports main universe multiverse re$deb [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports) hoary-extras main universe multiverse restr$deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/


Now, the error I get from sudo apt-get update. Not really an error, but it hangs on the last line. Have to exit terminal to get it to quit.

> erik@ubuntuLP:/etc/apt$ sudo apt-get update
Password:
Ign [http://ubuntu.nooms.de](http://ubuntu.nooms.de) hoary/ Release.gpg
Ign [http://ubuntu.nooms.de](http://ubuntu.nooms.de) hoary/ Release
Ign [http://ubuntu.nooms.de](http://ubuntu.nooms.de) hoary/ Packages
Hit [http://ubuntu.nooms.de](http://ubuntu.nooms.de) hoary/ Packages
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary Release.gpg
Get:1 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-updates Release.gpg [189B]
Get:2 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-security Release.gpg [189B]
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary Release
Get:3 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-updates Release [16.8kB]
Get:4 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-security Release [16.9kB]
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/main Packages
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/restricted Packages
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/universe Packages
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/multiverse Packages
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/main Sources
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/restricted Sources
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/universe Sources
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/multiverse Sources
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-updates/main Packages
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-updates/restricted Packages
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-updates/main Sources
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-updates/restricted Sources
Get:5 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-security/main Packages [38.7kB]
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-security/restricted Packages
Get:6 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-security/main Sources [11.2kB]
Hit [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary-security/restricted Sources
99% [Connecting to ftp2.caliu.info (147.83.29.16)

Now, reload in Synaptic. 3 screenshots. In order. If you cannot read the text, click to zoom in (1024/768)

[http://img396.imageshack.us/my.php?image=se16mv.png](http://img396.imageshack.us/my.php?image=se16mv.png)

[http://img396.imageshack.us/my.php?image=se27po.png](http://img396.imageshack.us/my.php?image=se27po.png)

[http://img396.imageshack.us/my.php?image=se34bo.png](http://img396.imageshack.us/my.php?image=se34bo.png)

And the full text from last screens textbox.
> 
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)






Thanks all!

---

### Post by heimo on 2005-08-20
That backports mirror has at the moment some problems (seen someone else with same problem). Other mirrors:
[http://backports.ubuntuforums.org/url.php]("http://backports.ubuntuforums.org/url.php")

---

### Post by erikpiper on 2005-08-20
[QUOTE=heimo]That backports mirror has at the moment some problems (seen someone else with same problem). Other mirrors:
[http://backports.ubuntuforums.org/url.php]("http://backports.ubuntuforums.org/url.php")[/QUOTE]
 Thanks!

---

