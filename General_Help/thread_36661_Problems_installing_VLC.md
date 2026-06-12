---
title: "Problems installing VLC"
date: 2005-05-24
forum: General Help
---

### Post by mira-ceti on 2005-05-24
Hi All,

I have been trying to install vlc in Hoary using the  apt-get install vlc command  I have the universe repositories available but I get the following errors;

apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: liba52-0.7.4 but it is not installable
       Depends: libid3tag0 (>= 0.15.0b) but it is not installable
       Depends: libmad0 (>= 0.15.1b) but it is not installable
E: Broken packages

The libraries mentioned in the message cannot be installed using apt-get.  Am I missing something here or are the libraries no longer available?

---

### Post by SGC on 2005-05-24
Add the following lines to your /etc/apt/sources.list:

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main

Then from the terminal do the following:

# sudo apt-get update
# sudo apt-get install wxvlc libdvdcss2

---

### Post by mira-ceti on 2005-05-25
Thanx for the idea, unfortunately it did not work, here is the output I got.


sudo apt-get update
Password:
Ign [http://download.videolan.org](http://download.videolan.org) sid Release.gpg
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Ign [http://download.videolan.org](http://download.videolan.org) sid Release
Ign [http://download.videolan.org](http://download.videolan.org) sid/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release
Ign [http://download.videolan.org](http://download.videolan.org) sid/main Sources
Get:5 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://download.videolan.org](http://download.videolan.org) sid/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
Hit [http://download.videolan.org](http://download.videolan.org) sid/main Sources
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release [16.8kB]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release.gpg
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release.gpg
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging Release.gpg
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging Release.gpg
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/universe Sources
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/restricted Sources
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging/universe Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging/restricted Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging/universe Packages
Get:7 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging/restricted Packages
Get:8 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages [10.8kB]
Get:9 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages [13.3kB]
Get:10 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages [20B]
Get:11 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages [20B]
Get:12 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages [2131B]
Get:13 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages [1642B]
Get:14 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages [20B]
Get:15 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages [3959B]
Get:16 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging/main Packages [7413B]
Get:17 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging/universe Packages [8105B]
Get:18 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging/multiverse Packages [430B]
Get:19 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports-staging/restricted Packages [375B]
Get:20 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging/main Packages [20B]
Get:21 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging/universe Packages [1051B]
Get:22 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging/multiverse Packages [20B]
Get:23 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras-staging/restricted Packages [20B]
Get:24 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg [189B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Fetched 84.1kB in 18s (4575B/s)
Reading package lists... Done
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems


sudo apt-get install wxvlc libdvdcss2
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wxvlc: Depends: vlc (= 0.8.1-1ubuntu7) but it is not going to be installed
E: Broken packages
bevan@ubuntu1:~$ sudo apt-get update
Ign [http://download.videolan.org](http://download.videolan.org) sid Release.gpg
Ign [http://download.videolan.org](http://download.videolan.org) sid Release
Ign [http://download.videolan.org](http://download.videolan.org) sid/main Packages
Ign [http://download.videolan.org](http://download.videolan.org) sid/main Sources
Hit [http://download.videolan.org](http://download.videolan.org) sid/main Packages
Hit [http://download.videolan.org](http://download.videolan.org) sid/main Sources
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release [16.8kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 34.1kB in 9s (3656B/s)
Reading package lists... Done
bevan@ubuntu1:~$ sudo apt-get install wxvlc libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wxvlc: Depends: vlc (= 0.8.1-1ubuntu7) but it is not going to be installed
E: Broken packages

---

### Post by SGC on 2005-05-25
It seems that apt-get try to download the package from ubuntu repository hence (0.8.1-1ubuntu7) instead of downloading it from VLC repository. I think if you comment the ubuntu repositories temporally then apt-get update. You will be able to downloading it without the unmet decencies

---

### Post by mira-ceti on 2005-05-25
Thanks again, but it looks like it is just not going to work for me, unfortunately.  Here is what I get now.


 sudo apt-get update
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Ign [http://download.videolan.org](http://download.videolan.org) sid Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release
Ign [http://download.videolan.org](http://download.videolan.org) sid Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Sources
Ign [http://download.videolan.org](http://download.videolan.org) sid/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/restricted Sources
Ign [http://download.videolan.org](http://download.videolan.org) sid/main Sources
Hit [http://download.videolan.org](http://download.videolan.org) sid/main Packages
Hit [http://download.videolan.org](http://download.videolan.org) sid/main Sources
Fetched 2B in 3s (1B/s)
Reading package lists... Done
bevan@ubuntu1:~$ sudo apt-get install wxvlc libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wxvlc: Depends: vlc (= 0.7.0-1) but it is not going to be installed
         Depends: libimlib2 but it is not installable
         Depends: libwxgtk2.4 (>= 2.4.2.4) but it is not installable
E: Broken packages

---

### Post by SGC on 2005-05-25
I just tried the following and it works for me

First remove VLC reprpositories that you add prevoiusly, then download libwxgtk2.5.3 from here: [http://packages.ubuntu.com/hoary/libs/libwxgtk2.5.3](http://packages.ubuntu.com/hoary/libs/libwxgtk2.5.3)

Install it with the following command:
dpkg - i libwxgtk2.5.3.deb

then do the following apt-get:
apt-get install wxvlc vlc libhal0 dbus-1


I hope , it will works for you.

---

### Post by mira-ceti on 2005-05-25
Thanks yet again, but as you can see it still does not want to install.  :(




 dpkg -i libwxgtk2.5.3_2.5.3.2ubuntu4_i386.deb
Selecting previously deselected package libwxgtk2.5.3.
(Reading database ... 59909 files and directories currently installed.)
Unpacking libwxgtk2.5.3 (from libwxgtk2.5.3_2.5.3.2ubuntu4_i386.deb) ...
Setting up libwxgtk2.5.3 (2.5.3.2ubuntu4) ...

root@ubuntu1:/home/bevan # apt-get install wxvlc vlc libhal0 dbus-1
Reading package lists... Done
Building dependency tree... Done
libhal0 is already the newest version.
dbus-1 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: liba52-0.7.4 but it is not installable
       Depends: libdvbpsi2 but it is not installable
       Depends: libdvdplay0 but it is not installable
       Depends: libflac4 but it is not installable
       Depends: libmad0 (>= 0.15.0b) but it is not installable
  wxvlc: Depends: libimlib2 but it is not installable
         Depends: libwxgtk2.4 (>= 2.4.2.4) but it is not installable
E: Broken packages

---

### Post by SGC on 2005-05-25
Search and install the following packages on synaptic:
liba52
liblibmad0 
dvdplay0
libimlib2 
libimlib2 

As for libdvbpsi2 and libflac4 I couldn't find them in ubuntu repositories, so try search for a repository that has them using the following page: 
[http://www1.apt-get.org/search.php](http://www1.apt-get.org/search.php)

After installing all dependencies do apt-get install wxvlc vlc libhal0 dbus-1

---

### Post by lorap on 2005-05-25
hi.
listen friend, once you've decided install vlc install all plugins.
this's the way to install it via synaptic:

before you install it via synaptic you've to add it to the repositories's list.
let's do it right now so after i get home the only thing you'd have to do just install the only package.
first of all open System-->Computer Management-->Synaptic Package Manager.
after you get it open go to the Setting-->Repositories.
once you get the repositories window open press Advanced button and mark all checkboxes possible except "download only upgradable packages" then press Ok.
after what you'll need to wait until the update process completes. the repositories' window'll close at the end of the process so you'll be prompted again the synaptic window.
press the Reload button and wait until the reload process completes.
now you're able to install the VLC player.
press the Search button and write in VLC then press Ok.
once you have the package found out mark it and all its plugins for install and then press Apply button. wait until install process completes after what close the synaptic.
have a nice day.
pavel

---

### Post by raz on 2005-05-25
[QUOTE=lorap]once you get the repositories window open press Advanced button and mark all checkboxes possible except "download only upgradable packages" then press Ok.[/QUOTE]

Can't find the 'Advanced' button, care to help?

TIA,

-r

---

### Post by mira-ceti on 2005-05-26
Thanks SGC and lorap for your help.  It does not seem to matter what i do, vlc will not install, I constantly get dependency problems with the libraries, so at this point I just give up. I will not be able to use Ubuntu to watch avi files.  I have  problems with xine & gxine too, neither will play sound, though sound works perfectly in other apps.  Totem plays the files and also has sound but its sound is so far out of sync that its not watchable.

Thanks again, I really do appreciate your efforts.

---

### Post by mira-ceti on 2005-05-26
Hi Guys,

I guess i wasn't quite truthfull when I said "I give up".  I have been trying various things.  Anyway   IT NOW WORKS PERFECTLY !!  :smile:  I installed the  Hoary Updates Binary in Synaptic -> Repositories and tried again to install VLC and it worked !

Thanks again for all your help I do appreciate it !

---

### Post by psychosaif on 2006-12-19
Can you please point out how u did the hoary binary update? I m having that same problem installing vlc that you had.

Thank you for your help.

---

### Post by jskeleton89 on 2008-02-22
Hey, I was having similar problems installing VLC, this is how I installed it....

I went to "System" -> "Administration" -> "Synaptic Package Manager"

Once Synaptic Loaded up, I went to "Settings" -> "Repositories" 

Under the "Ubuntu Software" Tab, I checked everything but "Software Restricted by Copyright or Legal Issues" then hit close.

I then hit "reload" in "Synaptic, searched for "VLC" and it installed without a problem....

I hope this helps everyone...

-Jack

---

