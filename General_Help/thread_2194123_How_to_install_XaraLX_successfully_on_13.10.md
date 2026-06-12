---
title: "How to install XaraLX successfully on 13.10"
date: 2013-12-16
forum: General Help
---

### Post by gnoshme on 2013-12-16
Posting here in case people need to find it.

XaraLX is a long forgotten brilliant tool that is an open source version of the Xara vector design tool.  The last time it was touched by Xara themselves was in November 2007, but it's been working fine in Ubuntu ever since, and is in the repo, but the repo version is broken.

Here's what to do

The issue has been solved by the Debian guys. Get the download from

64bit: [http://packages.debian.org/jessie/amd64/xaralx/download](http://packages.debian.org/jessie/amd64/xaralx/download)
or
32bit: [http://packages.debian.org/jessie/i386/xaralx/download]("http://packages.debian.org/jessie/amd64/xaralx/download")

install with:
 
sudo dpkg  -i --ignore-depends=libfontconfig1,libwxbase2.8-0,libwxgtk2.8-0 [download file]

It seems to work fine even though the dependent ubuntu packages are older than Debian is wanting (hence the ignore-depends) in this.

UPDATE:

So forcing this dependency ignore then messes around with subsequent attempts to install other software, with an error like:

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 xaralx : Depends: libfontconfig1 (>= 2.11) but 2.10.93-0ubuntu1 is to be installed
          Depends: libwxbase2.8-0 (>= 2.8.12.1+dfsg) but 2.8.12.1-14ubuntu1.1 is to be installed
          Depends: libwxgtk2.8-0 (>= 2.8.12.1+dfsg) but 2.8.12.1-14ubuntu1.1 is to be installed
          Recommends: xaralx-svg but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

The not very elegant solution is to sudo edit /var/lib/dpkg/status

Search for xaralx then in the dependency list remove the entries shown in the error.



K

---

### Post by braznyc on 2013-12-22
> **gnoshme said:**
> Posting here in case people need to find it.

XaraLX is a long forgotten brilliant tool that is an open source version of the Xara vector design tool.  The last time it was touched by Xara themselves was in November 2007, but it's been working fine in Ubuntu ever since, and is in the repo, but the repo version is broken.

Here's what to do

The issue has been solved by the Debian guys. Get the download from

64bit: [http://packages.debian.org/jessie/amd64/xaralx/download](http://packages.debian.org/jessie/amd64/xaralx/download)
or
32bit: [http://packages.debian.org/jessie/i386/xaralx/download]("http://packages.debian.org/jessie/amd64/xaralx/download")

install with:
 
sudo dpkg  -i --ignore-depends=libfontconfig1,libwxbase2.8-0,libwxgtk2.8-0 [download file]

It seems to work fine even though the dependent ubuntu packages are older than Debian is wanting (hence the ignore-depends) in this.

K



I had to keep Ubuntu 13.04 because when I upgraded to 13.10 XaraLX stopped working.

XaraLX is great and everyone should try it!


Thank you Gnoshme and thanks, Debian guys!

---

### Post by dragonfly41 on 2013-12-22
Trying to install on Ubuntu 12.04 32 bit.

Error: Dependency is not satisfiable
libfontconfig1(>=2.11)

So I got it from here ...
[(http://packages.debian.org/sid/i386/libfontconfig1/download)But when installing ..Error: Breaks existing package 'libfontconfig1-dev' dependencylibfontconfig1 (= 2.8.0-3ubuntu9.1)So next I had to find libfontconfig1-devIt seems that fontconfig stops at version 2.8 for Precise.https://launchpad.net/ubuntu/+source/fontconfig"]http://packages.debian.org/sid/i386/libfontconfig1/download]("http://Trying to install on Ubuntu 12.04 32 bit.Error: Dependency is not satisfiable libfontconfig1(>=2.11)I got it from here ... [http://packages.debian.org/sid/i386/libfontconfig1/download)

But when installing ..

Error: Breaks existing package 'libfontconfig1-dev' dependency 
libfontconfig1 (= 2.8.0-3ubuntu9.1)

So next I had to find libfontconfig1-dev

It seems that fontconfig package stops at version 2.8 for Precise.

[(http://packages.debian.org/sid/i386/libfontconfig1/download)But when installing ..Error: Breaks existing package 'libfontconfig1-dev' dependencylibfontconfig1 (= 2.8.0-3ubuntu9.1)So next I had to find libfontconfig1-devIt seems that fontconfig stops at version 2.8 for Precise.https://launchpad.net/ubuntu/+source/fontconfig"]https://launchpad.net/ubuntu/+source/fontconfig]("http://Trying to install on Ubuntu 12.04 32 bit.Error: Dependency is not satisfiable libfontconfig1(>=2.11)I got it from here ... [http://packages.debian.org/sid/i386/libfontconfig1/download)

What is needed to try XaraLX on 12.04?

===============================

[COLOR=maroon][Later edit]
A much simpler installation than I thought .. sudo apt-get install xaralx

...

After trying .. however top menubar appears to be truncated/hidden!

[/COLOR]

---

### Post by gnoshme on 2013-12-22
Huh.  For 12.04 I had no issues at all.. sudo apt-get install xaralx - Oh.. yes, you found it!

Braznyc and others.

The one issue I've had with Xara for a couple of years is that the cursur seems to get trapped up in the menu system, and keystrokes and text just doesn't work anymore.  I've more recently discovered that one way to guarantee create this is if you try to drag rotate an object. Things just go really bad, and as far as I can tell that entire document is then unrecoverable in that you can never get it back to a point where the usual keystrokes work.

Anyone else see this or have any suggestions?

K

---

### Post by manikinxvx on 2014-04-08
I had no problems *installing* Xara by simply going through the Ubuntu Software Center. However, upon installation, Xara simply will not launch. Anyone have any thoughts on this issue? (Xara LX 0.7r1785-5ubuntu2 on Xubuntu 13.10)

---

### Post by gnoshme on 2014-04-08
Yes. That's why this thread is here. The version in the repo that is being installed by the software center is broken.  Uninstall it from the software center then follow the instructions in this thread.

K

---

### Post by dragonfly41 on 2014-04-08
I run my Ubuntu 12.04 32bit desktop in Gnome Classic mode at login.
In that mode when I launch Xara Xtreme the top menu bar is missing.

However I found a workaround in this thread ...

[http://ubuntuforums.org/showthread.php?t=1920608](http://ubuntuforums.org/showthread.php?t=1920608)

> Apparently, Xara Xtreme is configured for Unity. Not for Gnome, not for Xfce, not for Enlightenment (those are the only DEs I have).

So, either run the desktop in Unity theme and maximise Xara Xtreme window in Unity to see the menu bar.

Or if remaining in Gnome Classic (with Xara menu bar missing) you can use the alt + key shortcuts (see thread link above)

alt f = file menu
alt e = edit menu
alt u = utilities menu
alt r = arrange menu
alt w = windows menu
alt h = help menu

---

### Post by 23dornot23d on 2014-04-08
Will it " SAVE " and pull back its own files properly now - or does it still give errors .....

I used it a lot before ..... but found I was having to screenshots of my work - then take the screenshot.

into inkscape and do a bitmap trace on the the files so I could save them as svg.

---

### Post by dragonfly41 on 2014-04-08
Well I've not yet used Xara much.
I've just now created a very simple test.xar file, saved it to desktop (using alt + f), closed Xara, re-opened Xara, restored test.xar

.. and it works so far.

I hope it is a good alternative to RealDraw Pro in windows.

---

### Post by 23dornot23d on 2014-04-08
Fails in 14.04 too ... so guess no one has done any fix for it ..........

> 
K53SV:~$ xaralx
xaralx: relocation error: xaralx: symbol _ZTV19wxGnomePrintFactory, version WXU_2.8 not defined in file libwx_gtk2u_core-2.8.so.0 with link time reference


Still like it ...........

[IMG]http://i.minus.com/iblJqQLTHoamx5.png[/IMG]

---

### Post by keulerchen on 2014-04-25
i found this workaround today and it seems to work fine:
[http://www.ubuntuask.com/q/answers-xara-lx-wont-launch-in-13-10-367427.html](http://www.ubuntuask.com/q/answers-xara-lx-wont-launch-in-13-10-367427.html)

---

### Post by uwe-bungto on 2014-04-29
If it doesn't work in 14.04 why is it in the repository?
I used that app under another name on a Acorn Archimedies, hope there is a fix for it.

---

### Post by keulerchen on 2014-04-29
maybe it's just a somehow forgotten piece of software ;)
but still: the woraround mentioned above also works with 14,4:
[http://www.ubuntuask.com/q/answers-xara-lx-wont-launch-in-13-10-367427.html](http://www.ubuntuask.com/q/answers-xara-lx-wont-launch-in-13-10-367427.html)

---

### Post by uwe-bungto on 2014-05-05
> **keulerchen said:**
> maybe it's just a somehow forgotten piece of software ;)
but still: the woraround mentioned above also works with 14,4:
[http://www.ubuntuask.com/q/answers-xara-lx-wont-launch-in-13-10-367427.html](http://www.ubuntuask.com/q/answers-xara-lx-wont-launch-in-13-10-367427.html)

It works now in Ubuntustudio 14.04

Thanks

---

### Post by xutpp on 2014-05-20
**Gnoshme** Thanks, it worked for me in **Ubuntu-Gnome 14.04** (xaralx_0.7r1785-7_amd64.deb)

Intel Core2 Duo CPU E4600 2.40GHz×2 2GiB Intel G33 amd64

---

### Post by kernelgo on 2014-07-12
> **keulerchen said:**
> maybe it's just a somehow forgotten piece of software ;)
but still: the woraround mentioned above also works with 14,4:
[http://www.ubuntuask.com/q/answers-xara-lx-wont-launch-in-13-10-367427.html](http://www.ubuntuask.com/q/answers-xara-lx-wont-launch-in-13-10-367427.html)

The link is down... Wich was that workaround please?

Im on Linuxmint 17 xfce 64b (based on Ubuntu 14.04 - 64b)

---

