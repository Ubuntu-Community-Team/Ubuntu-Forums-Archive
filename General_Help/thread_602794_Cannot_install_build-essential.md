---
title: "Cannot install build-essential"
date: 2007-11-04
forum: General Help
---

### Post by ctsdownloads on 2007-11-04
I have checked five threads on this issue. Installing  build-essential is not happening on three different Gutsy boxes. Here is what I have tried:

> matt@matt-laptop:~$ sudo apt-get install build-essential
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

OK, so I do a:

> matt@matt-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

No joy again. So off to using Aptitude:

> matt@matt-laptop:~$ gksudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libc6-dev 
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libstdc++6-4.1-dev linux-libc-dev patch 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libstdc++6-4.1-dev linux-libc-dev 
  patch 
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 7934kB of archives. After unpacking 31.9MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu9) but 2.6.1-1ubuntu10 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.6.1-1ubuntu10 (now) -> 2.6.1-1ubuntu9 (gutsy)]
libc6-i686 [2.6.1-1ubuntu10 (now) -> 2.6.1-1ubuntu9 (gutsy)]

Score is 116

Accept this solution? [Y/n/q/?] 

I choose yes.

And then the waiting starts as NOTHING happens and it sits there with a blinking cursor below the yes or no question - no hard drive activity, little CPU activity. ](*,)

---

### Post by nick_h on 2007-11-04
It looks like you upgraded your libc6 from gutsy-proposed.  To install build-essential you need to enable gutsy-proposed again and install libc6-dev.  You can then disable proposed again.

After this build-essential should install.

---

### Post by ctsdownloads on 2007-11-04
Oh believe me, repos were disabled way down after this. It was in there and nothing was going to remove it without some brute force. This is the thread that got me through it.
[http://ubuntuforums.org/showthread.php?t=565391](http://ubuntuforums.org/showthread.php?t=565391)

I had to CD to the directory where the older deb package of libc6 was downloaded from this site:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.5-0ubuntu14_i386.deb&md5sum=93f5e50c41abfaeac5963a448b9881e0&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.5-0ubuntu14_i386.deb&md5sum=93f5e50c41abfaeac5963a448b9881e0&arch=i386&type=main)

So basically, downloaded to /home/, then:

matt@matt-desktop:~$ cd /home/
matt@matt-desktop:/home$ sudo dpkg --force-downgrade -i libc*.dev

The terminal tossed out some warnings, but it worked. Things are back to where they ought to be and that other repo is commented out. :)

Thanks

---

### Post by zvacet on 2007-11-05
O.K. I see that you solve your problem,but for possible future situations when you get this message

> E: Broken packages

Go to the** synaptic>edit>fix broken packages**

---

### Post by ctsdownloads on 2007-11-05
> Go to the synaptic>edit>fix broken packages

That was one of the first three things I did. Trust me, it did nothing, so I would not rely on it too much. :)

---

