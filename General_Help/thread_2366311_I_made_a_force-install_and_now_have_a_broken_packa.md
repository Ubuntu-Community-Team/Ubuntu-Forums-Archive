---
title: "I made a force-install and now have a broken package"
date: 2017-07-16
forum: General Help
---

### Post by Coto_Paxi on 2017-07-16
Hi everyone,

I am linux user since 2007 and I made a fresh install (without formating the home partition) of (kubuntu) 17.04.

My lapttop is a Lenovo ThinkPad Edge E325.

I wanted to install Opera 12.16 from a *.deb file, which was not possible because of unmet dependencies.

I ran the command:
```
[FONT=monospace][COLOR=#000000]sudo dpkg --force-depends -i opera_12.16.1860_amd64.deb[/COLOR]
[/FONT]
```

Terminal did warn me about broken dependencies.

Now synaptic is constantly wanting to remove opera_12.16, which I don't want to allow, because this opera has been my mail client for some 15 years.

I will now post the output of the request to install vym
```
 [FONT=monospace][COLOR=#000000]/home/skippy# sudo apt-get install vym[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 opera : Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.16) but it is not installable
         Depends: libgstreamer0.10-0 (>= 0.10.15) but it is not installable
         Depends: gstreamer0.10-plugins-good but it is not installable
 vym : Depends: xsltproc
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
[/FONT]
```

When I run
```
apt --fix-broken install
```
the system wants to remove this opera, which I don't want to happen. 

Can anyone give me a helping hand, please? Can this be fixed in any way?

Thanks guys!

---

### Post by again? on 2017-07-16
I too have Opera 12.16 installed (just for the mail client).
Although I don't recall where I got the info from, I have this in my notes which
must have been the procedure I followed. (may have removed gstreamer dependencies)

> sudo dpkg --force-all -i opera_12.16.1860_amd64.deb

Then edit /var/lib/dpkg/status

Search for "opera "[COLOR="#FF0000"]*[/COLOR] and change "Depends:" line to
Depends: libc6 (>= 2.8), libfontconfig1, libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libice6, libsm6, libstdc++6 (>= 4.1.1), libx11-6, libxext6, libxml2 (>= 2.6.27), libxrender1, debconf (>= 0.5) | debconf-2.0, fonts-liberation | ttf-liberation | ttf-mscorefonts-installer

Also clear "Recommends:" line

Disable opera ppa and
• sudo apt update

Backup /var/lib/dpkg/status before you edit.
[COLOR="#FF0000"]*[/COLOR]When you search for opera include a space after or you will get a hundred or so matches.

For reference I'm running Gnome-Ubuntu 17.04 and this is the Opera section of my **/var/lib/dpkg/status** file.
```
Package: opera
Status: install ok installed
Priority: optional
Section: non-free/web
Installed-Size: 45535
Maintainer: Opera Packaging Team <packager@opera.com>
Bugs: https://bugs.opera.com/wizard/
Architecture: amd64
Version: 12.16.1860
Provides: www-browser, mail-reader, imap-client, news-reader
Depends: libc6 (>= 2.8), libfontconfig1, libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libice6, libsm6, libstdc++6 (>= 4.1.1), libx11-6, libxext6, libxml2 (>= 2.6.27), libxrender1, debconf (>= 0.5) | debconf-2.0, fonts-liberation | ttf-liberation | ttf-mscorefonts-installer
Recommends:
Description: Fast and secure web browser and Internet suite
 Opera is a small, fast, customizable, powerful and user-friendly web
 browser, as well as an Internet suite, including an email client, an IRC
 client, and web developer tools (Opera Dragonfly).
Homepage: http://www.opera.com/browser/
```
After making changes...
```
glen@GU17:~$ apt depends opera
opera
  Depends: libc6 (>= 2.8)
  Depends: libfontconfig1
  Depends: libfreetype6 (>= 2.2.1)
  Depends: libgcc1 (>= 1:4.1.1)
  Depends: libglib2.0-0 (>= 2.16.0)
  Depends: libice6
  Depends: libsm6
  Depends: libstdc++6 (>= 4.1.1)
  Depends: libx11-6
  Depends: libxext6
  Depends: libxml2 (>= 2.6.27)
  Depends: libxrender1
 |Depends: debconf (>= 0.5)
  Depends: <debconf-2.0>
    cdebconf
    debconf
 |Depends: fonts-liberation
 |Depends: ttf-liberation
  Depends: ttf-mscorefonts-installer
```


vym installs here without problems.
```
glen@GU17:~$ **apt policy vym xsltproc**
**vym**:
  Installed: 2.5.0-2
  Candidate: 2.5.0-2
  Version table:
 *** 2.5.0-2 500
        500 http://ftp.iinet.net.au/pub/ubuntu zesty/universe amd64 Packages
        100 /var/lib/dpkg/status
**xsltproc**:
  Installed: 1.1.29-2ubuntu0.1
  Candidate: 1.1.29-2ubuntu0.1
  Version table:
 *** 1.1.29-2ubuntu0.1 500
        500 http://ftp.iinet.net.au/pub/ubuntu zesty-updates/main amd64 Packages
        500 http://ftp.iinet.net.au/pub/ubuntu zesty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1.1.29-2 500
        500 http://ftp.iinet.net.au/pub/ubuntu zesty/main amd64 Packages
```

---

### Post by Coto_Paxi on 2017-07-16
Guber 2:

That solved it!! :popcorn:

Thanks a million!

One important thing to keep in mind:

I have installed Opera 12.xx and also Opera 26.xx (opera beta), which I use for regular browsing. In the file you mentioned I made the modifications first to the opera text that corresponded to opera beta. Once I found the Opera 12.xx lines, everything went like a charm!

Thanks again!

I will mark this topic as solved.

---

### Post by again? on 2017-07-16
Ok.
I used to use opera-beta. Now a Vivaldi fan.
Started using opera on Windows back when it was ad-sponsored.
Can't leave the old mail client though. :P

---

