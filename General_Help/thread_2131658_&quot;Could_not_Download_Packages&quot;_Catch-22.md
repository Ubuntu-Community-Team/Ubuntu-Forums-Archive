---
title: "&quot;Could not Download Packages&quot; Catch-22"
date: 2013-04-02
forum: General Help
---

### Post by zerubbabel on 2013-04-02
It all began when Chromium insisted on installing the "Unity WebApps" plugin, and I ended up with "unity-chromium-extension" being flagged as "broken", but I can't remove it with the package manager because it give me the message "Could not download packages." 

So I launch a terminal window and try "sudo apt-get -f install", tells me: "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

So I do that. which tell me:
> dpkg: dependency problems prevent configuration of unity-chromium-extension:
 unity-chromium-extension depends on unity-webapps-service; however:
  Package unity-webapps-service is not installed.

dpkg: error processing unity-chromium-extension (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 unity-chromium-extension

Then I try the "sudo apt-get -f install" again, and it gives me:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  geoclue geoclue-ubuntu-geoip libdee-1.0-4 libgee2 libjson-glib-1.0-0
  libmessaging-menu0 libpackagekit-glib2-14 libunity-common
  libunity-protocol-private0 libunity-webapps0 libunity9 libwnck-3-0
  libwnck-3-common libxres1 ttf-mscorefonts-installer unity-webapps-service
Suggested packages:
  unity-common
The following NEW packages will be installed:
  geoclue geoclue-ubuntu-geoip libdee-1.0-4 libgee2 libjson-glib-1.0-0
  libmessaging-menu0 libpackagekit-glib2-14 libunity-common
  libunity-protocol-private0 libunity-webapps0 libunity9 libwnck-3-0
  libwnck-3-common libxres1 unity-webapps-service
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 15 newly installed, 0 to remove and 13 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,045 kB of archives.
After this operation, 3,980 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

But if I answer "Y", it proceeds to the point where it shows an end-user license agreement for "ttf-mscorefonts-installer" with an "<ok>" at the end, but no response is accepted. Unless I close the terminal window, it won't go away. But if I close the terminal window, then I'm back to square one:
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)

How can I get out of this Catch-22?

---

### Post by ibjsb4 on 2013-04-02
For ttf-mscorefonts-installer check out post #7 in both links.

[https://answers.launchpad.net/ubuntu/+source/msttcorefonts/+question/158185](https://answers.launchpad.net/ubuntu/+source/msttcorefonts/+question/158185)

[https://bugs.launchpad.net/netflix-desktop/+bug/1089976](https://bugs.launchpad.net/netflix-desktop/+bug/1089976)

---

### Post by oldos2er on 2013-04-02
In order to accept the EULA you need to hit Tab or use the arrow keys to highlight 'Ok' then hit Enter. After that run ```
sudo apt-get install -f
```

---

### Post by zerubbabel on 2013-04-02
Thank you, Tab, Enter worked. So simple...

---

