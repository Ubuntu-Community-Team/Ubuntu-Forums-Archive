---
title: "Duplicate sources.list entry i386 and amd64 on amd64 from /var/lib/apt/lists/"
date: 2016-09-07
forum: General Help
---

### Post by jesusguevarautomotriz on 2016-09-07
Hi,

Please, I'm trying to fix this on Lubuntu 14.04.5 LTS, I consulted [this]("http://askubuntu.com/questions/120621/how-to-fix-duplicate-sources-list-entry") and [this]("https://ubuntuforums.org/showthread.php?t=2265723") but I'm not sure what I do and think I need assistance to get it right.

I checked my /etc/apt/sources.list file and not found duplicates, but I am not sure.

When I update via terminal I get this:
```

Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty-updates/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty-updates/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty-backports/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty-backports/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty-backports/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty-backports/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty-security/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ trusty-security/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

My source.list
```

deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security multiverse
deb http://archive.canonical.com/ubuntu trusty partner
deb http://extras.ubuntu.com/ubuntu trusty main
deb http://us.archive.ubuntu.com/ubuntu/ trusty restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security restricted
deb http://liveusb.info/multisystem/depot all main

```

Ls output from /var/lib/apt/lists/

```

apt.syncthing.net_dists_syncthing_InRelease
apt.syncthing.net_dists_syncthing_release_binary-amd64_Packages
apt.syncthing.net_dists_syncthing_release_binary-i386_Packages
archive.canonical.com_ubuntu_dists_trusty_partner_binary-amd64_Packages
archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages
archive.canonical.com_ubuntu_dists_trusty_partner_i18n_Translation-en
archive.canonical.com_ubuntu_dists_trusty_Release
archive.canonical.com_ubuntu_dists_trusty_Release.gpg
dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages
dl.google.com_linux_chrome_deb_dists_stable_Release
dl.google.com_linux_chrome_deb_dists_stable_Release.gpg
dl.google.com_linux_chrome-remote-desktop_deb_dists_stable_main_binary-amd64_Packages
dl.google.com_linux_chrome-remote-desktop_deb_dists_stable_Release
dl.google.com_linux_chrome-remote-desktop_deb_dists_stable_Release.gpg
dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-amd64_Packages
dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages
dl.google.com_linux_talkplugin_deb_dists_stable_Release
dl.google.com_linux_talkplugin_deb_dists_stable_Release.gpg
extras.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
extras.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages
extras.ubuntu.com_ubuntu_dists_trusty_Release
extras.ubuntu.com_ubuntu_dists_trusty_Release.gpg
linux.dropbox.com_ubuntu_dists_trusty_main_binary-amd64_Packages
linux.dropbox.com_ubuntu_dists_trusty_main_binary-i386_Packages
linux.dropbox.com_ubuntu_dists_trusty_Release
linux.dropbox.com_ubuntu_dists_trusty_Release.gpg
liveusb.info_multisystem_depot_dists_all_main_binary-amd64_Packages
liveusb.info_multisystem_depot_dists_all_main_binary-i386_Packages
liveusb.info_multisystem_depot_dists_all_Release
liveusb.info_multisystem_depot_dists_all_Release.gpg
lock
partial
ppa.launchpad.net_djcj_screenfetch_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_djcj_screenfetch_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_djcj_screenfetch_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_djcj_screenfetch_ubuntu_dists_trusty_Release
ppa.launchpad.net_djcj_screenfetch_ubuntu_dists_trusty_Release.gpg
ppa.launchpad.net_gezakovacs_ppa_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_gezakovacs_ppa_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_gezakovacs_ppa_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_gezakovacs_ppa_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_libreoffice_libreoffice-5-0_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_libreoffice_libreoffice-5-0_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_libreoffice_libreoffice-5-0_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_libreoffice_libreoffice-5-0_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_mc3man_trusty-media_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_mc3man_trusty-media_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_mc3man_trusty-media_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_mc3man_trusty-media_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_openshot.developers_ppa_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_openshot.developers_ppa_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_openshot.developers_ppa_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_openshot.developers_ppa_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_peterlevi_ppa_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_peterlevi_ppa_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_peterlevi_ppa_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_peterlevi_ppa_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_phablet-team_tools_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_phablet-team_tools_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_phablet-team_tools_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_phablet-team_tools_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_remmina-ppa-team_remmina-next_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_remmina-ppa-team_remmina-next_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_remmina-ppa-team_remmina-next_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_remmina-ppa-team_remmina-next_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_sandromani_gimagereader_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_sandromani_gimagereader_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_sandromani_gimagereader_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_sandromani_gimagereader_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_thomas.tsai_ubuntu-tuxboot_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_thomas.tsai_ubuntu-tuxboot_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_thomas.tsai_ubuntu-tuxboot_ubuntu_dists_trusty_Release
ppa.launchpad.net_thomas.tsai_ubuntu-tuxboot_ubuntu_dists_trusty_Release.gpg
ppa.launchpad.net_ubuntuhandbook1_apps_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_ubuntuhandbook1_apps_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_ubuntuhandbook1_apps_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_ubuntuhandbook1_apps_ubuntu_dists_trusty_main_i18n_Translation-en
ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_trusty_InRelease
ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_trusty_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_InRelease
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty_Release
us.archive.ubuntu.com_ubuntu_dists_trusty_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-security_InRelease
us.archive.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-security_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-security_multiverse_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-security_universe_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_i18n_Translation-en

```

Can I delete safe entries reported as duplicated at the end of as apt-get update  from /var/lib/apt/lists/? 
Delete i386 entries does this affect the multiarch support required for Teamviewer?
Thanks

---

### Post by howefield on 2016-09-07
Try creating a fresh sources.list..

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
```

to make a backup copy of your existing sources.list, then..

Open the Software and Updates application and check off the first 4 options on the *Ubuntu Software* tab, and if you wish the Canonical Partners repository from the *Other Software* tab and the backports repository from the *Updates* tab.

Close out and save, you should be prompted to reload your Software sources but if not, do a sudo apt-get update and post back with any errors.

---

### Post by jesusguevarautomotriz on 2016-09-07
My "Software and Updates" and "Software Updater" apps is broken since some time.

I try open "Software and Updates": Sorry, Ubuntu 14.04 has experienced an internal errror.
I try open "Software Updater": Crash Report, The application Software Updater has closed unexpectedly.

I Always  have to use the terminal for install, uninstall and updates.

---

### Post by howefield on 2016-09-07
OK, create the backup file as above and try creating a new file with the contents as follows.

```
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse 
```

If you don't know how to create the new file, just say.

---

### Post by jesusguevarautomotriz on 2016-09-07
Solved!, sudo apt-get update works well, no more error about duplicates.

Thanks for your answers,

---

### Post by howefield on 2016-09-07
You are very welcome.

Just to add that if you still need the liveusb.info/multisystem/depot repository it would need to be added back in to your sources.list, if you no longer use it, then forget it :)

Lastly, if Software and Update ect is still not working after fixing the sources.list feel free to post with the error(s).

---

### Post by jesusguevarautomotriz on 2016-09-07
Thanks,
Added mutltisystem to sources.list

Software & Updates and Software Updater still not working, same errors. I tried unninstall and reinstall but not luck. How could I fix this?

---

### Post by howefield on 2016-09-07
I'd suggest starting a new thread for this separate problem with the output from starting the applications via the terminal, ie...

```
software-properties-gtk
```
```
update-manager
```

There may be useful errors in the terminal output for someone who can help.

---

