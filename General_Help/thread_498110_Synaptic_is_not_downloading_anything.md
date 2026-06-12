---
title: "Synaptic is not downloading anything"
date: 2007-07-10
forum: General Help
---

### Post by nanbudh on 2007-07-10
Hi,
I am having a problem for past some months. Everytime i login as administator account Gnome showa a yellow bubble informing me "119 updates available". Now the problem is when i try to download something it shows no  progress and after a long time would give a message that it "failed to fetch" stuff from such and such source. I have trying to download any bittorent client (tried Azerues, bittornado etc)for 15 days now but the synaptic just stands their withou showing any progress. please help; here is my /etc/apt/sources.list:

[I][I][FONT="Courier New"]# 
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted



deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

##
##
##added by shavin on 12 sep 06 12:19 am from site [http://ubuntulondon.wordpress.com/2006/08/21/needed-extras/](http://ubuntulondon.wordpress.com/2006/08/21/needed-extras/)

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## WINE
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

#PLF Repositories
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
##addition done by shavin on 13 May 2007, 6:14 from [http://wxpython.org/download.php#prerequisites](http://wxpython.org/download.php#prerequisites)
##for wxpython
# wxPython APT repository at wxcommunity.com
deb [http://wxpython.wxcommunity.com/apt/ubuntu/dapper](http://wxpython.wxcommunity.com/apt/ubuntu/dapper) /
deb-src [http://wxpython.wxcommunity.com/apt/ubuntu/dapper](http://wxpython.wxcommunity.com/apt/ubuntu/dapper) /
##
##end of addition done by shavin
[/FONT][/I][/I]

---

### Post by Vajra Vrtti on 2007-07-11
It looks i little confuse to me. For instance, i think it should be
> deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe
but the first line is missing.
I don't know if this is a problem, but you also have **in** and **gb** repositories mixed.
I suggest you to use **[source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/")** to create a new sources.list.

---

### Post by nanbudh on 2007-07-11
i added the missing line and then gave the command:
sudo apt-get update on the terminal and i got this output:

```
shavin@ubuntu:~$ sudo apt-get update
Err http://wxpython.wxcommunity.com  Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://archive.canonical.com dapper-commercial Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://gb.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://archive.ubuntu.com dapper Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://wine.budgetdedicated.com dapper Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://in.archive.ubuntu.com dapper Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://packages.freecontrib.org dapper Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://gb.archive.ubuntu.com dapper Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://in.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://gb.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Err http://in.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://packages.freecontrib.org/plf/dists/dapper/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://wxpython.wxcommunity.com/apt/ubuntu/dapper/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg  Could not connect to 128.0.0.1:8080 (128.0.0.1), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
```


and about the "in" word i think "in " probably stands for india, my location.

There is another thing which is bothering me. When i installed ubuntu(dapper 6.06) i think i probably installed i386 version cos as i recall amd64 version did not install succesfully(my processor is AMD64, Asus x series motherboard)-(is it possible?) ...anyways..now when i go to System>Administration>Device Manager and click on "processor" it shows this:-
Vendor- Unknown
Device-Unknown
Status-Status
Bus Type-Unknown
Device Type- Processor
Capabilities- Processor
Should i be concerned about this??

---

### Post by Nythain on 2007-07-11
delete the country codes in and gb from the repos that have them so they look more like this:
deb [http://archive.ubuntu.com](http://archive.ubuntu.com)

from your timeout and unable to reach errors it looks like the in and gb repos are either having troubles or are non existant anymore

---

### Post by Vajra Vrtti on 2007-07-11
Use **[source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/")**.

---

### Post by nanbudh on 2007-07-14
Thanks for all your help guys, i found out what was wrong. It turns out that some time back i must have fiddled with Network proxy(System>Preferences>Network Proxy) and set it to manual 128.0.0.1 whereas i connect to internet directly. I set it to Direct and voila! the Synaptic came back to life again.Even the weather applet i added to desktop some time back and which was not working, started to show the weather data. Ha Ha.. Needless to add It felt goood:)
Hope this post helps somebody in a similar situation.

---

