---
title: "Problems on installing update in Ubuntu 16.04"
date: 2016-05-11
forum: General Help
---

### Post by Semn on 2016-05-11
Hello, I have upgraded from 15.04 to 16.04 and the installation has left a problem in the update program giving this reply on sudo apt update:

```
Building dependency tree       
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:97
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:104
W: [http://archive.canonical.com/dists/precise/Release.gpg:](http://archive.canonical.com/dists/precise/Release.gpg:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:25 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:17 and /etc/apt/sources.list:50
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:97
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list:96
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:49 and /etc/apt/sources.list:104
```



How can this be fixed?

---

### Post by bluepicaso2 on 2016-05-12
i have same problem.
But it has hapend today after switching from `main server ` to `best server`
below is my list
```

W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: GPG error: http://ppa.launchpad.net/mystic-mirage/komodo-edit/ubuntu xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DD969F10A7E2BCD2
W: The repository 'http://ppa.launchpad.net/mystic-mirage/komodo-edit/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: There is no public key available for the following key IDs:
DD969F10A7E2BCD2  
W: GPG error: http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A7D1D38BEB6D886
W: The repository 'http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04  Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: There is no public key available for the following key IDs:
5A7D1D38BEB6D886  
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
W: The repository 'http://ppa.launchpad.net/alexeftimie/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/synapse-core/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/tiheum/equinox/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/xenial/main/binary-i386/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/synapse-core/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/synapse-core/ppa/ubuntu/dists/xenial/main/binary-i386/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/xenial/main/binary-i386/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1



```
please help

---

### Post by grahammechanical on 2016-05-12
Both of you have 

> is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:50

So, you need to edit /etc/apt/sources.list and either comment out duplicate entries in sources.list by putting # at the front of the lines or by deleting the duplicate. I would comment out the lines and test that everything works before deleting.

@ bluepicaso2, you have an additional problem.

> Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found

Disable those PPAs and that error message will go away. As for the Google warning

> W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)

That is common. I get that. The Ubuntu developers now prefer software developers to use a stronger encryption algorithm (SHA2) rather than SHA1. And Google has yet to do that. And so we get a warning.

Regards.

---

### Post by bluepicaso2 on 2016-05-12
but these 404 suddenly came today, which is weird.
is there something to do with sever change from  software settings?

---

