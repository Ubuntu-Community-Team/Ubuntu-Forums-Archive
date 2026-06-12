---
title: "Firestarter Install Issue"
date: 2007-04-27
forum: General Help
---

### Post by Frihet on 2007-04-27
Fiesty. Gnome.

Installed Firefox via Synaptic. I had to create a custom launcher. That worked. I have the icon on my toolbar.

When I try to launch, I'm told I do not have permission. Sure enough, the executable is owned and can only be run by root.

I'm guessing I have to rest permissions, but do not want to do this without confirmation.

Thanks.

---

### Post by xoros on 2007-04-27
I always read that you are supposed to run it as root.

alt+f2 
gksudo firestarter

---

### Post by Frihet on 2007-04-27
Ok, that works to start the firewall. However, I still can't use the firestarter icon to get to the "control panel". This worked fine in 6.06., so there must have been something different going on.

I've got to think the package is messed up some way. Maybe I need to remove it and install it with apt as a user (if I can)?

---

### Post by Frihet on 2007-04-27
I tried apt-get. That did not help. I can only start the firewall as you suggested and the menu must stay on the desktop or the process stops (or so it seems).

Something has changed. I think I'll have to spend some time researching. I guess this is part of the Linux package at this point in time.

---

### Post by Frihet on 2007-04-27
Getting closer. Minimize to tray on close option shows the firewall to be running. I don't need the old Firestarter icon. Now, I just need to figure out how to get the boot process to start the firewall on the way up. That's probably on the list here somewhere. I don't want Voldemort scanning me while I fumble with a manual startup sequence.

---

### Post by Frihet on 2007-04-27
I think I've got it. Indeed, things have changed. Firestarter behaves differently. But, Firestarter is not the firewall. The firewall is running. The Firestarter GUI only runs when needed -- using the manual process. This, I gather, is supposed to be more secure because the app runs as root. So, I'll call it quits on this issue.

---

### Post by KrazyPenguin on 2007-04-27
No sense reinventing the wheel here.

I added a firestarter section to the ubuntuguide.org

You can find it here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall)

It basically shows how to setup Firestarter to run automatically at startup without having to enter the root password.

Good luck!!!

;-)

---

### Post by xoros on 2007-04-27
> **Frihet said:**
> Ok, that works to start the firewall. However, I still can't use the firestarter icon to get to the "control panel". This worked fine in 6.06., so there must have been something different going on.

I've got to think the package is messed up some way. Maybe I need to remove it and install it with apt as a user (if I can)?

Hmm..  I click the icon once and it pops right up.

---

### Post by nadamsieee on 2007-05-19
When I click System --> Administration --> Firestarter the GUI does not start.

I know that the daemon is running:
```
$ sudo /etc/init.d/firestarter status
 * Firestarter is running...
```

But I would like to be able to use the GUI. :(

Any ideas?

**Solved (partially):**

I had attempted to allow myself to start the Firestarter GUI without needing to enter a password:

```
$ sudo grep firestarter /etc/sudoers 
nate ALL= NOPASSWD: /usr/sbin/firestarter
```

Apparently, that setting combined with the **gksu /usr/sbin/firestarter** command fails. Commenting that line out allows me to start the Firestarter GUI just fine.

---

