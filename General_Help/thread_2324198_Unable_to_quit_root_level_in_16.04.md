---
title: "Unable to quit root level in 16.04"
date: 2016-05-11
forum: General Help
---

### Post by Mike_Andrews on 2016-05-11
I've gotten myself into a jam it seems, after installing tiger.
Tried using root to open tiger comments folder, which is locked; no soap.
Ran sudo passwd -dl root as instructed via wiki to return to standard user, but root is apparently still running.
Terminal output: ```
mike@mike-Kudu-Professional:~$ sudo passwd -dl root     [passwd: password expiry information changed.]
mike@mike-Kudu-Professional:~$ 

```
And now, when I load bleachbit (as root) a new login interface appears, similar to Windows login boxes, with NO TERMINAL -- whereas B4, terminal appeared together with the bleachbit gui and my login was to Terminal. 
Additionally, bleachbit no longer cleans Firefox and T-bird, nor X-11.
On the bleachbit interface, right window, a dialog appears: "You are running BleachBit with administrative privileges for cleaning shared parts of the system, and references to the user profile folder will clean only the root account."
Terminal indicates that I am not root, as the symbol for root user (#) is not present, but is a $.
I reloaded Synaptic P.M. cache and reinstalled any/all upgrades to bleachbit; no help.

After initial run of tiger following installation a folder named tiger was created in which all comments regarding status are recorded. But I have been unable to open the var/log/tiger folder as it is root-owned and despite all efforts, will not budge, even when using terminal cmd: sudo chown -R mike:mike /var/log/tiger. Terminal says there is no such file or folder.
I know I'm doing something wrong, and I've tried my best to figure out what it is; but if someone would kindly throw me some crumbs I'd be grateful.

---

### Post by QDR06VV9 on 2016-05-11
> **Mike_Andrews said:**
> I've gotten myself into a jam it seems, after installing tiger.
Tried using root to open tiger comments folder, which is locked; no soap.
Ran sudo passwd -dl root as instructed via wiki to return to standard user, but root is apparently still running.
Terminal output: mike@mike-Kudu-Professional:~$ sudo passwd -dl root     [passwd: password expiry information changed.]
mike@mike-Kudu-Professional:~$ 

And now, when I load bleachbit (as root) a new login interface appears, similar to Windows login boxes, with NO TERMINAL -- whereas B4, terminal appeared together with the bleachbit gui and my login was to Terminal. 
Additionally, bleachbit no longer cleans Firefox and T-bird, nor X-11.
On the bleachbit interface, right window, a dialog appears: "You are running BleachBit with administrative privileges for cleaning shared parts of the system, and references to the user profile folder will clean only the root account."
Terminal indicates that I am not root, as the symbol for root user (#) is not present, but is a $.
I reloaded Synaptic P.M. cache and reinstalled any/all upgrades to bleachbit; no help.

After initial run of tiger following installation a folder named tiger was created in which all comments regarding status are recorded. But I have been unable to open the var/log/tiger folder as it is root-owned and despite all efforts, will not budge, even when using terminal cmd: sudo chown -R mike:mike /var/log/tiger. Terminal says there is no such file or folder.
I know I'm doing something wrong, and I've tried my best to figure out what it is; but if someone would kindly throw me some crumbs I'd be grateful.
Not sure I understood all that..but what dose this report from the terminal
```
whoami
```
And any GUI application should be ran with **"gksudo" or "gksu"**
IE:
```
gksu bleachbit
```

---

