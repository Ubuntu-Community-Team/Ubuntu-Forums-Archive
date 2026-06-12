---
title: "How come I need Flatpack to solve a snap issue ?"
date: 2023-09-04
forum: General Help
---

### Post by georgesgiralt on 2023-09-04
Hello Guys, 
Since the advent of Firefox snap, I've been bothered by the lack of communication between 3 extensions I use and need (the main one being Keepassxc) and the external programs needed for their job. 
I searched everywhere, and always ran into a dialogue issue. 
Then someone told me to use flatpack to check/set the permissions the snap package use for "webextensions". 
This is what I did : 
```

$ sudo apt install flatpak
........

```
I already had the required packages :
```

$ dpkg -l xdg-desktop-portal chrome-gnome-shell
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name               Version                 Architecture Description
+++-==================-=======================-============-===================================================
ii  chrome-gnome-shell 10.1-5                  all          GNOME Shell extensions integration for web browsers
ii  xdg-desktop-portal 1.14.4-1ubuntu2~22.04.1 amd64        desktop integration portal for Flatpak and Snap

```
Firefox was also the required version. 
```

$ snap list
Nom                                    Version          Révision  Suivi            Éditeur         Notes
bare                                   1.0              5         latest/stable    canonical&#10003;      base
canonical-livepatch                    10.6.0           235       latest/stable    canonical&#10003;      -
core                                   16-2.60.2        15925     latest/stable    canonical&#10003;      core
core20                                 20230801         2015      latest/stable    canonical&#10003;      base
core22                                 20230801         864       latest/stable    canonical&#10003;      base
firefox                                117.0-2          3068      latest/stable    mozilla&#10003;        -
..............

```

Then I checked the permissions using Flatpack :
```

$ flatpak permission-show snap.firefox
Table             Object                                App          Permissions                  Data
webextensions     org.gnome.chrome_gnome_shell          snap.firefox no                           0x00
webextensions     org.keepassxc.keepassxc_browser       snap.firefox no                           0x00
webextensions     net.downloadhelper.coapp              snap.firefox no                           0x00
webextensions     org.gnome.shell.extensions.gsconnect  snap.firefox yes                          0x00
desktop-used-apps application/vnd.debian.binary-package snap.firefox gdebi,2,3                    0x00
desktop-used-apps application/gzip                      snap.firefox org.gnome.FileRoller,1,3     0x00
.............

```
As you can see of the 4 extensions using "webextensions" only one had permissions set properly. And I do not know why (because it is the least used of the 4... )
Then I set the permissions :
```

$ flatpak permission-set webextensions org.gnome.chrome_gnome_shell    snap.firefox yes
$ flatpak permission-set webextensions org.keepassxc.keepassxc_browser snap.firefox yes
$ flatpak permission-set webextensions net.downloadhelper.coapp snap.firefox yes

```
IT worked :
```

$ flatpak permission-show snap.firefox
Table             Object                                App          Permissions                  Data
webextensions     org.keepassxc.keepassxc_browser       snap.firefox yes                          0x00
webextensions     net.downloadhelper.coapp              snap.firefox yes                          0x00
webextensions     org.gnome.chrome_gnome_shell          snap.firefox yes                          0x00
webextensions     org.gnome.shell.extensions.gsconnect  snap.firefox yes                          0x00
desktop-used-apps application/vnd.debian.binary-package snap.firefox gdebi,2,3                    0x00
desktop-used-apps application/gzip                      snap.firefox org.gnome.FileRoller,1,3     0x00
.....

```
A Firefox restart later and I was able to connect the Firefox keepassxc extension to the keepasxc app. Fine. 
The Gnome Shell extension also was working. 
Fantastic. 
Then I wondered why I could not find a snap command or subcommand to do the same, and why I need to use flatpack which is, as far as I know outside Canonical reach to do this ? 
So I decided to ask people more knowledgeable as me.
Could you please tell me how to do it the "Ubuntu" way ? 
Or point me to a documentation ? 
Many thanks in advance for your education ! 
Have a nice day !

---

### Post by TheFu on 2023-09-04
I only skimmed the post. Sorry.  Too early. No coffee anymore.

The manpages and code has help.
```
$ snap help
The snap command lets you install, configure, refresh and remove snaps.
Snaps are packages that work across many different Linux distributions,
enabling secure delivery and operation of the latest apps and utilities.

Usage: snap <command> [<options>...]

Commonly used commands can be classified as follows:

           Basics: find, info, install, remove, list
          ...more: refresh, revert, switch, disable, enable, create-cohort
          History: changes, tasks, abort, watch
          Daemons: services, start, stop, restart, logs
      Permissions: connections, interface, connect, disconnect
    Configuration: get, set, unset, wait
      App Aliases: alias, aliases, unalias, prefer
          Account: login, logout, whoami
        Snapshots: saved, save, check-snapshot, restore, forget
           Device: model, reboot, recovery
     Quota Groups: set-quota, remove-quota, quotas, quota
  Validation Sets: validate
        ... Other: warnings, okay, known, ack, version
      Development: validate

For more information about a command, run 'snap help <command>'.
For a short summary of all commands, run 'snap help --all'.

```
To get more detailed help, add the command to the help ... 
```
$ snap help interface
```
These help areas go deeper and deeper. It can be difficult to find what you need, but it is probably in there.  I find it easier to just avoid snaps for now, almost always.

[https://forum.snapcraft.io/t/snap-reference/30854](https://forum.snapcraft.io/t/snap-reference/30854)
[https://forum.snapcraft.io/t/snapd-rest-api/17954](https://forum.snapcraft.io/t/snapd-rest-api/17954) has the REST API.

The flatpak solution was just to make things easier.  Nothing wrong with that. Convening how to control a complex system is very hard.  People's eye glaze over.

BTW, I'm not trying to say snaps are perfect or even good.  I switched from Ubuntu as a desktop to Linux Mint to avoid snaps, but if you need to do exactly what a snap does already and nothing else, they are easy ... assuming you don't want control.  I've been burned and left with nonworking servers due to snaps self-updating without approval. I'd thought I specifically asked the snap NOT to move to a new major release, yet it did anyway.  Unfortunately, providing a bug report requires registering for yet another account. I already have far too many different accounts online - no interest in having yet another one.

For firefox on Ubuntu, the way to avoid snaps seems to be to use the ESR version of firefox instead.  [https://ubuntuhandbook.org/index.php/2022/03/install-firefox-esr-ubuntu/](https://ubuntuhandbook.org/index.php/2022/03/install-firefox-esr-ubuntu/)
For example, I like to control the sandbox that firefox runs in, so I use firejail.  Firejail and snap packages conflict, so if using snaps, I lose that control.  To me, that is unacceptable, but Linux is flexible.  The work-around is to use firefoxESR and run it inside a customized firejail setup in the way I prefer.

I use keepassxc, but never with a browser extension.. Call me crazy, but I want to control exactly when and where I login.  The "auto-play" feature built-into keepassXC let's be do that. No extensions needed. Of course, if there is a human in the middle, sometimes it fails to work perfectly every time. A little practice and it pretty much works, always now.

---

### Post by ian-weisser on 2023-09-04
> **georgesgiralt said:**
> 
Then I wondered why I could not find a snap command or subcommand to do the same, and why I need to use flatpack which is, as far as I know outside Canonical reach to do this ? 


This was discussed in [https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759](https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759), posts 68 and 69

Specifically from one developer:

> The use of the flatpak command is quite confusing indeed. ....[T]his is because the permissions database, even though it&#8217;s not  flatpak-specific (it&#8217;s also used for snaps), doesn&#8217;t have its own  separate management tool yet.

My opinion: Not re-inventing the database, and not-reinventing the database management tools seem like good things to me. Limited development resources going toward software that actually needs developing.

---

### Post by georgesgiralt on 2023-09-04
Yes, I searched on the Snap documentation web site and blogs and couldn't find anything except flatpack command... 
Funny. Ubuntu promoting snaps and relying on the competition to trim their software.... 
When I was in the IT business I constantly advised against regression in new version as this make us loose market shares and make customers angry...
Seems I retired too long ago ;-) 
Anyway, I was able to make it work in Firefox snap, and it worked right out of the box in Microsoft Edge web browser. Go figure.

---

### Post by oldfred on 2023-09-04
Another alternative is not to use snap at all. You can use a ppa.

You also have to reset priorities as shown or it will reinstall the Firefox snap.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)

---

### Post by georgesgiralt on 2023-09-05
> **ian-weisser said:**
> This was discussed in [https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759](https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759), posts 68 and 69

Specifically from one developer:



My opinion: Not re-inventing the database, and not-reinventing the database management tools seem like good things to me. Limited development resources going toward software that actually needs developing.

Ian, 
Something escapes me. If you look at the code *before* I made any change, you'll see that the "org.gnome.shell.extensions.gsconnect" extension had it's permissions set right. So IMHO, it is possible to do it right at the install stage of an extension (if GS Connect can, we can ;-) ). 
Also, I tend to slightly disagree with you. If the snap subsystem was not up to speed and not fully developed, why force it to crucial apps like Firefox and CUPS in the "mainstream LTS" versions ? 
IMHO it would have been better to refine the snap elements while offering some apps for the nerds to test or the early adopters in the .10 releases or make installation an alternative for the mainstream users. 
Canonical is denting it's reputation of a sturdy linux distro where everything is set right and run out of the box. 
I do not doubt that snaps respond to serious problems with a neat solution, but it is, today, very very far from the panacea they told us it will be. I hope this will be, one day. (And I wonder if the securities issues they promised are solved, really are, but it's just a hunch, I'm not so savvy in computer security to test it proper).
End of rant ;-) I'll go to my first morning coffee.
I'll turn this thread to Solved because I divert from the technical to the political... And my question is answered. You have to use Flatpack tools because the snap counterparts are not written, yet.

---

### Post by ian-weisser on 2023-09-05
> **georgesgiralt said:**
> If the snap subsystem was not up to speed and not fully developed, why force it to crucial apps like Firefox and CUPS in the "mainstream LTS" versions ?

Little software is ever considered by the developers to be feature-complete.
The Open Source community has a long history of using software that is just-barely-ready for use. And then arguing about it for years,

The Firefox decision to use Snaps was made by Mozilla, for their own internal reasons (reduced support resource requirements). Not by Ubuntu. Not by Canonical. Not by nefarious secret cabal.

Similarly, the migration of CUPS to Snaps was decided by the OpenPrinting developers for their own internal reasons (also, coincidentally, reduced support resource requirements). While there are Canonical employees working full-time on OpenPrinting, it was an OpenPrinting decision. And it was also OpenPrinting's decision to suspend work on their Snap migration when they determined that it wouldn't be ready for 24.04. 


> **georgesgiralt said:**
> IMHO it would have been better to refine the snap elements while offering some apps for the nerds to test or the early adopters in the .10 releases or make installation an alternative for the mainstream users. 

That seems like exactly what the Snap developers did from 2015-2021.



> **georgesgiralt said:**
> Canonical is denting it's reputation of a sturdy linux distro where everything is set right and run out of the box.

I will let Canonical look after its own reputation.
There have been folks claiming that Ubuntu and Canonical are in some form of death-spiral since about 2006.

Folks bitterly complained in 2007 that Ubuntu wasn't doing enough to improve the Linux Desktop. Then folks bitterly complained in 2009 when Canonical opened its checkbook and spent a fortune improving the Linux Desktop.

Folks bitterly complained before 2015 that Ubuntu wasn't doing enough to overcome the many shortcoming of debs. And folks have been bitterly complaining since about 2016 when Canonical opened its checkbook and spent a fortune developing Snaps for precisely that purpose.

Seems like folks are gonna complain no matter what.


> **georgesgiralt said:**
> I do not doubt that snaps respond to serious problems with a neat solution, but it is, today, very very far from the panacea they told us it will be. I hope this will be, one day. (And I wonder if the securities issues they promised are solved, really are, but it's just a hunch, I'm not so savvy in computer security to test it proper).


Snaps were never promised to be a panacea. They were intended to solve several specific problems that Debian had not envisioned 20 years ago. And they do that pretty well.

The main security issue is seen commonly here at UbuntuForums: Folks using unpatched old versions with published CVEs. The same security problem that Ubuntu Pro also addresses.

---

