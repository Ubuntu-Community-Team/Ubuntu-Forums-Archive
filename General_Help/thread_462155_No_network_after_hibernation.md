---
title: "No network after hibernation"
date: 2007-06-02
forum: General Help
---

### Post by Firminator on 2007-06-02
Hello. 
I run the 7.04 an after waking up from hibernate mode, it can't remount the network adapter thus I have to reboot in order to have internet access. I have an old Intel mother board with  my network card on it. i use a router hub. and I hadn't have this problem on the 6.04. 
I installed and after wards removed the KDE desktop. I had Gnome before and now.

regards.

---

### Post by louieb on 2007-06-02
I have the same feature. on my laptop to get it going again i use a terminal and 
```
 
sudo ifdown eth0 
sudo ifup eth0  

```
That usually get it going without doing a reboot.

---

### Post by Firminator on 2007-06-03
Is there  a permanent solution for this problem? some thing like reinstalling the network adapter? If so how can I do this, I am a beginner  with Linux.

 I simply don't want to do anything every time my computer wakes-up from hibernation, I can as well shut down every time I leave my computer not working.

thanks anyhow.

---

### Post by kingmob on 2007-06-03
I also have some problems with my network as well. The 'best' solution i have thought of so far is to write a little script like this:
```

#!/bin/sh
ifdown eth0
ifup eth0

```
And run it with sudo. 
You could link this on the desktop as well and hopefully it should just ask you for the root-password. I think this could also be added to a runlevel that will get accessed when you get back out of hibernation, but i'm unsure how that works.

---

### Post by Firminator on 2007-06-03
Is there away to add this script segment to some sort of bigger script which is being ran while the computer wakes-up from hibernation, because its a bummer to run a script every time i wake up from hibernation.

---

### Post by kingmob on 2007-06-03
> **Firminator said:**
> Is there away to add this script segment to some sort of bigger script which is being ran while the computer wakes-up from hibernation, because its a bummer to run a script every time i wake up from hibernation.

That is this:
```

I think this could also be added to a runlevel that will get accessed when you get back out of hibernation, but i'm unsure how that works.

```
I have however not enough knowledge (yet) about runlevels to help you with this. /etc/event.d/rcS.d should contain something like S40Networking (going from memory here, i am at work). This makes sure your networks starts at boot and does something similar as "ifup eth0". Apparently your network is properly shutdown, but not activated again when waking up. It could be you have to add it to some other runlevel (rc2-5?), but that would be on your own risk, because i'm out on a limb here and have no knowledge what happens during hibernation and wakeup.
If you have the time and heart, you could read up what hibernation does to these runlevels, it might provide you the solution.

---

