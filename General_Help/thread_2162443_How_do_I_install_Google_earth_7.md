---
title: "How do I install Google earth 7?"
date: 2013-07-14
forum: General Help
---

### Post by borgward on 2013-07-14
How do I install Google earth 7?

I uninstalled 6.2.2....

Synaptic package manager does not list Google Earth 7

---

### Post by kc1di on 2013-07-14
follow the instructions on [this page.]("https://help.ubuntu.com/community/GoogleEarth")

---

### Post by borgward on 2013-07-15
I now have 7.1.1.1871 installed, but all pictures come up blank. Pictures layer is selected. After I right click on the blank picture I get 404. "That&#8217;s an error.

The requested URL / was not found on this server. That&#8217;s all we know."

---

### Post by kc1di on 2013-07-16
That sounds like a networking problem not a problem with the program itself.  I have had no problems with it here. 
But maybe someone else will chime in with a cure.

---

### Post by Impavidus on 2013-07-16
The problem is really there, I experience it too. Everything works, except the pictures, which never work. The problem first occured when GE6 stopped working. Most functions came back when changing to version 7, but the pictures didn't (the 360 degree panoramas do work though). I'm running 7.1.1.1871, using server kh.google.com. As everything else works, I suspect a problem with Google Earth itself or one of their servers. If it's a server side problem it explains why only some people have problems. I can't find an option to change to a different server. I suspect GE automatically selects one nearby.

Maybe helpful to compare with others:
```
$ nslookup kh.google.com
Server:        127.0.0.1
Address:    127.0.0.1#53

Non-authoritative answer:
kh.google.com    canonical name = kh.l.google.com.
Name:    kh.l.google.com
Address: 74.125.136.136
Name:    kh.l.google.com
Address: 74.125.136.190
Name:    kh.l.google.com
Address: 74.125.136.93
Name:    kh.l.google.com
Address: 74.125.136.91

```

---

### Post by borgward on 2013-07-16
Funny thing is that I can switch from earth to mars view and display those pictures.

---

### Post by wheelie207 on 2013-10-17
I just posted on another thread about not being able to install google earth because of a (ia-32 libs) error after I upgraded to 13.10 from 13.04 and the google earth is 64-bit.
Don't know if I should of done this or not, but I'm not sure why 13.10 removed my google earth in the first place.
Could it be the upgradfe or should I have done a total reinstall of ubuntu.

Harold

---

### Post by stidmatt on 2013-10-18
I also have the same problem. I have no idea why it isn't working, though it does work on my phone. It worked on Google Earth 6 and have seen that many people are having trouble with Google Earth 7. Would it be possible to downgrade, and where would I get the file to reinstall the old version? Unless if downgrading won't fix the problem.

---

### Post by scouser73 on 2013-10-18
Hey stidmatt, if you are using an x64 computer then please follow these instructions.  Thanks goes to [**[COLOR="#FF0000"]mc4man[/COLOR]**]("http://ubuntuforums.org/member.php?u=320715") for these instructions in getting Google Earth to work.

This is just a temporary workaround until Google Earth no longer required ia32-libs.

**_Google Earth Build Package_**

Download Google Earth x64 .DEB

Open Terminal, Copy & Paste Following Command And Press Enter

```
sudo apt-get install libc6:i386 lsb-core
```

Open Downloads Folder

Right Click On Google Earth .DEB Package & Select Extract Here

Click On Debian Folder

Right Click on Control & Select Open In Gedit

Remove The Whole Line Containing

**[COLOR="#FF0000"]Depends: lsb-core (>= 3.2), ia32-libs[/COLOR]**

Now Click Save, & Exit Control File

Now Delete The Original Google Earth .DEB Package You Downloaded

Create A Folder called getfix, Now Move The Extracted Google Earth Folder Into The getfix Folder

Now You Are Going To Rebuild The Google Earth .DEB Package

Open Terminal, Copy & Paste Following Command & Press Enter

```
dpkg -b /home/denis/Downloads/getfix/google-earth-stable_current_amd64
```

Once You Have Done That, Back In Terminal Copy & Paste The Following Command

```
sudo dpkg -i /home/denis/Downloads/getfix/google-earth-stable_current_amd64.deb
```

The Repackaged Google Earth Will Now Be Installed.

---

### Post by Smask on 2013-10-19
The problem with Panoramio photos not loading: 
GE ships with Qt libs that doesn't work properly. Amirpli posted a bunch of modified libs (64-bit) on GE product forum. This fixes photos and other stuff that requires javascript. Plus it fixes GE general crash happiness (having a crash while handling crash). [COLOR=#ff0000]*** Notice, these libs won't work with 32-bit GE [/COLOR][COLOR=#ff0000]*** [/COLOR]Now we'll have to wait for the official fix. [GE 7.1.2.2041 arrived]("https://support.google.com/earth/answer/40901?hl=en"), but still no fixes.

Amirpli's libs:
[https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit?usp=sharing](https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit?usp=sharing)

Extract these into the folder getfix/opt/google/earth/free before you rebuild the .deb file. Replacing the files in the plugins/imageformat folder might need write permission. That patchlib file is only required if you use debian so you can delete it.

Those new libs need libfreeimage3 to work
```
sudo apt-get install libfreeimage3
```
Instead of removing the depends line in DEBIAN/control, you can replace "ia32-libs" with "libfreeimage3".
Build the deb file and install

---

### Post by Swagman on 2013-10-25
Many thanks for this fix. 

As a trucker I use Google Earth heaps and was a bit disappointed it had been uninstalled after upgrading to 13:10
Ubuntuforums to the rescue ... *again* !

---

### Post by spiral2 on 2013-10-25
I installed google earth for ubunto/Linux 64bit and it says its installed correctly, however there is no launch icon & I can't find a way to open it.

I am new to ubuntu, and am not using it because I'm a computer genius, but because of political reasons re B** G****, so its a very steep learning curve .....

Having spent time researching this problem, most answers are to paste various bits of script into a "terminal"........ this is where I make an idiot of myself & ask where & what is this "terminal" (ubuntu 12.04) as I'm at my wits end [IMG]http://www.jonrb.com/emoticons/headache.gif[/IMG]

---

### Post by BlinkinCat on 2013-10-25
> **spiral2 said:**
> this is where I make an idiot of myself & ask where & what is this "terminal" (ubuntu 12.04) as I'm at my wits end [IMG]http://www.jonrb.com/emoticons/headache.gif[/IMG]

Hi,

Find terminal at Ctrl, Alt, T

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Cheers

---

### Post by spiral2 on 2013-10-25
> **BlinkinCat said:**
> Hi,

Find terminal at Ctrl, Alt, T

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Cheers

A little box appeared bottom right, thats the first time I've got that, [IMG]http://www.jonrb.com/emoticons/hi5.gif[/IMG]

---

### Post by spiral2 on 2013-10-25
So....I got the box & pasted;
sudo apt-get install lsb-core

From; [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Not knowing what to do once its pasted in I pressed enter, and nothing happened other than the box disappeared [IMG]http://www.jonrb.com/emoticons/headscratch.gif[/IMG]

---

### Post by spiral2 on 2013-10-26
[IMG]http://www.jonrb.com/emoticons/bump.gif[/IMG]

Having realised that there is an Alt key as well as an Alt Gr key [IMG]http://www.jonrb.com/emoticons/Doh2.gif[/IMG] I got the proper box to post code into...so then I followed the steps suggested above.

Google earth then appeared & worked perfectly, for all of five seconds....then this appeared in a terminal box

[PHP][1026/110015:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[1026/110015:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[/PHP]

What does this mean & what do I need to do to fix it ??

---

### Post by Jim_Granite on 2013-10-26
> **wheelie207 said:**
> not being able to install google earth because of a (ia-32 libs) error after I upgraded to 13.10 
I have the same error that Harold got, except mine is on a brand new Ubuntu 13.10 and described over here:
* [Why doesn't Google Earth install properly on Ubuntu 13.10 using the documented method]("http://ubuntuforums.org/showthread.php?t=2183733") * 

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

Right click on the deb file to extract the   google-earth-stable_current_amd64.deb file to a   google-earth-stable_current_amd64 directory.
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
 Google Earth lets you fly anywhere to see satellite imagery, 3D   buildings, 3D trees, terrain, Street View, planets and much more.

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
> **spiral2 said:**
> What does this mean & what do I need to do to fix it ??

I have no idea why, but, this is what I get when I run Google Earth now that I've finally installed it:
$ google-earth
```

[1026/065849:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[1026/065850:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1026/065850:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
... lots of these ... 
$ 

```

---

### Post by stidmatt on 2013-10-26
I just found the solution to the problem. I downloaded Ubuntu restricted extras (Flash, fonts, and other goodies) and Google Earth now works perfectly.

---

### Post by stidmatt on 2013-10-26
Never mind, it worked for the first location but then didn't work... what a strange problem.

---

### Post by j-lbarbry on 2013-10-27
Hello !
I tried several solutions, including those described above (deleting a line in the control file and rebuilding package, but I still get the same error message: ***error****** while loading shared libraries: libGL.so.1***
If I try to link some ligGL.so to /usr/lib/googleearth I get :  ***error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64***
regards

---

### Post by Smask on 2013-10-28
> **j-lbarbry said:**
> Hello !
I tried several solutions, including those described above (deleting a line in the control file and rebuilding package, but I still get the same error message: ***error****** while loading shared libraries: libGL.so.1***
If I try to link some ligGL.so to /usr/lib/googleearth I get :  ***error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64***
regards

Did you use the Amirpli libs on 32-bit Google Earth? They only works on 64-bit GE.

---

### Post by j-lbarbry on 2013-10-28
No, in my usr/lib32 directory I have only libnss_xxx, libz.so and gconv directory.
I have many problems with 13.10 (cups, virtualBoxGuestAddition ...)

---

### Post by robenroute on 2013-11-01
> **scouser73 said:**
> Hey stidmatt, if you are using an x64 computer then please follow these instructions.  Thanks goes to [**[COLOR="#FF0000"]mc4man[/COLOR]**]("http://ubuntuforums.org/member.php?u=320715") for these instructions in getting Google Earth to work.
.
.
.
The Repackaged Google Earth Will Now Be Installed.

> **Smask said:**
> The problem with Panoramio photos not loading: 
.
.
.
Build the deb file and install

Thanks guys! Your instructions got everything in working order again. Plain and simple! Many thanks again.

---

### Post by trash1464 on 2013-11-01
> **scouser73 said:**
> Hey stidmatt, if you are using an x64 computer then please follow these instructions.  Thanks goes to [**[COLOR=#FF0000]mc4man[/COLOR]**]("http://ubuntuforums.org/member.php?u=320715") for these instructions in getting Google Earth to work.

This is just a temporary workaround until Google Earth no longer required ia32-libs.

**_Google Earth Build Package_**

Download Google Earth x64 .DEB

Open Terminal, Copy & Paste Following Command And Press Enter

```
sudo apt-get install libc6:i386 lsb-core
```

Open Downloads Folder

Right Click On Google Earth .DEB Package & Select Extract Here

Click On Debian Folder

Right Click on Control & Select Open In Gedit

Remove The Whole Line Containing

**[COLOR=#FF0000]Depends: lsb-core (>= 3.2), ia32-libs[/COLOR]**

Now Click Save, & Exit Control File

Now Delete The Original Google Earth .DEB Package You Downloaded

Create A Folder called getfix, Now Move The Extracted Google Earth Folder Into The getfix Folder

Now You Are Going To Rebuild The Google Earth .DEB Package

Open Terminal, Copy & Paste Following Command & Press Enter

```
dpkg -b /home/denis/Downloads/getfix/google-earth-stable_current_amd64
```

Once You Have Done That, Back In Terminal Copy & Paste The Following Command

```
sudo dpkg -i /home/denis/Downloads/getfix/google-earth-stable_current_amd64.deb
```

The Repackaged Google Earth Will Now Be Installed.

This worked like a charm for me, running 13.10 - 64 bit many thanks!

---

### Post by sascha-baumeister on 2013-11-24
This is the only sollution i found that really worked for me, thanks a lot!

Note that I had to temporarily allow write access to the two ".so"-files within the opt/google/earth/free/plugins/imageformats" Folder in order to overwrite them with the patched replacements (using "sudo chmod a+w <filename>" to grant it, and "sudo chmod a-w <filename>" once the patches were copied).

Also, note that I had to change ownership of the files and directories in "getfix" to "root" (using "sudo chown -R root:root *") before building the deb-File, in order to avoid warnings from the Ubuntu Software Center during installation because of a misbuilt deb-File - this might however not happen if you install the deb-File using dpkg.

The resulting google-earth installation seems to run pretty stable in earth view under Ubuntu Gnome 13.10 (64bit). However, I noticed that it consistently crashes when I try to switch from earth to moon view. Any ideas what might cause that?

---

### Post by Smask on 2014-02-15
Never mind, my post borks searches

---

### Post by erhollowell on 2014-02-17
What do I do if, after running the first line the .deb package trys to install without me doing anything and after watching the downloads and install run you find that you don't have any googleearth icon or any files in your download page, what can you do? Please remember that some of us already have botched installs on our systems which do not work but interfer with further attempts to install.

My last attempt went: [following entering password for sudo]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb-core is already the newest version.
libc6:i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Yet I don't have Googleearth.

---

### Post by Smask on 2014-02-18
> **erhollowell said:**
> What do I do if, after running the first line the .deb package trys to install without me doing anything and after watching the downloads and install run you find that you don't have any googleearth icon or any files in your download page, what can you do? Please remember that some of us already have botched installs on our systems which do not work but interfer with further attempts to install.

My last attempt went: [following entering password for sudo]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb-core is already the newest version.
libc6:i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Yet I don't have Googleearth.

You clicked run instead of save the file? If so, the browser saves it to /tmp and run it from there. It will stay there until you exits or restarts the browser, or reboot the computer. After that, the file is gone and you have to download it again.

---

### Post by Herman on 2014-03-08
Thank you scouser73 & Smask, your helpful instructions post #9 and Post #10 worked for me :)

---

### Post by loftwyr on 2014-08-06
I'm doing these instructions and getting this error:

```

Setting up google-earth-stable (7.1.2.2041-r0) ...
xdg-icon-resource: size argument must be numeric
Try 'xdg-icon-resource --help' for more information.
xdg-desktop-menu: file '/opt/google/earth/free/google-earth.desktop' does not exist
Processing triggers for menu (2.1.47ubuntu1) ...

```

What am I doing wrong?

---

### Post by RogerDavis on 2014-11-05
When attempting to rebuild the package, I get the following error.  

dpkg-deb: error: failed to open package info file `/home/roger/Downloads/getfix/google-earth-stable_current_amd64/DEBIAN/control' for reading: No such file or directory
roger@roger-desktop:~$ 

The control file is most assuredly present.  

What's wrong?

Ubuntu 14.04

=======================

I got past the above, GE will now attempt to start.  Out of 10 tries, it might successfully start once, and it still won't show the panorama pictures!!!  Just a blank white display box.  

This is version google-earth-stable_current_amd64, freshly downloaded from Google and modified by removing line "Depends: lsb-core (>= 3.2), ia32-libs" from the control file and rebuilding.

This is the error info:
-------------------------------------------------------------------------
roger@roger-desktop:~$ google-earth
[1105/220407:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[1105/220407:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for kh.google.com failed err=-8181
[1105/220407:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for [www.google.com](www.google.com) failed err=-8181
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for accounts.google.com failed err=-8181
[1105/220407:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for support.google.com failed err=-8181
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220407:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1105/220408:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for storage.googleapis.com failed err=-8181
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1105/220408:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.


Another crash happened while handling crash!
------------------------------------------------------------------------------------

---

### Post by Impavidus on 2014-11-06
Sounds familiar. I fixed it by installing the 32 bits version and some libraries: [http://ubuntuforums.org/showthread.php?p=12890642#post12890642](http://ubuntuforums.org/showthread.php?p=12890642#post12890642)
The pictures still don't work. That has something to do with bad libraries build into Google Earth. I read it can be fixed by manually installing a patch, but I never bothered.

---

### Post by RogerDavis on 2014-11-06
OK, can you tell me where is info on the patch for 32 bit to make pictures and other features work?

---

### Post by Impavidus on 2014-11-06
I saw it mentioned in this post: [http://ubuntuforums.org/showthread.php?t=2196304&page=3&p=12892342#post12892342](http://ubuntuforums.org/showthread.php?t=2196304&page=3&p=12892342#post12892342)
That is about 64 bit though, which works for some, but not for all.

---

### Post by RogerDavis on 2015-05-01
See below for the working answer :

[https://productforums.google.com/forum/?utm_medium=email&utm_source=footer#!msg/maps/yP-kFwxfVJM/rXSpxRQdEFAJ](https://productforums.google.com/forum/?utm_medium=email&utm_source=footer#!msg/maps/yP-kFwxfVJM/rXSpxRQdEFAJ)

---

