---
title: "How to update Flash Player"
date: 2017-11-14
forum: General Help
---

### Post by aneblanc on 2017-11-14
For a while now on some websites I have a banner telling me "Adobe Flash Player was blocked because it is out of date" with the options of "Update plug-in" or "Run this time".
I run Ubuntu 16.04 and Chromium 62.0.3202.75. Adobe Flash Player is not listed under chrome://components. 

How can I install, reinstall or update Flash?

---

### Post by again? on 2017-11-14
Make sure the Canonical Partner repository is enabled in other software.
Open via terminal...
```
software-properties-gtk --open-tab 1
```

After checking run an update and upgrade flash
```
sudo apt update
sudo apt install adobe-flashplugin
```

Also check you're allowing flash for the particular site by clicking the left side of the address bar.

---

### Post by andfree on 2018-02-05
I have the same problem, and the advice above didn't solve it. I haven't found any way to update flash, I only can choose the option "Run this time" every time the flash player is used. I run Ubuntu 16.04 xenial 64-bit & Chromium 64.0.3282.119[COLOR=#757575][FONT=Roboto].[/FONT][/COLOR]

---

### Post by again? on 2018-02-05
I have a beta version of chromium installed which doesn't pick up the latest flash even though
it appears to look in the same location as Vivaldi.
[ATTACH=CONFIG]278450[/ATTACH]
Had to install pepperflashplugin-nonfree where it reports the latest version from a different location and I no longer get the "out of date error"
[ATTACH=CONFIG]278449[/ATTACH]


If I downgrade chromium to the default version for 16.04 it picks up the latest flash without the extra  pepperflashplugin-nonfree install.
If your packages are up to date, chromium should be on version 64.
```
**[COLOR="#006400"]glen@Xen2:~$[/COLOR] apt policy chromium-browser**
chromium-browser:
  Installed: 64.0.3282.119-0ubuntu0.16.04.1
  Candidate: 64.0.3282.119-0ubuntu0.16.04.1
  Version table:
 *** 64.0.3282.119-0ubuntu0.16.04.1 500
        500 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe amd64 Packages
        500 http://ftp.iinet.net.au/pub/ubuntu xenial-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     49.0.2623.108-0ubuntu1.1233 500
        500 http://ftp.iinet.net.au/pub/ubuntu xenial/universe amd64 Packages

**[COLOR="#006400"]glen@Xen2:~$[/COLOR] chromium-browser --version**
Using PPAPI flash.
 --ppapi-flash-path=/usr/lib/adobe-flashplugin/libpepflashplayer.so --ppapi-flash-version=
Chromium 64.0.3282.119 Built on Ubuntu , running on Ubuntu 16.04
```

---

### Post by andfree on 2018-02-06
I[COLOR=#000000]nst[/COLOR][COLOR=#000000]alling pepperflashplugin-nonfree didn't solve the problem. I don't k[/COLOR][COLOR=#000000]now if I should[/COLOR][COLOR=#000000] somehow[/COLOR][COLOR=#000000] remove adobe-flashplugin, because:

[/COLOR]> $ chromium-browser --versionUsing PPAPI flash.
 --ppapi-flash-path=/usr/lib/adobe-flashplugin/libpepflashplayer.so --ppapi-flash-version=
Chromium 64.0.3282.119 Built on Ubuntu , running on Ubuntu 16.04
[COLOR=#000000]

[/COLOR]And a[COLOR=#000000]t [/COLOR]chrome://flash:

> [TABLE]
[TR]
[TD]**Flash plugin**[/TD]
[TD]28.0.0.126 /usr/lib/adobe-flashplugin/libpepflashplayer.so[/TD]
[/TR]
[TR]
[TD]****[/TD]
[TD]--- Crash data ---[/TD]
[/TR]
[/TABLE]


---

### Post by andfree on 2018-02-06
Finally, I removed it with the command:


```
sudo apt-get purge adobe-flashplugin
```


I reinstalled it, and now it's ok. It's solved for me. Thanks for the help.

---

### Post by slickymaster on 2018-02-06
> **andfree said:**
> Finally, I removed it with the command:


```
sudo apt-get purge adobe-flashplugin
```


I reinstalled it, and now it's ok. It's solved for me. Thanks for the help.

Being so, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by again? on 2018-02-06
> **slickymaster said:**
> Being so, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Not andfree's thread to *solverise*. :P

---

### Post by slickymaster on 2018-02-06
> **guber2 said:**
> Not andfree's thread to *solverise*. :P

Right :P

---

