---
title: "Software updates for Feisty?"
date: 2007-10-03
forum: General Help
---

### Post by th_11 on 2007-10-03
I have been wondering is there going to be updated packages for OpenOffice and Firefox on Feisty?

I have Feisty and Update Manager haven't offered me updates for Firefox or OpenOffice.

My Firefox version is 2.0.0.6 and OpenOffice version is 2.2.0. I'm also wondering that should I not use OpenOffice at all to make sure my system doesn't get compromised by that OpenOffice vulnerability?

Or should I just wait a bit longer to get the updates from Update Manager?

---

### Post by strabes on 2007-10-03
Gutsy has the new versions of those programs. You can upgrade to gutsy by running:```
gksudo update-manager -c
```

---

### Post by por100pre1 on 2007-10-03
For Firefox try [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/").

---

### Post by rsambuca on 2007-10-03
I think you may as well just wait the 2 and a half weeks and upgrade to Gutsy after it has reached official stable status.  In the mean time, Firefox is regularly updated, so don't worry about that, and as for OO, just don't open any unknown tiff files and you will be fine.

---

### Post by TheExplorer on 2007-10-03
The thing is that Firefox doesn't need to be upgraded from 2.0.0.6 to 2.0.0.7 under Linux.
> Fixed in Firefox 2.0.0.7
MFSA 2007-28 Code execution via QuickTime Media-link files
It matters only in Windows environment.

P.S. You can install Mozilla products manually. Just download them and do the following:
> sudo tar -C /opt -zxvf ~/Desktop/thunderbird-* (if the .tar.gz file is on the Desktop)
sudo ln -s /opt/thunderbird/thunderbird /usr/local/bin/thunderbird

This is how I install Thunderbird for e.g. It resides in my /opt directory.

---

### Post by rsambuca on 2007-10-03
> **TheExplorer said:**
> The thing is that Firefox doesn't need to be upgraded from 2.0.0.6 to 2.0.0.7 under Linux.

It matters only in Windows environment.
In any event, FF receives regular security updates in Ubuntu, regardless of the version number.

---

### Post by nanotube on 2007-10-03
> **TheExplorer said:**
> 
P.S. You can install Mozilla products manually. Just download them and do the following:


This is how I install Thunderbird for e.g. It resides in my /opt directory.

sorry but this is kind of bad advice. if all you do is those two commands, that doesn't prevent you from running the old version by clicking the icons, which may mess up your profile. also doesn't import your old setttings... no profile backup for just in case... no plugins.... there are more complete manual installation instructions on the ubuntu wiki. 

for thunderbird:
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

for firefox:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by th_11 on 2007-10-04
Thanks for the replies!

I think I'll wait that two and a half weeks and then upgrade to Gutsy. It's good to know that Firefox in  Feisty is safe to use, and I'll just make sure I don't open any unknown tiff files so I don't have to think about OpenOffice.

By the way, I used Ubuntuzilla when I first started with Ubuntu to get the latest Thunderbird, and it worked great back then!

So few more weeks waiting for Gutsy... I'm getting  excited :D

---

### Post by th_11 on 2007-10-05
A few days ago I was asking about those OpenOffice security updates... Now this morning I logged in to my Feisty and UpdateManager offered me OpenOffice security updates!

This is amazing, now I feel  like "they made the update for me" :D

Good work!

---

### Post by cmost on 2007-10-05
You should also be aware that you can download and install the OpenOffice.org debs directly from the openoffice.org website. Simply remove the Ubuntu OpenOffice using Synaptic, then untar the downloaded archive.  Go into the DEBS directory and type 'sudo dpkg -i *.deb'  wait for the packages to install.  Then, navigate to the desktop integration directory and repeat the aforementioned command.  You may also want to PIN the new openoffice packages in Synaptic to avoid Apt offering to "autoclean" them for you.  I've been running the newest OpenOffice since its release and it is much improved.

---

### Post by th_11 on 2007-10-05
I was actually thinking that if I would update OpenOffice manually, but as I heard the newest version of OpenOffice will be included in Gutsy, and Gutsy is only a few weeks away so I decided to go with the older version of OpenOffice these few weeks (I don't use OpenOffice THAT much).

---

### Post by venik212 on 2007-10-05
Nanotube, The HOWTO you have posted prodeced only errors for me-- the system hung and did not respond, etc.
It is hard to understand why they do not keep TB uptodate in the repositories.

---

### Post by nanotube on 2007-10-06
> **venik212 said:**
> Nanotube, The HOWTO you have posted prodeced only errors for me-- the system hung and did not respond, etc.
It is hard to understand why they do not keep TB uptodate in the repositories.

if you want help to try and resolve the errors, then please post the details, and we'll try to help you. the instructions on the ubuntu wiki have worked for many in the past, so my suspicion would be that maybe you mistyped some commands?

if you are just ready to give up and don't care about resolving the errors, then... well, you don't have to do anything else. :)

---

### Post by venik212 on 2007-10-08
Thanks, but I think I'll just wait for Gutsy's official release.

---

