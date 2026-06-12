---
title: "VLC under ubuntu 17.10"
date: 2018-01-22
forum: General Help
---

### Post by alain.roger on 2018-01-22
Hi,

i have an issue while i'm trying to install VLC 2.2.6-6 under ubuntu 17.10.
When i type: sudo apt install vlc=2.2.6-6 i get the following message:
```
[FONT=monospace]
The following packages have unmet dependencies:
 vlc : Depends: vlc-bin (= 2.2.6-6) but 4.0.0~rc1~~git20180121+r73720+120~ubuntu17.10.1 is to be installed
       Depends: vlc-plugin-base (= 2.2.6-6) but 4.0.0~rc1~~git20180121+r73720+120~ubuntu17.10.1 is to be installed
       Depends: vlc-plugin-qt (= 2.2.6-6) but 4.0.0~rc1~~git20180121+r73720+120~ubuntu17.10.1 is to be installed
       Depends: vlc-plugin-video-output (= 2.2.6-6) but 4.0.0~rc1~~git20180121+r73720+120~ubuntu17.10.1 is to be installed
       Depends: vlc-l10n (= 2.2.6-6) but 4.0.0~rc1~~git20180121+r73720+120~ubuntu17.10.1 is to be installed
       Recommends: vlc-plugin-notify (= 2.2.6-6) but it is not going to be installed
       Recommends: vlc-plugin-samba (= 2.2.6-6) but it is not going to be installed
       Recommends: vlc-plugin-skins2 (= 2.2.6-6) but it is not going to be installed
       Recommends: vlc-plugin-video-splitter (= 2.2.6-6) but it is not going to be installed
       Recommends: vlc-plugin-visualization (= 2.2.6-6) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/FONT][FONT=monospace]
[/FONT]
```

I do not want to use SNAP as it create mounting points always visible in dolphin and it confuses me everytime.

What should i do to have VLC install correctly in my case ?
thx

---

### Post by #&amp;thj^% on 2018-01-22
I like to use a PPA for VLC but that's just me, solves some of my needs using VLC.
PPA found here:[https://launchpad.net/~jonathonf/+archive/ubuntu/vlc](https://launchpad.net/~jonathonf/+archive/ubuntu/vlc)

Right now VLC sits at version 2.2.8 with the above PPA shown.

NOTE: if you’re trying to upgrade from VLC version older than 2.2.4, REMOVE VLC first to avoid unmet dependencies issue:

```
sudo apt-get remove vlc vlc-nox && sudo apt-get autoremove
```
This has helped me and others when met with unmet dependencies issue.

---

### Post by tinylagarto on 2018-01-22
You have a PPA or some kind of external repo enabled for VLC because the version in Ubuntu 17.10 is at 2.2.6-6. 
First you have to remove that repo and the install VLC again. 

You could open the Software Properties app and look under 'Other Programs' and remove the repo, then reload and install VLC.

---

### Post by mc4man on 2018-01-22
This ppa was used, either continue to use or remove the ppa & remove every single vlc source package that was installed from it.
(- or have that ppa enabled & use ppa-purge, manual removal might go better.
[https://launchpad.net/~videolan/+archive/ubuntu/master-daily](https://launchpad.net/~videolan/+archive/ubuntu/master-daily)

---

