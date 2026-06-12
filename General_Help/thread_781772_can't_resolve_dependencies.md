---
title: "can't resolve dependencies"
date: 2008-05-04
forum: General Help
---

### Post by tronica on 2008-05-04
i have xchat installed and i want to install xchat-systray but i get the following:

```
tronica@desktop:~$ sudo apt-get install xchat-systray
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xchat-systray: Depends: xchat (> 2.0.4) but it is not going to be installed
E: Broken packages
```

i tried using synaptic to fix it, but it doesn't help. any ideas?

---

### Post by Oldsoldier2003 on 2008-05-04
Are you trying to get the xchat notifcations to pop up in your systray? if thats the case you just need to install libnotify-bin and anble it in xchat.

```
sudo apt-get install libnotify-bin
```

As to the package you referenced I just did an apt-get install -s for the package and it is indeed uninstallable with all the Ubuntu repos installed, so there is an issue with the package.

---

### Post by tronica on 2008-05-04
thanks for the info, thats what i wanted.

---

