---
title: "update problem"
date: 2015-12-17
forum: General Help
---

### Post by gerryw on 2015-12-17
I have had this problem for a while.

I am running Ubuntu 15.04.

When I go to install update I the updates seem to install, but I get two notices.

The first saying "System program problem detected".

The second one is "Package operation failed".

In the details section while installing I get " grub install error /usr/lib/grub/i386-pc/ modinfo.sh does'nt exist.

Any help gratefully received.

---

### Post by kc1di on 2015-12-17
That last error message indicates a grub install problem.  Is your machine 32 or 64 bit UEFI boot or MBR? 
If it's 32 bit you might try from a terminal```
sudo apt-get install grub
    sudo apt-get autoremove
``` 

in any event give us a little more info on your setup.

---

### Post by gerryw on 2015-12-17
Thanks for the Reply.

My machine is 64 bit UEFI

---

### Post by kc1di on 2015-12-17
Ok , try this in a terminal
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broken
```

(Note there is a space between status and /var/lib/dpkg)

once you done that issue the following commands:

```
sudo apt-get update
```

list any error message you get here.

---

### Post by gerryw on 2015-12-18
Thank you I think that worked.

The only thing that looked like an error message was:

"mv: missing destination file operand after ‘/var/lib/dpkg/status.broken’"

Thank you again for your help.

---

### Post by kc1di on 2015-12-18
Your Welcome , Enjoy :)

---

### Post by gerryw on 2015-12-18
Oh dear it seems to have come back worse I can not open the software center or Synaptic.

When I try to open Synaptic it comes back with:

 E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by kc1di on 2015-12-18
Ok in a terminal do this :
```
sudo mv /var/lib/dpkg/status.broken /var/lib/dpkg/status
```

Then ```
sudo apt-get update
```

Then ```
sudo apt-get autoclean
```
then try to open synaptic again.

---

### Post by gerryw on 2015-12-18
Thank you so much for taking the time to help me again,

It worked!

Have a really nice day

---

