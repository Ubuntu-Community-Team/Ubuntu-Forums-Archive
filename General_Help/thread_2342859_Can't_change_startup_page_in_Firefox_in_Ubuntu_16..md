---
title: "Can't change startup page in Firefox in Ubuntu 16.10 Mate"
date: 2016-11-10
forum: General Help
---

### Post by Mark Phelps on 2016-11-10
Despite using the preferences to change the start page in Firefox in Ubuntu 16.10 Mate, it does not work.

It keeps reverting to the default page.

I've remove the preferences -- no change

I've uninstalled Firefox, removed any remaining files, reinstalled firefox -- no change.

I've RESET Firefox -- no change.

Any ideas?
Top

---

### Post by #&amp;thj^% on 2016-11-10
This was also linked here:[https://ubuntuforums.org/showthread.php?t=2342072&p=13565275#post13565275](https://ubuntuforums.org/showthread.php?t=2342072&p=13565275#post13565275)
```
sudo apt remove ubuntu-mate-default-settings
```
Cheers

---

### Post by howefield on 2016-11-10
It's a low priority marked bug, however there is a package that you can uninstall which will fix it, just can't find the recently posted thread on the same subject right now.

Edit : Aha.. ninja'ed by 1fallen:)

---

### Post by Mark Phelps on 2016-11-10
> **1fallen said:**
> This was also linked here:[https://ubuntuforums.org/showthread.php?t=2342072&p=13565275#post13565275](https://ubuntuforums.org/showthread.php?t=2342072&p=13565275#post13565275)
```
sudo apt remove ubuntu-mate-default-settings
```
Cheers

Thought it was something I was doing wrong, so I went into my Mint install -- and there, the preference changes work OK.

However, I did this package removal and that fix it!

thanks for the help

---

### Post by #&amp;thj^% on 2016-11-10
Your Very Welcome.
And thanks for your contributions also.

---

### Post by Mark Phelps on 2016-11-10
Sorry folks, I spoke too soon.

While that DID fix the Firefox preferences problem, it trashed the install in the process.

When I came back after shutting it down and attempted to login, I got the failure to start session error -- and the ONLY way to fix that was to do a restore to an older install -- a few days ago.

After I did that, I was able to boot OK.  So then, I set about making the changes again.

And, once again, after making the Firefox changes, when I tried to reboot, I got the session error message again.

Guess I will have to live without the Firefox preferences working.

---

### Post by &amp;KyT$0P# on 2016-11-10
> **Mark Phelps said:**
> Guess I will have to live without the Firefox preferences working.
Not so sure about that.  Looking at [the package]("http://packages.ubuntu.com/yakkety/ubuntu-mate-default-settings"), you will notice that it installs a file [FONT=Courier New]/usr/lib/firefox/ubuntumate.cfg[/FONT].  That is a [lockpref file]("http://kb.mozillazine.org/Locking_preferences"), set up by [FONT=Courier New]/usr/lib/firefox/defaults/pref/all-ubuntumate.js[/FONT].

Can you completely quit Firefox, then modify the lockpref file to use your preferred startup page?

---

### Post by Mark Phelps on 2016-11-10
> **halogen2 said:**
> Not so sure about that.  Looking at [the package]("http://packages.ubuntu.com/yakkety/ubuntu-mate-default-settings"), you will notice that it installs a file [FONT=Courier New]/usr/lib/firefox/ubuntumate.cfg[/FONT].  That is a [lockpref file]("http://kb.mozillazine.org/Locking_preferences"), set up by [FONT=Courier New]/usr/lib/firefox/defaults/pref/all-ubuntumate.js[/FONT].

Can you completely quit Firefox, then modify the lockpref file to use your preferred startup page?

Thanks, that was EXACTLY what worked!

I was messing around with config files and discovered that this fix (editing the ubuntumate.cfg file) is what fixes the problem.

The bug report says deleting it fixes the problem -- but that prevents Firefox from starting.

Also, doing the package removal gets rid of LOTS of packages, so much that Ubuntu can't start after that.

---

### Post by &amp;KyT$0P# on 2016-11-10
You're welcome!  :KS

> **Mark Phelps said:**
> The bug report says deleting it fixes the problem -- but that prevents Firefox from starting.
Yeah, not surprising there'd be issues with that.  It leaves [FONT=Courier New]all-ubuntumate.js[/FONT] a loose end which needs to be tied up.

---

### Post by #&amp;thj^% on 2016-11-11
> **Mark Phelps said:**
> Sorry folks, I spoke too soon.

While that DID fix the Firefox preferences problem, it trashed the install in the process.

When I came back after shutting it down and attempted to login, I got the failure to start session error -- and the ONLY way to fix that was to do a restore to an older install -- a few days ago.

After I did that, I was able to boot OK.  So then, I set about making the changes again.

And, once again, after making the Firefox changes, when I tried to reboot, I got the session error message again.

Guess I will have to live without the Firefox preferences working.

How Odd? All good here...and this was suggested by lah 7  as described here: [https://ubuntu-mate.community/t/ubuntu-mate-always-forces-search-start-page-in-firefox/7707/10](https://ubuntu-mate.community/t/ubuntu-mate-always-forces-search-start-page-in-firefox/7707/10)
[S]Mark Phelps you may want to add further information to the bug.[/S]
Sorry You had problems though.
```
System:    Host: me-System-Product-Name Kernel: 4.8.0-26-generic x86_64 (64 bit)
           Desktop: MATE 1.16.0  Distro: Ubuntu 16.10

```

EDIT: Just got new information here:
> Seems to be just a **16.10 bug**, ubuntu-mate-default-settings for 16.04 [(v16.04.5.3)]("https://launchpad.net/ubuntu/+archive/primary/+files/ubuntu-mate-settings_16.04.5.3.tar.xz") doesn't even contain the configuration files:
  /usr/lib/firefox/ubuntumate.cfg
/usr/lib/firefox/defaults/pref/all-ubuntumate.js 
 They're responsible. It's safer to delete them with **sudo**  then uninstall ubuntu-mate-default-settings which contains other defaults like the panels in MATE Tweak.


I would keep my eye on this thread...and I will try to keep it updated as new information rolls in.
Thanks for the new information Mark.

---

### Post by #&amp;thj^% on 2016-11-17
Mark I have not been able to reproduce your error..."failure to start session error" And this has bothered me ever since.
Also I am a tester so it has been a long time for me to remember what I did.
But in checking some old install-logs I discovered that I did notice what was being removed and what it was being replaced with.
What will be removed is:
```
The following packages will be REMOVED:
  mate-desktop-environment-core mate-screensaver mate-session-manager
  ubuntu-mate-core ubuntu-mate-default-settings ubuntu-mate-desktop
The following NEW packages will be installed:
 ** debian-mate-default-settings**
```
Again being a tester I was quick to spot the "Suggested packages:"
And I should have checked that install log first...so my bad here.(But  1 year ago is long time to remember that stuff ;)) 
```
mate-desktop-environment-core
```
But I show I also installed these packages along with that one.
```
sudo apt install mate-desktop-environment-core mate-screensaver mate-session-manager
```
And firefox Obey's "My" preferences. 
```
apt-cache policy ubuntu-mate-default-settings
ubuntu-mate-default-settings:
  Installed: (none)
  Candidate: 16.10.7
  Version table:
     16.10.7 500
        500 http://archive.ubuntu.com/ubuntu yakkety/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu yakkety/universe i386 Packages
        100 /var/lib/dpkg/status

```
So if interested... this is probably why I still have a working system...if not maybe **useful to future visitors**.
Screens included
Kind Regards

---

