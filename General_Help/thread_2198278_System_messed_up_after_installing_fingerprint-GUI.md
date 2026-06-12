---
title: "System messed up after installing fingerprint-GUI"
date: 2014-01-08
forum: General Help
---

### Post by DrScum on 2014-01-08
accidentally I ran into [http://askubuntu.com/questions/111334/login-using-fingerprint-reader](http://askubuntu.com/questions/111334/login-using-fingerprint-reader) and gave it a try. Unfortunately I installed and uninstalled the package before I read the more detailed instructions here [https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui) especially the part about uninstalling.

My problem now is that I can't login with my regular user name anymore, however, I enabled my system for root login, which still works. Thus I can get into the system for fixing it. I don't know however, what I have to do in order to fix the problem.

According to the link mentioned above this is what happens:

"The package policykit-1-fingerprint-gui replaces GNOME's standard PolicyKit daemon (contained in package policykit-1-gnome). However, when you decide to uninstall Fingerprint GUI (and hence remove policykit-1-fingerprint-gui), policykit-1-gnome will not get automatically installed back, hence there won't be any PolicyKit daemon in the system, and APT will try to remove all the packages that depend on it. Therefore, if you want to remove Fingerprint GUI, make sure you install policykit-1-gnome back first.
   sudo apt-get install policykit-1-gnome
   sudo apt-get remove fingerprint-gui"

I didn't install the package policykit-1-gnome before removing fingerprint-gui! What can I do to restore the system?

---

### Post by Bucky Ball on 2014-01-08
Open a terminal and:

```
sudo apt-get install policykit-1-gnome
sudo apt-get remove fingerprint-gui
```

Just go for the first command if you've already done the second (which it sounds like you have). Reboot. You may still have issues but at least you'll have a policykit. That's why your user has gone. The lack of policykit has probably trashed a heap of stuff. Never know, that might get it back, but then again, this may be irreparable.

---

### Post by DrScum on 2014-01-08
I didn't exactly "loose the user", in the logon window the user is available, along with a third user I created and the "logon" option. I can logon as the third user (restricted account) and I can logon as root. If I try to logon to my normal account, the screen goes to console for a second (I can't read the messages appearing) and returns to the logon window.

If I logon as root, I can su to my normal account.

I can also logon to my normal account from a tty terminal.

If I do what you suggest above, this is what I get:
policykit-1-gnome is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-unique-3.0 linux-headers-3.2.0-53 libjlayer-java kunststoff
  linux-headers-3.2.0-53-generic linux-image-3.2.0-53-generic libjcifs-java
  linux-headers-3.2.0-53-generic-pae libfprint0 libyanfs-java libfakekey0
  linux-image-3.2.0-53-generic-pae libj2ssh-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

But I still can't logon to my normal account.

---

