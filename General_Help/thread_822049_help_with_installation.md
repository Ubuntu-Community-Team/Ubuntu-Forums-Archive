---
title: "help with installation"
date: 2008-06-07
forum: General Help
---

### Post by runandjump on 2008-06-07
I've had Edubuntu for a while now, and any time I try and install something, either from the Add/Remove Programs or the Internet, I can't. When I try and install something from the Add/Remove programs, nothing happens. When I try and install something from the internet, it goes to the package installer, and then a message pops up telling me that synaptic or one of the other package managing programs is running, and I have to close it before I can install. I don't have any other programs like that running, so what do I do?

---

### Post by avtolle on 2008-06-07
Dumb question here, but I'm notorious for such: have you closed Add/Remove totally after using it?

---

### Post by Sef on 2008-06-07
Can you add from Synaptic or the Terminal or both?

---

### Post by drs305 on 2008-06-07
> **runandjump said:**
> I don't have any other programs like that running, so what do I do?

You can check which processes are running with:
```
ps -u **username**
ps -u root

```


For instance, the Add/Remove app is listed as "gnome-app-insta" under my username, and Synaptic is listed as "synaptic" when searched for with the 'root' variation above.

Added: Should you find any listed under the root command, you can kill the process with:
```
sudo killall appname_or_process
```
For those found with your username, you don't need to add the "sudo". Interestingly, the identified processes are sometimes truncated, so gnome-app-insta is actually killed by the command:
```
killall gnome-app-install
```

---

### Post by runandjump on 2008-06-07
haha. Yes, I've closed Add/Remove Programs. when I try and install something with the package manager I don't have anything open but firefox and rhythmbox

---

