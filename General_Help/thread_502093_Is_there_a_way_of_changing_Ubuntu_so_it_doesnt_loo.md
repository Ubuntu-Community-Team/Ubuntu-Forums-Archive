---
title: "Is there a way of changing Ubuntu so it doesnt look for Pam config file at startup?"
date: 2007-07-16
forum: General Help
---

### Post by IAmALinuxFool on 2007-07-16
Hi,

I had problems with keyring manager so install pam, but every 2-3 seconds a box would come up with "failed to authenticate" which made it impossible to do anything so i booted to recovery mode and rm'd the contents of /etc/pam.d now i get a blue screen on start up saying "can't find pam config file" and get sent to command line. I've tried a number of things and none have worked, so i was wondering if theres something i can edit so Ubuntu doesnt look for Pam on startup, really trying to avoid a fresh install - just got Ubuntu set up the way i like it!

TIA,

Dan.

---

### Post by TheFoe92 on 2007-07-16
How did you get this pam? If you got from the terminal you could just type in: ```
sudo apt-get remove *
``` where the star is the name of the program that you used to install it in the first place. If you didn't get it from terminal, where did you get it from?

---

### Post by NilsE on 2007-07-16
Try to Re-Install libpam:

In terminal which it sounds like that is all you have. Might work without a network connection since it may be cached
```

sudo aptitude install libpam-keyring
```

If it installs then do the following:

```
sudo echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm

NOTE: This will use your login password for keyring and allow you to remember
connection passwords/keys in the keyring and not get prompted by the keyring
manager every time.

```

---

### Post by sisco311 on 2007-07-16
1.) boot with the *init=/bin/bash *kernel option
2.) obtain a list of packages which you need to reinstall
```
grep /etc/pam.d /var/lib/dpkg/info/*.list
```3.) reinstall the packages with [I]apt-get -o DPkg::Options::="--force-confmiss" --reinstall install
4.) [/I]```
cp /usr/share/pam/common-account /etc/pam.d/
cp /usr/share/pam/common-auth /etc/pam.d/
cp /usr/share/pam/common-session /etc/pam.d/
cp /usr/share/pam/common-password /etc/pam.d/
```
5.) reboot

---

### Post by IAmALinuxFool on 2007-07-18
I just noticed that people responded to this thread - I've already reinstalled Ubuntu but thanks for the responses!

Dan

---

