---
title: "Problems updating seeing exclamation bar in triangle in task bar."
date: 2015-06-27
forum: General Help
---

### Post by thedoctor818772 on 2015-06-27
I am running Ubuntu 15.04 on an Acer Aspire M laptop and am seeing (in the task bar) an exclamation bar inscribed in a red triangle. I have tried updating and get the following:

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/vivid/InRelease  


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/vivid-security/InRelease  


W: Failed to fetch http://deb.opera.com/opera-stable/dists/stable/InRelease  

```

I presume this has something to do with what I am seeing. Could someone please advise me on how to fix this issue? Thanks.

---

### Post by sandyd on 2015-06-27
Could be corrupt package list.

Try
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by thedoctor818772 on 2015-06-27
Now I get the following:

```

Err http://linux.dropbox.com vivid InRelease                                                                          
  
Err http://www.geogebra.net stable InRelease                                                                          
  
Err http://dl.google.com stable InRelease

```

and also:

```

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/vivid/InRelease  


W: Failed to fetch http://www.geogebra.net/linux/dists/stable/InRelease  


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  


W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://dl.google.com/linux/talkplugin/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/talkplugin/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages)

```

---

### Post by cstrife89 on 2015-06-29
> **sandyd said:**
> Could be corrupt package list.

Try
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

To add, to thedoctor's post, after doing that, I checked the contents of /var/lib/apt/lists.

```

thedoctor818@TARDIS:~$ ls /var/lib/apt/listsdeb.opera.com_opera-stable_dists_stable_non-free_binary-amd64_Packages
deb.opera.com_opera-stable_dists_stable_non-free_binary-i386_Packages
deb.opera.com_opera-stable_dists_stable_Release
deb.opera.com_opera-stable_dists_stable_Release.gpg
dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages
dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages
dl.google.com_linux_chrome_deb_dists_stable_Release
dl.google.com_linux_chrome_deb_dists_stable_Release.gpg
dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-amd64_Packages
dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages
dl.google.com_linux_talkplugin_deb_dists_stable_Release
dl.google.com_linux_talkplugin_deb_dists_stable_Release.gpg
linux.dropbox.com_ubuntu_dists_vivid_main_binary-amd64_Packages
linux.dropbox.com_ubuntu_dists_vivid_main_binary-i386_Packages
linux.dropbox.com_ubuntu_dists_vivid_Release
linux.dropbox.com_ubuntu_dists_vivid_Release.gpg
lock
partial
ppa.launchpad.net_ci-train-ppa-service_landing-001_ubuntu_dists_vivid_main_binary-amd64_Packages
ppa.launchpad.net_ci-train-ppa-service_landing-001_ubuntu_dists_vivid_main_binary-i386_Packages
ppa.launchpad.net_ci-train-ppa-service_landing-001_ubuntu_dists_vivid_main_i18n_Translation-en
ppa.launchpad.net_ci-train-ppa-service_landing-001_ubuntu_dists_vivid_Release
ppa.launchpad.net_ci-train-ppa-service_landing-001_ubuntu_dists_vivid_Release.gpg
ppa.launchpad.net_m.br_cockatrice_ubuntu_dists_vivid_main_binary-amd64_Packages
ppa.launchpad.net_m.br_cockatrice_ubuntu_dists_vivid_main_binary-i386_Packages
ppa.launchpad.net_m.br_cockatrice_ubuntu_dists_vivid_main_i18n_Translation-en
ppa.launchpad.net_m.br_cockatrice_ubuntu_dists_vivid_Release
ppa.launchpad.net_m.br_cockatrice_ubuntu_dists_vivid_Release.gpg
ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_vivid_main_binary-amd64_Packages
ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_vivid_main_binary-i386_Packages
ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_vivid_main_i18n_Translation-en
ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_vivid_Release
ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_vivid_Release.gpg
security.ubuntu.com_ubuntu_dists_vivid-security_main_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_vivid-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_vivid-security_main_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_vivid-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_vivid-security_multiverse_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_vivid-security_multiverse_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_vivid-security_multiverse_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_vivid-security_multiverse_source_Sources
security.ubuntu.com_ubuntu_dists_vivid-security_Release
security.ubuntu.com_ubuntu_dists_vivid-security_Release.gpg
security.ubuntu.com_ubuntu_dists_vivid-security_restricted_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_vivid-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_vivid-security_restricted_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_vivid-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_vivid-security_universe_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_vivid-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_vivid-security_universe_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_vivid-security_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_multiverse_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_multiverse_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_Release
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_universe_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid-backports_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid_Release
us.archive.ubuntu.com_ubuntu_dists_vivid_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_vivid_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid_universe_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_Release
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_universe_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_vivid-updates_universe_source_Sources
www.geogebra.net_linux_dists_stable_main_binary-amd64_Packages
www.geogebra.net_linux_dists_stable_main_binary-i386_Packages
www.geogebra.net_linux_dists_stable_Release
www.geogebra.net_linux_dists_stable_Release.gpg
thedoctor818@TARDIS:~$ 
```

I double-checked after that; the directory is definitely empty before apt-get update. Not sure what's going on.

---

### Post by monkeybrain20122 on 2015-06-29
Failed to fetch can happen simply because server is down on the other end. I won't worry about it unless it is persistent over a few days. Just wait a few hours and try again.
Also you have two entries for the same google repo in your sources. Just remove one of them. Easy way, search Software & Updates from the dash, open it, go to "Other Software" tab, right click to highlight one of the duplicated google entries and choose remove.

---

