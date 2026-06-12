---
title: "Firefox-ESR on zesty zapus?"
date: 2017-08-26
forum: General Help
---

### Post by ejbiow on 2017-08-26
As many of you know, Firefox 57 will only run web extension extensions and in fact, Firefox 55 disabled one of the extensions that I really like, to wit, [Toolbar Buttons]("https://addons.mozilla.org/en-US/firefox/addon/toolbar-buttons/reviews/").  I love having a button in my toolbar that will take me to the top or bottom of the page and others that enlarge and shrink the page, etc. Yes, I know, I can do it from the keyboard, but I'm not one of those folks that always has her hands on the keyboard, normally, I am just reading, and the rodent is my friend. 

Normally I use Debian and both Stretch and Jessie use firefox-esr, which should give me a year or so to find alternatives to Toolbar Buttons (or more likely, away from Firefox altogether, which has been moving away from configurability for years and towards a more Google Chrome simplified walled-garden approach; palemoon looks promising). For xenial 16.04 I was able to install firefox-esr from [Jonathon F's PPA]("https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr"), and all was good, but it doesn't work for zesty, I get the following:
```
The following packages have unmet dependencies:
 firefox-esr : Depends: libhunspell-1.3-0 but it is not installable
               Depends: libjsoncpp0 (>= 0.6.0~rc2) but it is not installable
``` Ubuntuzilla doesn't package an ESR version of firefox for Ubuntu, either.

So for the moment I've just installed the Debian Stretch stable version of firefox-esr, it seemed to install cleanly and is working for the moment.
```
dpkg -i firefox-esr_52.3.0esr-1~deb9u1_amd64.deb 
Selecting previously unselected package firefox-esr.
(Reading database ... 382673 files and directories currently installed.)
Preparing to unpack .../firefox-esr_52.3.0esr-1~deb9u1_amd64.deb ...
Adding 'diversion of /usr/bin/firefox to /usr/bin/firefox.real by firefox-esr'
Unpacking firefox-esr (52.3.0esr-1~deb9u1) ...
Setting up firefox-esr (52.3.0esr-1~deb9u1) ...
update-alternatives: using /usr/bin/firefox-esr to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
Processing triggers for man-db (2.7.6.1-2) ...
``` 
This is not a great solution, I will have to update it manually every time the esr package gets updated. Does anyone have a better suggestion, other than just sucking it up and living with Mozilla's current version?

---

### Post by &amp;KyT$0P# on 2017-08-26
Why do you need it as a third-party .deb package?  It would be better to use the [official Mozilla build]("https://www.mozilla.org/firefox/organizations/all/"), if you can.

---

### Post by ejbiow on 2017-08-26
It just seemed easier, a deb file will update the menus for me and I will notice when my Debian stable firefox gets updated and can copy the deb file from /var/cache/apt/archives/ to my always-on local server so I won't have to hunt down the official Mozilla build every time it is modified.

---

