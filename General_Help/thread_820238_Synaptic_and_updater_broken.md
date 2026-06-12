---
title: "Synaptic and updater broken"
date: 2008-06-06
forum: General Help
---

### Post by FrankVdb on 2008-06-06
I de-installed some software from a Ubuntu box that I'll be using as a server. This went alright until it tried to remove Totem. I think it got stuck at totem-common. Synaptic locked up and now it now longer starts, i.e. it tries to start but exits after a couple of seconds.

Is this a Gnome problem?

The strange thing is that running sudo synaptic in a terminal fires up synaptic without any hassle.
I can install software from there but I can't seem to update my system with a couple of important updated that are available. I tried sudo apt-get update and then sudo apt-get upgrade but this only updates software, not system files.

I've searched the forums but I can't find any relevant posts...

Thanks in advance for any input.

---

### Post by FrankVdb on 2008-06-06
I just tried sudo update-manager in a terminal and the update manager just works and updates my system...

In summary: starting update manager and synaptic from Gnome doesn't work, starting them from the command line works.

---

### Post by drs305 on 2008-06-06
You may have a corrupted /etc/hosts file. The following has worked for many people who have similar symptoms.

Backup and inspect your current hosts file.
```

sudo cp /etc/hosts /etc/hosts.bak1
gksudo gedit /etc/hosts

```
There should be a line that looks like this. The computer name should match the results of the first entry, with no additions such as .network, .web, .local, etc. :
```
127.0.1.1  **your-computer-name**
```

---

