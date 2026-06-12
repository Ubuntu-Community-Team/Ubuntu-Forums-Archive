---
title: "Why doesn't Google Earth install properly on Ubuntu 13.10 using the documented method"
date: 2013-10-26
forum: General Help
---

### Post by Jim_Granite on 2013-10-26
Googling for how to install Google Earth on 64-bit Ubuntu 13.10, I follow the documented method:

[LIST=1]
[*]1. Install the lsb-core package:
[LIST]
[*]$ sudo apt-get install lsb-core 
[/LIST]
  
[*]Obtain the deb file:
[LIST]
[*]$ firefox -url [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html) 
[*]$ wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb) 
[/LIST]
  
[*]Install the deb file:
[LIST]
[*]$ sudo dpkg -i google-earth-stable*.deb 
[*]$ sudo apt-get -f install 
[/LIST]
  
[/LIST]

But, this fails every time, complaining about 32 bit libraries.
But I'm on a 64-bit OS.
What am I doing wrong?
```

$ sudo dpkg -i google-earth-stable*.deb
... 
Selecting previously unselected package google-earth-stable.
(Reading database ... 186607 files and directories currently installed.)
Unpacking google-earth-stable (from google-earth-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-earth-stable:
 google-earth-stable depends on ia32-libs; however:
  Package ia32-libs is not installed.

dpkg: error processing google-earth-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Errors were encountered while processing:
 google-earth-stable

```

I tried installing the missing libraries, but to no avail:
```

$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0

E: Package 'ia32-libs' has no installation candidate

```

---

### Post by Swagman on 2013-10-26
Follow the destructions [**HERE**](http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438)

I had the same issues

Remember to change the username in his code to your own before pressing enter !!

dpkg -b /home/**denis**/Downloads/getfix/google-earth-stable_current_amd64

to...

dpkg -b /home/**yourusername**/Downloads/getfix/google-earth-stable_current_amd64

In all instances.

---

### Post by Jim_Granite on 2013-10-26
> **Swagman said:**
> Follow the destructions [**HERE**]("http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438")

That was it! Thanks! 

These well-documented commands were supposed to work, but they failed on 64-bit Ubuntu 13.10:
$ sudo apt-get install lsb-core
Download the package for "64 bit .deb (For Debian/Ubuntu)"
$ firefox -url [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)
or
$ wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb)

$ sudo dpkg -i google-earth-stable*.deb
$ sudo apt-get -f install

This is the error I got:
```

$ sudo dpkg -i google-earth-stable*.deb
... 
Selecting previously unselected package google-earth-stable.
(Reading database ... 186607 files and directories currently installed.)
Unpacking google-earth-stable (from google-earth-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-earth-stable:
 google-earth-stable depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing google-earth-stable (--install):
 dependency problems - leaving unconfigured
```

So, [based on this thread]("http://ubuntuforums.org/showthread.php?t=2162443"), I then modified the procedure:
$ sudo apt-get install libc6:i386 lsb-core

Download the package for "64 bit .deb (For Debian/Ubuntu)"
$ firefox -url [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)
or
$ wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb)

Right click on the deb file to extract the  google-earth-stable_current_amd64.deb file to a  google-earth-stable_current_amd64 directory.
[ATTACH=CONFIG]247253[/ATTACH]
$ vi ./google-earth-stable_current_amd64/DEBIAN/control
Remove the "Depends" line below, and save that control file.
```

Package: google-earth-stable
Version: 7.1.1.1888-r0
Architecture: amd64
Maintainer: Google Earth Team <google-earth-support@google.com>
Installed-Size: 198273
Pre-Depends: dpkg (>= 1.14.0)
** Depends: lsb-core (>= 3.2), ia32-libs**
Section: net
Priority: optional
Description: Explore, search and discover the planet
 Google Earth lets you fly anywhere to see satellite imagery, 3D  buildings, 3D trees, terrain, Street View, planets and much more.

```

Delete the .deb package:
$ rm ./google-earth-stable_current_amd64.deb

Rebuild the Debian package to create a new google-earth-stable_current_amd64.deb file:
$ dpkg -b ./google-earth-stable_current_amd64

Now install your new Debian package:
$ sudo dpkg -i ./google-earth-stable_current_amd64.deb
```

$ sudo dpkg -i ./google-earth-stable_current_amd64.deb
Selecting previously unselected package google-earth-stable.
(Reading database ... 186916 files and directories currently installed.)
Unpacking google-earth-stable (from .../google-earth-stable_current_amd64.deb) ...
Setting up google-earth-stable (7.1.1.1888-r0) ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Processing triggers for man-db ...

```

Test to see if Google Earth was installed:
$ which google-earth
=> /usr/bin/google-earth

[ATTACH=CONFIG]247254[/ATTACH]

---

### Post by Jim_Granite on 2013-10-26
I haven't tested yet, but, this is what shows up in the terminal when I run google-earth:

$ google-earth
```

[1026/065849:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[1026/065850:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1026/065850:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
... lots of these ... 
$ 

```

EDIT: Google earth seems to work despite these cryptic errors.

---

### Post by Jim_Granite on 2013-10-29
Google earth seems to be working find, even with those errors, so I'm going to mark this as solved.

---

### Post by Jim_Granite on 2013-12-29
Drat. Google Earth just stopped working on Ubuntu 13.10. 
Reinstalling with the latest downloads, but using these instructions failed.
Sigh.

This is back to being unresolved:
- [Where are WORKING instructions for installing Google Earth on 64-bit Ubuntu 13.10? 		]("http://ubuntuforums.org/showthread.php?t=2196312")

---

### Post by mc4man on 2013-12-29
Well if it wasn't installed it wouldn't crash so both threads are 'resolved'.
g-e crashes for a lot of folks using linux, the distro or how you installed doesn't seem to matter.

Here it opens ok, works ok, but I can get it to crash sooner or later exactly as you've seen & so can loads of other users ("Another crash happened while handling crash!"

Note that that extended 'error' message is seen here when opening g-e, doesn't seem to be the cause of the crash, at least not directly.
(if you google search the error you'll find loads of comments about g-e also crashing - ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler

(probably the best solution was to script starting/restarting g-e  until it opens without crashing, typically 5-6 times

---

### Post by Jim_Granite on 2014-01-02
> **mc4man said:**
> 
(probably the best solution was to script starting/restarting g-e  until it opens without crashing, typically 5-6 times

It's not really installed if it doesn't actually work - but - I did try running google-earth from the command line a dozen times, and, on the fifth or so try, it actually worked but I couldn't reproduce the working.
It crashed the other times and is still crashing right away after the splash screen.

The fact it worked once, and didn't work the other 95% of the time is weird.
What's different the one time it worked that the other times didn't have?

Makes no sense.

---

### Post by Jim_Granite on 2014-01-03
Since the solution is to keep trying, here's a documented test of a dozen sequential "google-earth" commands on 64-bit Ubuntu 13.10:
1.
```

$ google-earth
[0103/114759:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114801:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114802:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114805:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0103/114805:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0103/114805:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114805:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114805:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114805:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114809:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114809:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114809:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114809:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!

```

2.
```

$ google-earth
[0103/114947:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114947:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114948:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114948:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114948:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114948:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114948:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114948:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114948:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/114948:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!

```
3.
```

$ google-earth
[0103/115019:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115020:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195021:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195021:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195021:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195021:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195021:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195023:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195023:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195023:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195023:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195023:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195026:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0103/195026:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195026:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195026:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195026:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195026:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!



```
4. This one grayed out, and then, within about 30 seconds, gave a different crash message:
```

$ google-earth
[0103/115052:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115052:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
Segmentation fault (core dumped)



```
5. 
```

$ google-earth
[0103/115222:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115222:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!


```

7.
```

$ !!
google-earth
[0103/115258:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195300:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195303:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195303:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195303:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195303:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195303:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195305:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195305:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195305:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195305:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195305:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195306:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0103/195306:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0103/195306:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195306:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195306:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195306:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/195306:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!

```

8. 
```

$ google-earth
[0103/115334:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/115335:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115335:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115335:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115335:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115335:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115335:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115335:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115335:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115336:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115336:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115336:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115336:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115336:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115336:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115336:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115336:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115338:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115338:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115338:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115338:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115339:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0103/115339:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115339:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115339:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115339:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!

```

9. Again, this one segfaulted:
```

$ !!
google-earth
[0103/115421:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115422:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115423:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115423:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115423:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115423:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
Segmentation fault (core dumped)


```

10.
```

$ google-earth 
[0103/115611:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115611:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115612:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115612:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115612:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115612:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115612:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115612:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115612:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115612:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!

```
11.
```

$ !!
google-earth 
[0103/115637:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/115638:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115638:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115638:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115638:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115638:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115638:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115638:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115638:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115639:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115639:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115639:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115639:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115642:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115642:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115642:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115642:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115643:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115643:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115643:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115643:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115644:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0103/115644:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0103/115644:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115644:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115644:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115644:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!



```
12.
```

$ !!
google-earth 
[0103/115703:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115704:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115707:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0103/115707:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115707:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115707:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115707:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115708:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115708:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115708:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0103/115708:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!



```

The one crash report said "googleearth-bin crashed with SIGSEVV" whatever that means:
[ATTACH=CONFIG]249169[/ATTACH]

---

### Post by mc4man on 2014-01-03
Since you brought this up keep opening g-e & in very short order would get crashes on opening about 80% of the time. 
(so basically abandoned using.

I just put up a 2nd new install (14.04 as that's all I'm interested in, but shouldn't be much different than 13.10

so decided to try something different, used the i386 package instead which will install very easily as it only deps on lsb-core.
After install checked an ldd on google-earth-bin to see what was needed & came up with the below list. On that new install g-e is working fine

So went back to other install, ran the list & then installed the i386 package. **For the moment** all seems well

So if inclined you could try - 
```
sudo apt-get install libc6-i386 libglib2.0-0:i386 libsm6:i386 \
libglu1-mesa:i386 libgl1-mesa-glx:i386 libxext6:i386 \
libxrender1:i386 libx11-6:i386 libfontconfig1:i386 lsb-core
```

Then get the i386 package & install 
(you can remove the amd64 one first or just use dpkg to do a replace, eg.

sudo dpkg -i '/home/doug/Desktop/google-earth-stable_current_i386.deb'

Edit - for 13.10 you may want to check on any of the packages that have 6 or 1 other than libc6-i386 to see if that's the number in 13.10 or is it something else...

---

### Post by ubunt72 on 2014-01-05
mc4man, can you help me?  Or at least try?  :)   I am doing the same thing, trying to get GE to work.  I am not 100% sure, but, I was getting the common error with shared lib files.

"./googleearth-bin: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory"

I think the installation procedure should be, if you are using an amd64 (i.e. 64-bit) version of Ubuntu, to install the i386/32-bit version of GE.   Installing the 64-bit ver. only results in an error msg of saying ia-32 libs is missing but that package has been deprecated (replaced my multiarch).    This is about as much as I understand so far.   

I followed the instructions but I don't understand the above error.   If someone can explain?   I think that is where I am stuck.   I recently removed the i386 package and tried the 64-bit but I knew it wouldn't help (i.e. work).    It's best to use the 32-bit GE and resolve the problem with the shared files - but not sure what to do.   I think it has something to do with the associated lib files with nvidia and MESA.

My video card is nvidia.  

What does this mean?:  "After install checked an ldd on google-earth-bin to see what was needed  & came up with the below list. On that new install g-e is working  fine"

ldd?

I am using Ubuntu 14.04, also.    I installed the latest stable GE (ver. 7).

---

### Post by mc4man on 2014-01-05
> **ubunt72 said:**
> mc4man, can you help me?  Or at least try?  :)   I am doing the same thing, trying to get GE to work.  I am not 100% sure, but, I was getting the common error with shared lib files.

"./googleearth-bin: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory"

I think the installation procedure should be, if you are using an amd64 (i.e. 64-bit) version of Ubuntu, to install the i386/32-bit version of GE.   Installing the 64-bit ver. only results in an error msg of saying ia-32 libs is missing but that package has been deprecated (replaced my multiarch).    This is about as much as I understand so far.   

I followed the instructions but I don't understand the above error.   If someone can explain?   I think that is where I am stuck.   I recently removed the i386 package and tried the 64-bit but I knew it wouldn't help (i.e. work).    It's best to use the 32-bit GE and resolve the problem with the shared files - but not sure what to do.   I think it has something to do with the associated lib files with nvidia and MESA.

My video card is nvidia.  

What does this mean?:  "After install checked an ldd on google-earth-bin to see what was needed  & came up with the below list. On that new install g-e is working  fine"

ldd?

I am using Ubuntu 14.04, also.    I installed the latest stable GE (ver. 7).
Did you install all the packages in the code box in my prior post?
( libGLU.so.1 is provided by libglu1-mesa:i386

---

### Post by ubunt72 on 2014-01-05
Sure.  But, that doesn't help me.  I am reading via various Google search entries and hits with way too many theories.   For e.g., a broken symlink.   Too many potential culprits. :(  I don't see this one getting solved unless someone has a good explanation for the error message.

libglu1-mesa is installed.   I see no entry or candidate for libglu1-mesa:i386.       libgl1-mesa-glx:i386 is installed, though.   I don't get the difference or why one is installed and the other isn't. :(

---

### Post by ubunt72 on 2014-01-05
Hey, I found something that worked!   Perhaps, someone can explain why?  lol

I came across this link:
[http://askubuntu.com/questions/366438/how-to-install-google-earth-64bit-in-ubuntu-13-10-ia32-libs-dependency-error](http://askubuntu.com/questions/366438/how-to-install-google-earth-64bit-in-ubuntu-13-10-ia32-libs-dependency-error)

I tried 'doug's suggestion and copy-pasted so that I installed those packages (some were already installed):

For Ubuntu 13.10/14.04 64 bit installs
  sudo apt-get install libc6-i386 libglib2.0-0:i386 libsm6:i386 \
libglu1-mesa:i386 libgl1-mesa-glx:i386 libxext6:i386 \
libxrender1:i386 libx11-6:i386 libfontconfig1:i386 lsb-core

I already had the i386 package for google earth (installed).  I ran the  sudo apt-get update and closed the terminal.  I tried starting GE (i.e.  click the globe) and voila.  

I guess I was missing a required package that is in the list?  I have no  idea what else it could be.  It must resolve the problem with the  shared lib files?   Or when it looked (upon trying to start GE), it  couldn't find one of the packages?

---

### Post by mc4man on 2014-01-05
> **ubunt72 said:**
> 

I tried 'doug's suggestion and copy-pasted so that I installed those packages (some were already installed):

 I tried starting GE (i.e.  click the globe) and voila.  

I guess I was missing a required package that is in the list?  I have no  idea what else it could be.  It must resolve the problem with the  shared lib files?   Or when it looked (upon trying to start GE), it  couldn't find one of the packages?

That was the intention of the command in the code box - c&p it into a terminal & run. Those packages satisfy all the deps/required libs of g-e i386 on amd64

(Generally speaking for myself - 
anything posted in a code box is intended to be c&p into a terminal & run.
anything in a quote box is for info/comparison purposes.
Occasionally some info doesn't format right in a quote box so will put in a code box, it would/should be obvious that it's for info purposes, not c&p...

---

### Post by mc4man on 2014-01-05
To extend a bit - 
the packages I mentioned are the *min* needed to allow g-e i386 to run on amd64. If you examine the ldd on google-earth-bin you'll still see several not founds.
Whether providing them provides anything positive I haven't looked into as not really a fan of g-e (also possible they are a negative

Installing just one of the qt4 libs will pull in the rest, (& a whole lot more
to see - 
sudo apt-get -s install  libqtgui4:i386

webkit is - libqtwebkit4:i386
libgoogleearth_free.so &  libglobalnew.so have not  pursued..

> $ ldd  /opt/google/earth/free/googleearth-bin
	linux-gate.so.1 =>  (0xf77ac000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf7768000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7722000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7570000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf756b000)
	libgoogleearth_free.so => not found
	libglobalnew.so => not found
	libQtGui.so.4 => not found
	libQtNetwork.so.4 => not found
	libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xf752f000)
	libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf748f000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf735b000)
	libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf7350000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf733c000)
	libGL.so.1 => /usr/lib/i386-linux-gnu/mesa/libGL.so.1 (0xf72e1000)
	libGLU.so.1 => /usr/lib/i386-linux-gnu/libGLU.so.1 (0xf726e000)
	librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf7265000)
	libQtCore.so.4 => not found
	libQtWebKit.so.4 => not found
	libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf717a000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf715d000)
	/lib/ld-lsb.so.3 => /lib/ld-linux.so.2 (0xf77ad000)
	libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf7134000)
	libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf711a000)
	libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xf70f1000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf70d0000)
	libglapi.so.0 => /usr/lib/i386-linux-gnu/libglapi.so.0 (0xf70b9000)
	libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xf70b5000)
	libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf70af000)
	libX11-xcb.so.1 => /usr/lib/i386-linux-gnu/libX11-xcb.so.1 (0xf70ab000)
	libxcb-glx.so.0 => /usr/lib/i386-linux-gnu/libxcb-glx.so.0 (0xf7093000)
	libxcb-dri2.so.0 => /usr/lib/i386-linux-gnu/libxcb-dri2.so.0 (0xf708d000)
	libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0xf7087000)
	libdrm.so.2 => /usr/lib/i386-linux-gnu/libdrm.so.2 (0xf707a000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf7075000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf706e000)

---

### Post by watonzito on 2014-03-02
Gracias, pude instalarlo con éxito. 
Saludos.

---

