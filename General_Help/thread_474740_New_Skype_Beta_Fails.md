---
title: "New Skype Beta Fails?"
date: 2007-06-15
forum: General Help
---

### Post by bishop9226 on 2007-06-15
It installed fine on my core duo intel but on my x2 system i get

"error: wrong architecture 'i386'"

so i guess they arent making skype for amd machines now and not telling anyone either?

what the heck

---

### Post by ashz on 2007-06-15
You must force the install, don't worry it wil be fine...

sudo dpkg -i --force-architecture /home/user/package_name.deb

Download the deb file to your home directory, obviously replace "User" with user name and "package_name.deb" with the skype package name.

That should all work, if it does not then also install this..

sudo apt-get install ia32-libs

Thanks to Algyzas on the Skype forums for that answer.

Laters
Ash

---

### Post by mikewhatever on 2007-06-15
I'd say the problem is it's still a beta. i386 should mean 32 bits, I think.

---

### Post by bishop9226 on 2007-06-15
didnt work - see it says it did but all it updated was the conf file!!!!!!!!!!

> 
art@art-desktop:~$ sudo dpkg -i --force-architecture /home/art/skype-1.4.0.74.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 131139 files and directories currently installed.)
Preparing to replace skype 1.4.0.74-1 (using /home/art/skype-1.4.0.74.deb) ...
Unpacking replacement skype ...
Setting up skype (1.4.0.74-1) ...

Configuration file `/etc/dbus-1/system.d/skype.conf'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** skype.conf (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/dbus-1/system.d/skype.conf ...
art@art-desktop:~$ 



---

### Post by bishop9226 on 2007-06-15
it put a skype icon in /usr/share/applications

bvut when i click on it NOTHING happens.  but if i click on my skype launcher on the top of my desktop, it opens the old skype (the command for it is /usr/bin/skype_start)


so it seems that installing this beta version didnt install anything but a new conf file and some icons that dont work!  now when i click on skype under applications > internet - nothing happens.  can someone help me please?

see look i tried it again

> art@art-desktop:~$ sudo dpkg -i --force-architecture /home/art/skype-1.4.0.74.deb
Password:
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 131139 files and directories currently installed.)
Preparing to replace skype 1.4.0.74-1 (using /home/art/skype-1.4.0.74.deb) ...
Unpacking replacement skype ...
Setting up skype (1.4.0.74-1) ...
art@art-desktop:~$ 
art@art-desktop:~$ 




---

### Post by bishop9226 on 2007-06-15
b
u
m
p

---

### Post by ashz on 2007-06-15
did u follow my other instruction??

sudo apt-get install ia32-libs

---

### Post by bishop9226 on 2007-06-15
yes i did that first after the installed failed once.  but even after that it still faiiled because it said it depended on libqt4-gui and libqt4-core being installed.  so then i went to synaptic and installed them.  i tried again after that and got the install output you see here:

> art@art-desktop:~$ sudo dpkg -i --force-architecture /home/art/skype-1.4.0.74.deb
dpkg - warning, overriding problem because --force enabled:
package architecture (i386) does not match system (amd64)
(Reading database ... 131139 files and directories currently installed.)
Preparing to replace skype 1.4.0.74-1 (using /home/art/skype-1.4.0.74.deb) ...
Unpacking replacement skype ...
Setting up skype (1.4.0.74-1) ...

Configuration file `/etc/dbus-1/system.d/skype.conf'
==> File on system created by you or by a script.
==> File also in package provided by package maintainer.
What would you like to do about it ? Your options are:
Y or I : install the package maintainer's version
N or O : keep your currently-installed version
D : show the differences between the versions
Z : background this process to examine the situation
The default action is to keep your current version.
*** skype.conf (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/dbus-1/system.d/skype.conf ...
art@art-desktop:~$ 

now when i click on the icon in the apps -> internet folder, or in the usr/applications folder nothing happens.  but when i click on my old launcher, the old one opens.

---

### Post by bishop9226 on 2007-06-16
anyone?

---

### Post by ashz on 2007-06-19
This is more of a program specific enquiry, as you know I gace you instructions from someone on the Skype forums, so since that didn't work i suggest go over to there.  There must be more people who have had this same issue!!

Laters
Ash

---

