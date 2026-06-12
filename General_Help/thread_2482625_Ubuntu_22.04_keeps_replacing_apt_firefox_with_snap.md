---
title: "Ubuntu 22.04 keeps replacing apt firefox with snap firefox"
date: 2023-01-06
forum: General Help
---

### Post by cheezykins on 2023-01-06
Every few days I end up on the snapd version of firefox. It's immediately obvious when it happens because it suddenly slows to a crawl, takes 30+ seconds to start up and one of my extensions refuses to work properly. then I look and it's running the snap instead.

I am installing firefox from the ppa:mozillateam/ppa PPA.

I have the following in /etc/apt/preferences.d/00-firefox

```
Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
```

And my apt-cache policy fore firefox shows as:

```
firefox:
  Installed: 1:1snap1-0ubuntu2
  Candidate: 108.0.2+build1-0ubuntu0.22.04.1~mt1
  Version table:
 *** 1:1snap1-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     108.0.2+build1-0ubuntu0.22.04.1~mt1 1001
       1001 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
```

Doing snap remove firefox and apt install firefox re-installs the correct version, but warns me that it is downgrading firefox

```
$ sudo apt install firefox
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  xul-ext-ubufox
The following NEW packages will be installed
  xul-ext-ubufox
The following packages will be DOWNGRADED:
  firefox
0 to upgrade, 1 to newly install, 1 to downgrade, 0 to remove and 5 not to upgrade.
```

So I am wondering if there's either a way to stop it from seeing the snap as an upgrade, or just stop it from considering the snap at all? Ideally without disabling snapd entirely as I have a couple of other things that are only available via snap.

---

### Post by TenPlus1 on 2023-01-06
Their is a guide available that shows how to remove snaps and block it from re-installing itself: [https://www.debugpoint.com/remove-snap-ubuntu/](https://www.debugpoint.com/remove-snap-ubuntu/)

---

### Post by cheezykins on 2023-01-06
I am wondering if this is the bit I was missing:

```
echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox
```

Unfortunately I am not sure how to test it until another Firefox version is released!

I've set it for now and I will see if it upgrades successfully through the PPA or if reverts to the snap again.

---

### Post by guiverc on 2023-01-06
Rather than read 3rd party blogs about how to do it, why not follow one of the  blogs written about the process via Ubuntu *development* team members (*there have been many!*).

eg. [https://balintreczey.hu/blog/firefox-on-ubuntu-22-04-from-deb-not-from-snap/](https://balintreczey.hu/blog/firefox-on-ubuntu-22-04-from-deb-not-from-snap/)

[I]Posted just in case helpful.

([/I]* blogs from Ubuntu Members inc. developers get picked up at Planet Ubuntu, Ubuntu News etc.* *thus you don't have to subscribe to them all *)

---

### Post by monkeybrain20122 on 2023-01-07
Why don't you just download it from Mozilla? You can check for update by clicking Help > About Firefox. If there is a update just restart FF and it will do it automatically.

---

### Post by oldfred on 2023-01-07
I followed the instructions here to remove snap & add ppa.

You also have to reset priorities as shown or it will reinstall the Firefox snap.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)

---

