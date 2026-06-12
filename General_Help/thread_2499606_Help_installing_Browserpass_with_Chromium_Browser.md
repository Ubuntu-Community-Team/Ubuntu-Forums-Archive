---
title: "Help installing Browserpass with Chromium Browser"
date: 2024-08-02
forum: General Help
---

### Post by jwoodruff on 2024-08-02
Running Ubuntu 24.04 LTS
I am attempting to switch browsers from firefox to chromium. I currently use pass password manager and passff on firefox.
Installed chromium browser and have added the browserpass extension. Also installed  [webext-browserpass]("https://packages.debian.org/sid/webext-browserpass") via "sudo apt install webtext-browserpass"
"browserpass-native" binary file exists in /usr/lib/browserpass/ (as well as "Makefile")
When using chromium-browser, either pressing ctl-shift-L or clicking extensions icon and selecting "Browserpass", "Loading available logins" pops up and just hangs - even when on a website included in the .password store files.
The passwords do work with firefox and passff.
I suspect I have to do something to configure the browserpass native messaging host but am unsure of what steps are required.
Any help appreciated
Thanks

---

### Post by #&amp;thj^% on 2024-08-02
This has been an on going bug with Chromium snap package: [https://github.com/browserpass/browserpass-native/issues/82](https://github.com/browserpass/browserpass-native/issues/82)
And: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1741074](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1741074)

If firefox works use that, or .deb version of Brave

---

### Post by jwoodruff on 2024-08-02
Thanks.

---

