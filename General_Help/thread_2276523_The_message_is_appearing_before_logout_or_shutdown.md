---
title: "The message is appearing before logout or shutdown"
date: 2015-05-03
forum: General Help
---

### Post by Kaminar on 2015-05-03
Hi,

the window with this message
```

Are you sure you want to close all programs and log out?
Some software updates won't be applied until the computer next restarts.

```
appears before logout or shutdown in Ubuntu 14.04 LTS. It is not my computer, so I don't know exactly when it has started.

Does anyone have any clue where might be the problem?
Thanks in advice.

---

### Post by kc1di on 2015-05-03
It sounds as if you have pending updates that have not yet been installed.

You can try this to clear it in a terminal
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

if that produces nothing give this command a try:
```
sudo dpkg --configure -a
```

Note: you'll need to supply the users password after the first command. 
good Luck :)

---

### Post by Kaminar on 2015-05-03
I did it. But the window with the message still appears.

---

### Post by buzzingrobot on 2015-05-03
> **Kaminar said:**
> Hi,

```

Some software updates won't be applied until the computer next restarts.

```
appears before logout or shutdown in Ubuntu 14.04 LTS. It is not my computer, so I don't know exactly when it has started.


That's telling you that an update has been downloaded and applied but can't be activated until the system reboot.  These are typically kernel or driver updates or some other core system component.

If you continue to see that message after the system reboots, then something likely went wrong with the last update that was run on the machine.

---

### Post by Kaminar on 2015-05-04
Yes, the message is appearing after the system reboots. Is any possibility to find what update went wrong?

---

### Post by kc1di on 2015-05-04
I would try this also:
```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
```

if that doesn't clear the message next step would be this
```
sudo rm /var/lib/apt/lists/* -vf
```

the do ```
sudo apt-get update
```
hope it works :)

---

### Post by stalkingwolf on 2015-05-04
or try  going into synaptic package manager , click edit then fix broken.   or recovery mode and fix broken packages

---

### Post by buzzingrobot on 2015-05-04
> sudo apt-get install -f

can complete the install of packages.  Worth a try.

---

### Post by Kaminar on 2015-05-04
I did everything:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove 
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```
The message before logout is still appearing.

After run **sudo apt-get install -f** it displayed

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Logout message still appears and complains about undone updates.

---

### Post by Vladlenin5000 on 2015-05-04
After ```
sudo apt get update
``` you need to do ```
sudo apt-get upgrade
```. Did you?

If not please do it again and note down any error messages.
If you did it already, have you noticed any error message?

---

### Post by Kaminar on 2015-05-04
Yes, I did **sudo apt-get update** and then **sudo apt-get upgrade**. I didn't notice any errors.

---

