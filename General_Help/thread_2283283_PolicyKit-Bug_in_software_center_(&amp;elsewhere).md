---
title: "PolicyKit-Bug in software center (&amp;elsewhere)"
date: 2015-06-20
forum: General Help
---

### Post by pavel protin on 2015-06-20
hello!

i freshly installed ubuntu on my cubox-i 4 . hurray! i use one of maltegrosse's builds: 
[http://solidrun.maltegrosse.de/~samv/]("http://askubuntu.com/questions/207503/authentication-service-is-not-available-when-installing-idle-using-python-2-7")

at session-start, i get to choose between a huge, sluggish kde, a "pure" xfce and xubuntu. xubuntu is the only one that seems to mostly work and look nice. (i tell you this because i suspect interference between the kde- and the x-parts of the build, without having any good idea about the specifics). what bugs me is the following:

after the first few installs from the software-center (whole applications, which worked), every time i tried to download something (codecs, plugins), i got this:

>  Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.161'}): org.debian.apt.install-or-remove-packages 

i get similar messages from amarok, gmusicbrowser and firefox ("similar" means: they miss some package - do i want to install the plugin? - oh, but i do not have the right...) 
fyi: in "application autostart",the authentication agent is indeed, and always has been, turned on ("/usr/lib/policykit-1-gnome/...)

to no avail, i tried the solutions here:
[http://askubuntu.com/questions/218961/software-cant-be-installed-or-removed-because-the-authentication-service-is-no](http://askubuntu.com/questions/218961/software-cant-be-installed-or-removed-because-the-authentication-service-is-no)
and here:
[http://askubuntu.com/questions/207503/authentication-service-is-not-available-when-installing-idle-using-python-2-7](http://askubuntu.com/questions/207503/authentication-service-is-not-available-when-installing-idle-using-python-2-7)

purge and reinstall of the software manager seemed to work the first time, but only for one download. the second time i tried it, it did nothing. 

help would be much appreciated. i don't have a particulary good grasp of the command lines, so please assume i'm a little slow. thank you!

---

