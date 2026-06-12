---
title: "Proftpd in updates"
date: 2006-10-17
forum: General Help
---

### Post by sefs on 2006-10-17
Hi all.

Is anyone having problems with proftpd updating in this mornings updates?

There seems to be an update for it, but I get this message....

///
Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.
///

When I do sudo apt-get dist-upgrade i get this message 
```

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  proftpd
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

I go into synaptic and see two proftpd lines one with a star on it.  If i try to install it it sticks there at the downloading dialog box and nothing happens.

What do i do.

Thanks.

---

### Post by vidak on 2006-10-17
There is a proftpd-common (or something similar) package, which should be deleted during upgrading, and this is not done by default. I got the same problem, but after pressing 'request upgrade' in adept, the ...common package was selected for removing and proftpd for upgrade. There should be something similar in synaptic/aptitude too...
There are some modifications in the config syntax, this should be checked during/after install - check if the ftpd is running, and you can log on your host through ftp.

---

### Post by sefs on 2006-10-17
Thank you.  That was very helpful.

> **vidak said:**
> There is a proftpd-common (or something similar) package, which should be deleted during upgrading, and this is not done by default. I got the same problem, but after pressing 'request upgrade' in adept, the ...common package was selected for removing and proftpd for upgrade. There should be something similar in synaptic/aptitude too...
There are some modifications in the config syntax, this should be checked during/after install - check if the ftpd is running, and you can log on your host through ftp.

---

