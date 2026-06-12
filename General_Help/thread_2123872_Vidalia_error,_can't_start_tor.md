---
title: "Vidalia error, can't start tor"
date: 2013-03-09
forum: General Help
---

### Post by goodbye-windows(tm) on 2013-03-09
Hi All,

I installed vidalia and all its dependencies through synaptic.

When I tried to run vidalia (after restarting), it gave me an error message:

```


Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified.


```

I did check the path to everything listed in the 'settings', and all of them have files installed in the correct directories. I looked in the log, which is supposed to show additional info on any errors, and it was empty.

There is a tor file in /usr/sbin/tor, the file is listed as a shared library and is 1.6 MB. I'm not sure if this is the executable or not. I did look on the permissions tab of the file and it said the file was owned by root and everything is grayed out on the permissions tab.

The configuration file is also located in the proper directory, but it is a blank/empty file. The help file indicates the configuration file use is optional, so this is possibly a normal condition.

I'm running Vidalia ver 0.2.20 in a 64 bit Xubuntu 12.04. I don't have a firewall (yet).

I've read the entire help file.

Would appreciate any help.

Art

,

---

### Post by chrischan on 2014-01-17
Same for me on 64bit Ubuntu 13.10. I can execute /usr/sbin/tor on the console, but vidalia reports the error above. I tried to place "/usr/sbin/tor Ux," into the file "/etc/apparmor.d/usr.bin.vidalia" (found somewhere else) to no avail.

---

### Post by goodbye-windows(tm) on 2014-01-18
I still have the same problem and would very much like to contribute to tor!!! I have 7M internet connection. If you should hear of a fix for this, please advise me. GL.

Art

---

