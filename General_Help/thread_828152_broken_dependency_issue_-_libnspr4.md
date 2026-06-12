---
title: "broken dependency issue - libnspr4"
date: 2008-06-13
forum: General Help
---

### Post by frogeye on 2008-06-13
hi all

havieng  a problem dealing wiht  a dependency issue.  below is the output:

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libnspr4-dev
The following NEW packages will be installed:
  libnspr4-dev
0 upgraded, 1 newly installed, 0 to remove and 0 nolibnspr4-devt upgraded.
2 not fully installed or removed.
Need to get 0B/271kB of archives.
After this operation, 1565kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 254702 files and directories currently installed.)
Unpacking libnspr4-dev (from .../libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.1_amd64.deb (--unpack):
 trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package kompozer-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Greatly  appreciate any suggestions 

tia

frogeye

---

### Post by Rocket2DMn on 2008-06-13
Try deleting that file, cleaning your cache, running update/upgrade, then trying again. As always, use the rm command carefully - it cannot be undone!  Do not deviate from the instructions with it, and if you aren't sure, don't do it and ask for more help.  We are removing the downloaded package file with rm + sudo.
```
sudo rm /var/cache/apt/archives/libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.1_amd64.deb
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
Then continue with what you are trying to install.

---

### Post by wolfen69 on 2008-06-13
try installing the .deb from [Here]("http://packages.ubuntu.com/hardy/amd64/libnspr4-0d/download")

---

### Post by frogeye on 2008-06-13
Thanks for you responses

removing   that file seems to have fixed some issues wiht firefox, but returning to the installation of google gadgets i still need libnspr4-dev, if i am understanding  the situation.   i have libnspr4 od installed and when  i try to install forfm the site wolfen69 linked to i get a message tha i already have a newer package, and it fails to install. looking  in the that reposository i find the dev package but it wont install.

backtracking a bit,  i had been trying to get xulrunner-dev for google gadgets which was giving the message tha ti woudlnt install properly do to an absence fo gtk host - the message :

 Hosts:
  Build gtk host                no
  Build qt host                 no

configure: WARNING: Neither gtk host nor qt host will be built !!!
	      Nothing can be used to run Google Gadgets for Linux.


so when i went back to synaptic and tired ot install xulrunner-dev it pulled the libnspr4-dev package as a dependency and then failed to install the nspr4-dev, althought it showed the xulrunner-dev as installed.

trying to  installthe libnspr4-dev independeantly wiht synaptic gives teh same message:

E: /var/cache/apt/archives/libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.1_amd64.deb: trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package kompozer-dev



 again thanks for you suggestions

---

### Post by joshsmith on 2008-06-13
can you remove the package komposer-dev?
the package manager (synaptic) keeps programs seperate, 2 packages cant both control the same file.
so remove the one you dont need.

if you actually need both, try this command in terminal
sudo apt-get install --force-overwrite libnspr4-dev

---

### Post by Rocket2DMn on 2008-06-13
OK, let's try removing and purging that program
```
sudo apt-get remove --purge libnspr4-dev
```
Then attempt to reinstall your program so it can pick up that dependency, hopefully without conflict.  Are you following directions from somewhere to install google gadgets?  If so, show us the link so we can have a look at it.

---

### Post by frogeye on 2008-06-13
ok i removed kompozer and was able to install zulrunner-dev and libnspr4-dev

but now i still get teh message for the gadgets ./configure output that there is no gtk host.   Here is the ./configure output:

[http://pastebin.com/m1b853dc9](http://pastebin.com/m1b853dc9)


and here are teh google gadget instructions:

[http://code.google.com/p/google-gadgets-for-linux/wiki/HowToBuild](http://code.google.com/p/google-gadgets-for-linux/wiki/HowToBuild)

---

### Post by Rocket2DMn on 2008-06-13
Why don't you try following a guide that is specific to Ubuntu, have a look here - [http://www.ubuntugeek.com/howto-install-google-gadgets-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/howto-install-google-gadgets-in-ubuntu-804-hardy-heron.html)

I can't load your pastebin right now, it just won't open.  However, that guide should get you on your way :)

---

### Post by frogeye on 2008-06-13
> **Rocket2DMn said:**
> Why don't you try following a guide that is specific to Ubuntu, have a look here - [http://www.ubuntugeek.com/howto-install-google-gadgets-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/howto-install-google-gadgets-in-ubuntu-804-hardy-heron.html)

I can't load your pastebin right now, it just won't open.  However, that guide should get you on your way :)

My bad....
yes it  is up and running even as i type these letters.

thanks

frogeye

---

