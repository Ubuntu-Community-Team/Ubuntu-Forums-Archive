---
title: "unable to install update from google"
date: 2013-10-16
forum: General Help
---

### Post by soluckytouselinux on 2013-10-16
Hi everyone. I just got this update from Google. I try and check the box to install the update, and I can't check the box. I tried updating from the terminal and that didn't work. I tried to Google the problem, and couldn't find anything. Thanx in advance[ATTACH=CONFIG]246994[/ATTACH]

---

### Post by gregz41 on 2013-10-16
I have the very same problem.... it shows up in update manager under other  but won't let me put a check in the box

---

### Post by TheFu on 2013-10-16
> **soluckytouselinux said:**
> Hi everyone. I just got this update from Google. I try and check the box to install the update, and I can't check the box. I tried updating from the terminal and that didn't work. I tried to Google the problem, and couldn't find anything. Thanx in advance[ATTACH=CONFIG]246994[/ATTACH]

a) if you didn't ask for it or go looking for it, then don't install it.  [http://krebsonsecurity.com/2011/05/krebss-3-basic-rules-for-online-safety/](http://krebsonsecurity.com/2011/05/krebss-3-basic-rules-for-online-safety/)
b) what update is it?  I've **never** seen a google update on Ubuntu. NEVER.

To me, this seems like an attack attempt.

---

### Post by gregz41 on 2013-10-16
It is the new update for chrome... It was released awhile ago took awhile to get here...  Attack through update manager ???????

---

### Post by gregz41 on 2013-10-16
from 66 to 69

---

### Post by TheFu on 2013-10-16
> **gregz41 said:**
> It is the new update for chrome... It was released awhile ago took awhile to get here...  Attack through update manager ???????

Any URL with "APT:" will cause Ubuntu desktop redirect the URL to the installer, correct? Seems like an attack to me. I've been expecting a Linux/Ubuntu attack for a few years. Even thought about how I'd do it.  I think it would be trivial and relatively easy to get a user to provide me with root access and they'd probably never know it.

I don't use chrome, but **chromium** definitely does NOT show up this way.

---

### Post by gregz41 on 2013-10-16
I shot and e-mail to google about it

---

### Post by slickymaster on 2013-10-16
FWIW, Chrome has been updated yesterday, to 30.0.1599.101 for Windows, Mac, Linux and Chrome Frame. All the information [here]("http://googlechromereleases.blogspot.pt/").

I've received it through a normal ```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
~$ apt-cache policy google-chrome-stable 
google-chrome-stable:
  Installed: 30.0.1599.66-1
  Candidate: 30.0.1599.101-1
  Version table:
     30.0.1599.101-1 0
        500 http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages
 *** 30.0.1599.66-1 0
        100 /var/lib/dpkg/status
```

---

### Post by craig10x on 2013-10-16
Same here....got that update yesterday...it's the latest version of Chrome 30 stable...installed fine for me...
Chromium doesn't get updated versions from Google...Chrome does (in fact it puts a ppa updater in your software sources)...

---

### Post by gregz41 on 2013-10-16
This is what I get:

Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  google-chrome-stable
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by slickymaster on 2013-10-16
Can you please post the output of```
apt-cache policy libc6
```

---

### Post by gregz41 on 2013-10-16
Here it is:

libc6:
  Installed: 2.15-0ubuntu10.4
  Candidate: 2.15-0ubuntu10.4
  Version table:
 *** 2.15-0ubuntu10.4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2.15-0ubuntu10.2 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages
     2.15-0ubuntu10 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages

---

### Post by slickymaster on 2013-10-16
> **gregz41 said:**
> Here it is:

libc6:
  Installed: 2.15-0ubuntu10.4
  Candidate: 2.15-0ubuntu10.4
  Version table:
 *** 2.15-0ubuntu10.4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2.15-0ubuntu10.2 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages
     2.15-0ubuntu10 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages

Hmm, I don't see any problems there. What about```
apt-cache policy libudev0
```can you please post the its output.

---

### Post by gregz41 on 2013-10-16
Here it is:

libudev0:
  Installed: 175-0ubuntu9.4
  Candidate: 175-0ubuntu9.4
  Version table:
 *** 175-0ubuntu9.4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     175-0ubuntu9 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages

---

### Post by scouser73 on 2013-10-16
Google Chrome blog details the update as being **Chrome has been updated to 30.0.1599.101 for Windows, Mac, Linux and Chrome Frame.**

According to an op posting on the Google Chrome blog, the 30.0.1599.101 version is being held back due to dependency issues.

[B][COLOR="#FF0000"][COLOR="#FF0000"]Depend: lib32gcc1 (>=1:4.1.1) but it is not installable
Depend: lib32stdc++6 (>=4.6) but it is not installable
Depend: libc6-i386 (>=2.11) but it is not installable[/COLOR][/COLOR][/B]

[http://googlechromereleases.blogspot.co.uk/2013/10/stable-channel-update_15.html](http://googlechromereleases.blogspot.co.uk/2013/10/stable-channel-update_15.html)

---

### Post by slickymaster on 2013-10-16
> **gregz41 said:**
> Here it is:

libudev0:
  Installed: 175-0ubuntu9.4
  Candidate: 175-0ubuntu9.4
  Version table:
 *** 175-0ubuntu9.4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     175-0ubuntu9 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages

That's really odd, even though my version of libc6 is 2.17-93ubuntu4, yours is recent enough to not cause the issue you're dealing with, and we are running the same version of libudev0,

Please issue the follwoing commands in a terminal and again post its output:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo apt-get dist-upgrade
```

---

### Post by craig10x on 2013-10-16
Perhaps you should delete the google ppa from you software sources, uninstall chrome and then re-install with the latest chrome from a new deb file from their site...
That will give you that latest updated version, and put a new ppa in your sources again...maybe your google ppa got messed up (just a guess)...

Any settings you had on your chrome (including extensions) will likely be remembered when you re-install because those preferences are in your system's home settings...
(you can bring up your chrome by typing  "google-chrome-stable" in the ubuntu software center search bar)...

---

### Post by gregz41 on 2013-10-16
here it is:

:~$ sudo aot-get install -f
sudo: aot-get: command not found



also if it will save all extensions and stuff


edit   i see prob  with command

Here it is:
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  google-chrome-stable

---

### Post by slickymaster on 2013-10-16
> **gregz41 said:**
> here it is:

:~$ sudo aot-get install -f
sudo: aot-get: command not found

also if it will save all extensions and stuff

Sorry [COLOR=#000000]gregz41, there was a typo in that command. The correct command to be issued is```
sudo apt-get instal -f
```

_NOTE:_ I edit my previous post to correct the typo.[/COLOR]

---

### Post by gregz41 on 2013-10-16
I seen that it does ssame thing as I posted above

I seen the typo,   I ran the commands and I get the same result

---

### Post by soluckytouselinux on 2013-10-16
It seems to me that Ubuntu and Google Chrome don't work well with each other. I have had problems in the past with Chrome. When I updated to 12.10, Google crashed. I think that I will stick with Chromium and Firefox for now until they get the bugs out. It's too bad. I really like Chrome.

---

### Post by slickymaster on 2013-10-17
Well, one thing you can be assured of, there's nothing wrong with your system.

The problem lies on Google side and there's an already reported bug - [Wrong 64-bit dependencies on 32-bit version of Ubuntu]("https://code.google.com/p/chromium/issues/detail?id=304017"). Chromium developers are working on it.

There's a suggested workaround, **_which I don't advise you to try because things can go the wrong way_**, that goes by unpacking the Debian package, editing DEBIAN/control to remove the incorrect dependencies and repack the Debian package.

```
~$ apt-get download google-chrome-stable
~$ dpkg-deb -R google-chrome-stable_30.0.1599.101-1_i386.deb 304017

~$ sed -i 304017/DEBIAN/control \
      -e 's/30.0.1599.101-1/30.0.1599.101-2~304017/' \
      -e 's/lib32gcc1 (>= 1:4.1.1), lib32stdc++6 (>= 4.6), //' \
      -e 's/libc6-i386 (>= 2.11), //'

~$ sudo chown root:root 304017/opt/google/chrome/chrome-sandbox
~$ sudo chmod 4755 304017/opt/google/chrome/chrome-sandbox

~$ dpkg-deb -b 304017
~$ sudo dpkg -i 304017.deb
```

---

