---
title: "Updating oddities"
date: 2015-01-24
forum: General Help
---

### Post by Penfold1971 on 2015-01-24
My setup consists of a machine running Ubuntu 14.04.1 and an Intel iMac running Mac OS 10.6.8. I started with version 12.04 of Ubuntu and I kept up with updating until version 14.04.1 came out.

I use the Ubuntu machine solely to participate in the Folding@Home project and ran it headless until 14.04.1
I use Terminal app on the iMac to check in and see what the temperatures are and whether or nor there are updates to the Ubuntu software.

Previously I used these commands without any apparent issues :

[FONT=courier new]sudo apt-get update[/FONT] (to refresh available updates?)

followed by

[FONT=courier new]sudo apt-get dist-upgrade[/FONT] (to upgrade all packages plus install new ones as required?)

I then used [FONT=courier new]sudo apt-get autoremove[/FONT] (to clear away any useless packages?)

However with version 14.04.1, and using the same commands, I have noticed odd (to me) occurences, which I have put up with but which I now want to get clarified.


As an example, I have gathered the following 3 items from today’s updating :

**1) Logging into the Ubuntu machine from the iMac via Terminal app I got the message** :

[FONT=courier new]13 packages can be updated.[/FONT]
[FONT=courier new]8 updates are security updates[/FONT]

I used the commands as listed above, and as per usual. Following on from the second command the following appeared (I’ve only copied over and listed here the “Get: x http:” lines - I ommitted the lines that started with “Hit” for relative brevity) :

[FONT=courier new]Get:1 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates Release.gpg [933 B]          [/FONT]
[FONT=courier new]Get:2 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates Release [62.0 kB]   [/FONT]
[FONT=courier new]Get:3 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security Release.gpg [933 B]     [/FONT]
[FONT=courier new]Get:4 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security Release [62.0 kB]             [/FONT]
[FONT=courier new]Get:5 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/main Sources [64.4 kB][/FONT]
[FONT=courier new]Get:6 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/restricted Sources [2,061 B][/FONT]
[FONT=courier new]Get:7 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/universe Sources [17.4 kB][/FONT]
[FONT=courier new]Get:8 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/main Sources [157 kB][/FONT]
[FONT=courier new]Get:9 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/multiverse Sources [714 B] [/FONT]
[FONT=courier new]Get:10 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/main amd64 Packages [199 kB] [/FONT]
[FONT=courier new]Get:11 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/restricted Sources [2,061 B][/FONT]
[FONT=courier new]Get:12 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/universe Sources [97.6 kB]  [/FONT]
[FONT=courier new]Get:13 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/multiverse Sources [3,558 B][/FONT]
[FONT=courier new]Get:14 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/main amd64 Packages [406 kB][/FONT]
[FONT=courier new]Get:15 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/restricted amd64 Packages [8,875 B][/FONT]
[FONT=courier new]Get:16 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/universe amd64 Packages [84.7 kB][/FONT]
[FONT=courier new]Get:17 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/multiverse amd64 Packages [1,153 B][/FONT]
[FONT=courier new]Get:18 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/restricted amd64 Packages [8,875 B][/FONT]
[FONT=courier new]Get:19 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/universe amd64 Packages [240 kB][/FONT]
[FONT=courier new]Get:20 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/main i386 Packages [190 kB]  [/FONT]
[FONT=courier new]Get:21 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/multiverse amd64 Packages [9,392 B][/FONT]
[FONT=courier new]Get:22 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/restricted i386 Packages [8,846 B][/FONT]
[FONT=courier new]Get:23 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/main i386 Packages [397 kB] [/FONT]
[FONT=courier new]Get:24 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/universe i386 Packages [84.9 kB][/FONT]
[FONT=courier new]Get:25 [COLOR=#2400a9]_[http://security.ubuntu.com](http://security.ubuntu.com)_[/COLOR] trusty-security/multiverse i386 Packages [1,397 B][/FONT]
[FONT=courier new]Get:26 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/restricted i386 Packages [8,846 B][/FONT]
[FONT=courier new]Get:27 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/universe i386 Packages [241 kB][/FONT]
[FONT=courier new]Get:28 [COLOR=#2400a9]_[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)_[/COLOR] trusty-updates/multiverse i386 Packages [9,570 B][/FONT]

At this point I’m puzzled as to why there are 28 items when the original notice only mentioned the numbers 13 and 8. Also puzzling, 14 out of the 28 listed above are listed as ‘security’, not 8.

I carried out the third, (‘autoremove’), command and got :

[FONT=courier new]0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade[/FONT]

**2) When I logged out of the Ubuntu machine via Terminal, and then logged back in there was a message that said** :

[FONT=courier new]16 packages can be updated.[/FONT]
[FONT=courier new]8 updates are security updates[/FONT]

Repeating the first two Terminal commands resulted in :

[FONT=courier new]0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade[/FONT]

**3) Going to my Ubuntu machine a couple of hours later, I found Software Updater running with the following message** :

[FONT=courier new]Updated software is available for this computer. Do you want to install it now?[/FONT]

[FONT=courier new]Details of updates[/FONT]
[FONT=courier new]    Install[/FONT]
[FONT=courier new]    **Security updates**[/FONT]

[FONT=courier new]    Ubuntu base[/FONT]

[FONT=courier new]        Command-line SMB/CIFS clients for Unix[/FONT]
[FONT=courier new]        Common files used by both the Samba server and client[/FONT]
[FONT=courier new]        Library to read and write ELF files[/FONT]
[FONT=courier new]        Python bindings for Samba[/FONT]
[FONT=courier new]        Samba common files used by both the server and the client[/FONT]
[FONT=courier new]        Samba core libraries[/FONT]
[FONT=courier new]        Samba winbind client library[/FONT]
[FONT=courier new]        Shared library for communication with SMB/CIFS servers[/FONT]

[FONT=courier new]    **Other updates**[/FONT]

[FONT=courier new]        Landscape Service[/FONT]
[FONT=courier new]        Printers[/FONT]
[FONT=courier new]            Printer auto-configuration facility based on udev[/FONT]
[FONT=courier new]            Printer configuration GUI[/FONT]
[FONT=courier new]            Printers[/FONT]
[FONT=courier new]            Python modules for printer configuration with CUPS[/FONT]

I clicked on the Install now button of course.

There seems, to me, to be mismatches between the initial info given by Terminal on the iMac, the second piece of info given by Terminal on the iMac and then the info given by Software Updater on the Ubuntu machine.

Can anyone enlighten me, please? Are my Terminal commands now the wrong ones?

---

### Post by Penfold1971 on 2015-01-25
Bump.

Maybe my post was too long? Too many issues? Wrong sub-forum?

Can anyone advise please?

---

### Post by bapoumba on 2015-01-25
Well, I had subscribed to the thread yesterday to see what others might have to say about it :)
I'm not quite easy with problems running updates on one machine from another one.
How do you connect to your ubuntu machine ? Is that a server or a desktop install ?

---

### Post by ian-weisser on 2015-01-25
Couple important concepts:

- The Ubuntu repositories update *all the time*. So If you do an apt-get update a few minutes apart, you might get a different result if a package has been changed in the meantime.

- Software Updater and apt-get update use the same sources, but *differently*. Software Updater uses an additional step called Phased Updates. Apt-get doesn't. Phased Updates is a clever way to spread an update among the millions of updating machines over a few days or so, to allow a bad update to be noticed and reverted before it borks everyone's machines. So when updated Foo1.2 arrives, apt-get picks it up immediately, while Software Updater may wait a day or two. apt-get and Software Updater might give you different answers during that period - that's expected, and understandably confusing if you haven't seen it before.

- Apt-get **update** checks all your sources to refresh the database of available packages. 'Get 28' means you have 28 sources, not 28 packages to update. Apt-get **upgrade** uses the updated database to calculate that 13 updated packages are available from those 28 sources, and downloads and installs them.

- Apt-get **upgrade** and **dist-upgrade** have different behaviors on Ubuntu and Debian. In the ordinary course of an Ubuntu release, you will use 'upgrade' in daily use, and 'dist-upgrade' only for updating the kernel. Using 'dist-upgrade' daily won't hurt an Ubuntu system, go ahead and use it...but DON'T take that habit to a Debian system. An ordinary 'upgrade' should not cause any orphaned packages for autoremoval. A dist-upgrade often will cause packages for autoremoval...after a reboot. Your system should be autoremoving old kernel packages automatically for you already.

- When you log in to the terminal, the available-update messages are created by a message-of-the-day script in /etc/init/motd-update/ that uses the existing package database; it doesn't perform an apt-get update because that would delay your login (apt-get updates take time!) So the welcome message might be based on yesterday's data...or older, if you poweroff the machine.

- You can use both apt-get and Software Updater; using both won't cause harm. But using both won't have any benefit for you, either. They draw from the same sources.

---

### Post by bapoumba on 2015-01-25
> **ian-weisser said:**
> Couple important concepts:

- The Ubuntu repositories update *all the time*. So If you do an apt-get update a few minutes apart, you might get a different result if a package has been changed in the meantime.
Yeah, that was my first thought but was not quite sure about it.
> **ian-weisser said:**
> 
- Software Updater and apt-get update use the same sources, but *differently*. Software Updater uses an additional step called Phased Updates. Apt-get doesn't. Phased Updates is a clever way to spread an update over a few days or so, to allow a bad update to be noticed and reverted before it borks everyone's machines. So when updated Foo1.2 arrives, apt-get picks it up immediately, while Software Updater may wait a day or two. So apt-get and Software Updater might give you different answers - that's expected.

Phased updates would lead to less packages updated from Software Updater than from apt-get, but here the numbers are the other way around. That is what confused me most :)

---

### Post by ian-weisser on 2015-01-25
> **bapoumba said:**
> Phased updates would lead to less packages updated from Software Updater than from apt-get, but here the numbers are the other way around.

Hmm. I discounted the original 13 since that seemed old data. The apt-get update bumped that up to 16.

So I count 16 packages that apt-get is proposing, and 14 packages that Software Updater is proposing.
Perhaps I have misplaced a counting finger or two. It has happened before....

---

### Post by bapoumba on 2015-01-25
> **ian-weisser said:**
> Hmm. I discounted the original 13 since that seemed old data. The apt-get update bumped that up to 16.

So I count 16 packages that apt-get is proposing, and 14 packages that Software Updater is proposing.
Perhaps I have misplaced a counting finger or two. It has happened before....
Or me :) You are correct, sorry (and I did look at the latest ones /o\).
Makes sense then, I should have counted more carefully..

---

### Post by Penfold1971 on 2015-01-25
> **bapoumba said:**
> Well, I had subscribed to the thread yesterday to see what others might have to say about it :)
I'm not quite easy with problems running updates on one machine from another one.
How do you connect to your ubuntu machine ? Is that a server or a desktop install ?

The Ubuntu machine is connected via an ethernet cable to my AirPort Extreme Base Station. My Intel iMac connects wirelessly to the AEBS and then on through to the Ubuntu machine. (The AEBS is connected via ethernet cable to the router connected to the telephone line.)


The Ubuntu install is I am sure a desktop install. Is there some way I can tell? It was in June 2012 that I built the Ubuntu machine and installed Ubuntu version 12.04. I'm sure I wouldn't have known to select a server version. I wouldn't have known (and still don't) know exactly what a server version is.

---

### Post by Penfold1971 on 2015-01-25
> **ian-weisser said:**
> 
- Apt-get **update** checks all your sources to refresh the database of available packages. 'Get 28' means you have 28 sources, not 28 packages to update. Apt-get **upgrade** uses the updated database to calculate that 13 updated packages are available from those 28 sources, and downloads and installs them.

- Apt-get **upgrade** and **dist-upgrade** have different behaviors on Ubuntu and Debian. In the ordinary course of an Ubuntu release, you will use 'upgrade' in daily use, and 'dist-upgrade' only for updating the kernel. Using 'dist-upgrade' daily won't hurt an Ubuntu system, go ahead and use it...but DON'T take that habit to a Debian system. An ordinary 'upgrade' should not cause any orphaned packages for autoremoval. A dist-upgrade often will cause packages for autoremoval...after a reboot. Your system should be autoremoving old kernel packages automatically for you already.

- When you log in to the terminal, the available-update messages are created by a message-of-the-day script in /etc/init/motd-update/ that uses the existing package database; it doesn't perform an apt-get update because that would delay your login (apt-get updates take time!) So the welcome message might be based on yesterday's data...or older, if you poweroff the machine.

- You can use both apt-get and Software Updater; using both won't cause harm. But using both won't have any benefit for you, either. They draw from the same sources.
Thank you for patiently setting out that very full explanation. That is a great help to my understanding. And I have no intention of going to a Debian system ;).

I guess I can simply rely on my tried and tested routine as set out at the beginning of my first post and not go to the Ubuntu machine and deal with Software Updater.

Two things about my setup I didn't mention :

1) The Ubuntu machine is on permanently except for shutdown to respond to both an instruction to Restart **plus** (importantly) to use the shutdown to check for and clean dust out of the fan filters. So I use the Restart prompt as an excuse for a clean.
2) I want to run the machine without a monitor attached. I had been doing this, but the reboot into Ubuntu previously wouldn't proceed after power on. I had to reconnect the monitor and actually select 'Ubuntu' from a set of alternatives. It was only with the monitor re-attached that I began to see the software Updater messages.

---

