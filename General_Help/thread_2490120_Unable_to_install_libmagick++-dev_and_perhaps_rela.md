---
title: "Unable to install libmagick++-dev and perhaps related unmet dependencies"
date: 2023-08-23
forum: General Help
---

### Post by psyctc on 2023-08-23
I am running Ubuntu 22.04.2 LTS updated daily, apt-get update and then apt-get ungrade say "0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade."
However, for some weeks now I have got "unmet dependencies" trying to install libmagick++-dev (which I need to get the R package magick which depends on that package).  I get this:

```
root@Clevo2:/media/chris/Clevo_SSD2/Data/MyR/R/distill_blog/test2/_posts# apt-get install libmagick++-dev
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libcairo2-dev : Depends: libfontconfig1-dev (>= 2.2.95)
                 Depends: libfreetype6-dev (>= 2.1.10)
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.72.4-0ubuntu1) but 2.72.4-0ubuntu2.2 is to be installed
                  Depends: libglib2.0-bin (= 2.72.4-0ubuntu1)
                  Depends: libglib2.0-dev-bin (= 2.72.4-0ubuntu1)
 libmagickcore-6.q16-dev : Depends: libfreetype6-dev
 libwmf-dev : Depends: libfreetype-dev but it is not installable
E: Unable to correct problems, you have held broken packages.
```

apt-cache policy libmagick++-dev gives me this:

```
libmagick++-dev:
  Installed: (none)
  Candidate: 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3+esm2
  Version table:
     8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3+esm2 500
        500 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security/main amd64 Packages
        500 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security/main i386 Packages
     8:6.9.11.60+dfsg-1.3build2 500
        500 http://mirror.infomaniak.ch/ubuntu jammy/universe amd64 Packages
        500 http://mirror.infomaniak.ch/ubuntu jammy/universe i386 Packages
```

Is anyone else seeing this?  How can I explore it further and solve it?!

TIA,

Chris

---

### Post by Xian on 2023-08-24
I'd first try to run the install command with aptitude. 
It may offer different solutions to resolve the dependency issues. 

Install aptitude:
$ sudo apt-get install aptitude

Then:
$ sudo aptitude install libmagick++-dev


You can also install synaptic
$ sudo apt-get install synaptic

Then run the synaptic progam and goto:
 Edit - Fix Broken Packages

---

### Post by psyctc on 2023-08-25
Thanks Xian, I had tried that but aptitude didn't do any better than apt.  It turned out that I had pointed my Ubuntu repostitories to mirror.infomaniak.ch using the "nearest server" option and that mirror has become out of synch (I assume) with the main Ubuntu server.  When I switched back to the main server and ran apt-get update and apt-get upgrade that pulled a very large number of updates after which I could do the install of libmagick++-dev and then of the R magick package that depends on libmagick++-dev.

---

### Post by ajgreeny on 2023-08-25
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

