---
title: "Never update or upgrade an encrypted UBUNTU installation?"
date: 2017-03-31
forum: General Help
---

### Post by xenon3 on 2017-03-31
To my knowledge an encrypted installation has a fixed boot sector, completely full with the 4 or 5 UBUNTU kernel versions, when you try to stuff for instance a security update in it or try to upgrade the primary kernel to the newest version, whole boot sector and all kernel versions in it gets corrupted, there is simply no space for it in the fixed size boot sector.

Moreover with an encrypted installation I had maybe 9 out of 10 times during system startup NOT the GRUB boot menu to chose alternative kernels, this is completely at random, with the specified approximate probability of 9 times out of 10, it immediately went to the encryption key entry box (encryption passphrase or something is it called).

What I advice is to disable all updates and upgrades in "Software Updater" from the programs collection, IF YOU HAVE AN ENCRYPTED INSTALLATION.

Please correct me if I'm wrong!

---

### Post by sudodus on 2017-03-31
Encrypted systems are difficult (maybe impossible) to repair, so it is very important to have a regular ***backup*** routine.

[B][I]It is possible and important to update and upgrade an encrypted system. Otherwise it will be vulnerable to attacks via the netwerk connection.
[/I][/B]
Avoid getting the boot partitions filled with old kernels. You can install the Synaptic Package Manager,

```
sudo apt-get install synaptic
```

and use it to remove old kernels, or you can use terminal window commands. Look for 'linux-image'

***Check which kernel you are running and remove all but the current one and one previous kernel.***

---

### Post by Impavidus on 2017-03-31
You've got an encrypted system because you want additional security, right? If you care about the security of your computer and all others on the internet, install those updates. Just don't forget to uninstall the old kernels. They should be autoremovable, but if necessary it can be done manually in a few seconds.

---

### Post by ian-weisser on 2017-03-31
"Don't install updates" is unwise advice. Instead, properly maintain your system - uninstall the older kernels.

In 16.04 and newer, removal of older kernels should occur automatically. If not, seek support here.

---

### Post by xenon3 on 2017-06-07
I came one day home from work and my UBUNTU installation was completely corrupt, login screen was completely different, when logged everything looked different and nothing was working, even the colors were different, so I thought I had a failed update (I changed the updater settings) I indeed got last time while it was working a message of a failed update (not a major kernel update, some kind of minor update) so I thought the fixed boot sector encrypted installation got corrupted by an update forcing himself in the fixed boot sector. But then again I also had in the three days to come, while at work, hardware damages on my main and spare computers??? So I got paranoid and thought maybe they have been in my house, maybe these are things (including corrupted installation) that malicious people only can do on the computer itself, or by USB ports attaching some device. :(

---

