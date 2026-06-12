---
title: "Snap automatically remove Firefox(deb) and replace it with Firefox(snap)"
date: 2022-04-29
forum: General Help
---

### Post by tome74 on 2022-04-29
With the new Ubuntu 22.04, Firefox(snap) is installed by default. However, it failed to launch/run if the Firefox profile is managed by Profile Sync Daemon ([https://wiki.archlinux.org/title/profile-sync-daemon](https://wiki.archlinux.org/title/profile-sync-daemon)), which stores the profile in tmpfs, ie /run/user/$(uid), This is because snap limits access to directories outside the approved ones. 

So I removed Firefox (snap) and replaced it with Firefox(deb). Instructions ([https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/](https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/)). Unfortunately, a day later, Snap by itself, automatically decide to remove the Firefox(deb) and replace it with Firefox(snap). 

How to stop Snap from doing this ? Thanks.

Note: I have no problem using snap applications if it had worked properly.


-Hock

---

### Post by oldfred on 2022-04-30
I believe these were the steps I followed.
I then removed all snaps.
[URL="https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/"]https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/
[/URL]or:
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

```
90  sudo snap remove firefox
   91  sudo add-apt-repository ppa:mozillateam/ppa
   92  echo '
   93  Package: *
   94  Pin: release o=LP-PPA-mozillateam
   95  Pin-Priority: 1001
   96  ' | sudo tee /etc/apt/preferences.d/mozilla-firefox
   97  cat /etc/apt/preferences.d/mozilla-firefox
   98  echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox
   99  sudo apt install firefox
  100  sudo snap remove firefox
  101  snap list
  102  sudo apt autoremove --purge snapd
  103  snap list
```

---

### Post by Crimple on 2022-04-30
There's also this tutorial:

[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)

---

### Post by vanadium on 2022-05-03
If you want to keep snap, but prevent installation of firefox snap, stopping at line
```

cat /etc/apt/preferences.d/mozilla-firefox

``` 
(line 97 of Oldfred's output) should be enough. This prioritizes the package "firefox" from the PPA of mozilla over that of Ubuntu. Priority indeed must be high enough - 1001. A value of '501' appears not to work (default is 500).

That allows you to maintain the option to install some other apps through snap.

Optionally, also include the next line, which allows the mozilla firefox package to be updated fully automatically in the background without confirmation.

---

