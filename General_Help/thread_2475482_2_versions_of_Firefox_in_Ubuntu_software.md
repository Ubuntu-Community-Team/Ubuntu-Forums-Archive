---
title: "2 versions of Firefox in Ubuntu software"
date: 2022-05-28
forum: General Help
---

### Post by cam17 on 2022-05-28
When i search in Ubuntu software for firefox I see 2 versions. Why are there 2 versions of firefox and what is the difference? Also I specifically entered firefox but some other apps displayed, why ?

---

### Post by zebra2 on 2022-05-28
You don't say what release of Ubuntu you are using but if it is Ubuntu 22.04 you should only have the snapcraft version in software.  If you click and open each firefox being displayed you will get the needed info.  In other words snapcraft or deb.  I doubt the the deb version will be in the 22.04 software. In either case the snap version will default. The other software are appearing because they have a relationship with firefox in some way however minor.

---

### Post by #&amp;thj^% on 2022-05-28
One show's Installed, then again in the listings is all.
verify using:
```
apt-cache policy firefox
firefox:
  Installed: (none)
  Candidate: 1:1snap1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
     100.0.2+build1-0ubuntu0.22.04.1~mt1 500
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages

```
and 
```
snap list firefox
```
unless you also install from a different method IE:
```
flatpak search firefox
Name  Description                  Application ID     Version     Branch Remotes
Fire\u2026 Fast, Private & Safe Web Br\u2026 \u2026g.mozilla.firefox 100.0.2     stable flathub
Moja\u2026 Mojave-Style Theme for GTK \u2026 \u2026heme.Mojave-light 0.1         3.22   flathub
Fire\u2026 Client for accessing 3D vir\u2026 \u2026r.FirestormViewer 6.3.9.58205 stable flathub
Jopl\u2026 A free, open source note ta\u2026 \u2026ic.joplin_desktop 2.7.15      stable flathub
Libr\u2026 LibreWolf Web Browser        \u2026brewolf-community 100.0.2-1   stable flathub
Vieb  Vim Inspired Electron Brows\u2026 dev.vieb.Vieb      7.2.0       stable flathub

```

---

### Post by Dennis N on 2022-05-28
I have two also. One is a dummy apt package in the Ubuntu repository that installs the Snap version. The other is the actual Firefox snap.

---

### Post by grahammechanical on 2022-05-29
If this is Ubuntu 20.04 then Ubuntu Software will indeed show two versions of Firefox. The installed version will be the deb version. The other version which is not installed but can also be installed is the snap version. Both version can co-exist but I am not sure that they will share configuration files instead of acting independently to each other.

It should also be noted that an online upgrade to Ubuntu 22.04 will remove the deb version of Firefox and replace it with the snap version. This practice started with upgrades from Ubuntu 21.04 to 21.10. I doubt if the 22.04 software store will offer the Firefox deb version.

Regars

---

### Post by zebra2 on 2022-05-29
> **grahammechanical said:**
>  I doubt if the 22.04 software store will offer the Firefox deb version.

Regars

One would think that the OP with 187 posts would know to state which release is being referenced. Without that information the actual question can't be answered. The question really is about the Ubuntu Software app and not the snap vs deb issue. My 22.04 Ubuntu Software only lists one Firefox which is snapcraft.  In addition I have examined many other apps in the Ubuntu Software app and everything seems to be the snap version.  Also, my experience is that typing in a terminal "sudo apt-get install firefox" will resolve to a snap version.  Currently so far as I can see, the only alternative/workaround is to download a deb version from a PPA or other source or install a flatpak. 
Regarding the OP question why two firefox's. If it involves 22.04 the second copy may just be a clingon from an upgrade.  

I might as well add that with Ubuntu 22.10 if one were to run an apt-get firefox install instead of snap install the result could likely be a messy bog that won't open at all. 

If the OP wants to run firefox (which actually should be already installed) the snap install firefox would be the best bet, my opinion.

---

### Post by cam17 on 2022-05-29
The version I am running is 20.04.4 LTS.
when I run snap list firefox
i get
error: no matching snaps installed

Why is it the specific search firefox shows apps like Joplin?

---

### Post by zebra2 on 2022-05-29
> **cam17 said:**
> The version I am running is 20.04.4 LTS.
when I run snap list firefox
i get
error: no matching snaps installed

Why is it the specific search firefox shows apps like Joplin?
 
The reason Joplin shows up in a firefox search in Ubuntu Software is because parts of Joplin code is used in various browser extensions.  How that fact merits being listed in a firefox search could be completely random.  I wouldn't get bogged down in Ubuntu's reasons but that search result might be exactly what another user was trying to find. So far as the two firefox listings goes, answer is I don't know. 20.04 is ancient history in my experience. I suggest you click on the link and it will give you information on that result. It is possible that one is a snap app and the other a deb app. 

Thanks for clarifying your version.

---

### Post by cam17 on 2022-05-30
It is valid becuase the "ubuntu software" is clearly not finding the  apps a user is looking. Joplin has nothing to do with firefox hence why I  asked.

20.04.4 LTS is not scheduled to be updated until Aug-2022 so how is it ancient history?

---

### Post by zebra2 on 2022-05-30
> **cam17 said:**
> 

20.04.4 LTS is not scheduled to be updated until Aug-2022 so how is it ancient history?

I can't remember!

---

### Post by deadflowr on 2022-05-30
> Why is it the specific search firefox shows apps like Joplin?
Because some piece(s) of information provided by the apps are similar enough for the search to deem them possibly relevant.

---

### Post by cam17 on 2022-05-31
I was told that 20.04 LTS will be automatically updated in Aug-2022 through this forum. 

The Ubuntu software 3.38.1 seems to have problems are they local or system wide.
1. The search finds items that should not show
2. In some of the description on Ubuntu software it shows "never upgrade" like firefox but updates are still received.

---

### Post by deadflowr on 2022-05-31
> I was told that 20.04 LTS will be automatically updated in Aug-2022 through this forum.

No such thing as automatic.
What will happen is the upgrade channel will be officially opened up for users of 20.04 to have the ability to upgrade to 22.04.

And by official, I mean you will get an option in the update manager (software updater) for the upgrade,
without having to invoke any extra commands like you would need to do now in order to run an upgrade.

You can in fact run an upgrade right now if you invoke the -d flag when running the update-manager command from the command line.
And while it's usually safe, there is always a chance something odd might need to be squared away.

Which is why waiting until the channel is officially open can allow the developers to flesh out and fix any of those odd discrepancies that they can,
so as to allow for the best possible upgrade experiences.

---

### Post by cam17 on 2022-06-01
There is something wrong with "ubuntu software" it finds items that have no items in the search and it shows 2 of the same items in my case Firefox it also did this for Keepassxc.

---

### Post by cam17 on 2022-06-08
How can a user tell the difference between the 2 versions of Firefox? How are they different ?

---

