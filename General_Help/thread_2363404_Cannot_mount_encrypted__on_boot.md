---
title: "Cannot mount encrypted / on boot"
date: 2017-06-09
forum: General Help
---

### Post by usernameroot on 2017-06-09
Hi, i have a big problem
I made a mistake in Ubuntu and I can't login (The disk drive for / is not ready yet or not present, press s to skip mounting or m for manual recovery... "S"=nop.. error. "M" : root filesystem check failed. A maintenance shell will now be started. Cannot open acces to console, the root account is locked. See sulogin(8) for more détails. press enter to continue. -> reboot..)
So I launched the live-usb version to be able to retrieve data from "home" because I have important data
But .. it is encrypted: THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA. "blabla"
Then I run the command "ecryptfs-recover-private", It asks me for my password and my "mount" passphrase
I write it, ok, and, "INFO: Success! Private data mounted at [tmp/ecryptfs.X33nAJBh].
But... When i go to "tmp/ecryptfs.X33nAJmBh", i can't open this (permission), It is also encrypted ...
Pls help me... I have important data, thanks lot :/

---

