---
title: "Problem installing vmware server"
date: 2007-07-30
forum: General Help
---

### Post by robert-s on 2007-07-30
I'm having trouble installing vmware server on my ubuntu feisty machine. I get the error
```
A previous installation of VMware software has been detected.

Failure

Execution aborted.
```
When I try to install from the binary downloaded from their website. I did have a version of vmware player installed once, but I uninstalled it a while ago so I'm not sure what it's complaining about. I've also tried installing it though synaptic and Add/Remove without success, it gives the same error.

---

### Post by AlexThomson_NZ on 2007-07-30
I wonder if you have a lingering directory somewhere.  I know of other apps that throw this error if there is the previous *.app_name* directory in the home directory.  Maybe check this?

---

### Post by kens8 on 2007-07-30
Found this elsewhere:

> **speakman said:**
> Or just:
```
sudo killall vmnet-natd
```

And then:
```
sudo apt-get remove --purge vmware-player
```

Did it for me...

I had the same problem and I did have a lingering directory, but I can't remember where.  Maybe /etc/vmware?  Took me forever to find it.

---

### Post by sarahsilverman on 2007-07-30
i had the same problem go to my thread where the great people helped me "http://ubuntuforums.org/showthread.php?t=512372"

---

### Post by robert-s on 2007-07-31
> **sarahsilverman said:**
> i had the same problem go to my thread where the great people helped me "http://ubuntuforums.org/showthread.php?t=512372"
Thanks very much, that thread fixed it. I needed to remove the /etc/vmware directory.

---

