---
title: "Stop Chromium updates"
date: 2019-04-06
forum: General Help
---

### Post by s9032g@comcast.net on 2019-04-06
Using 18.10. Have Chrome stable. Uninstalled Chromium but updates keep coming. I tried apt-mark without success. Also tried dpkg set-selections. Better idea? Thanks

---

### Post by #&amp;thj^% on 2019-04-06
Can you post those commands you used for both, apt-mark and  dpkg set-selections. 
Could be just a syntax error
Also please show this:
```
apt-mark showhold
```

Blocking Package Updates Using APT Preferences File

Another way to block updates of a specific package is to add its entry in /etc/apt/preferences or /etc/apt/preferences.d/official-package-repositories.pref file. This file holds the responsibility of updating or blocking certain package updates according to priority specified by the user.

To block the package, you just need to enter its name, additional feature, and to what priority you want to take it to. Here, priority < 1 would block the package.

For blocking any package, just enter its details in file /etc/apt/preferences like this:

Package: <package-name> (Here, '*' means all packages)
Pin: release *
Pin-Priority: <less than 0>

For example to block updates for package apache2 add the entry as shown:
```
Package: apache2
Pin: release o=Ubuntu
Pin-Priority: 1
```

---

### Post by Frogs Hair on 2019-04-06
The synaptic package manager has a hold version option.

---

### Post by ajgreeny on 2019-04-06
If you don't use, and don't intend to use chromium in future, you could simply uninstall it.

I do not use Ubuntu so I don't know what other packages it may remove at the same time, so be prepared to abandon the removal if it also takes something you want to keep.
It is quite possible that the removal of chromium might also take **ubuntu-desktop** package, though chromium does not seem to be a dependency of it so I suspect it will not, and disastrous though that may sound, it is not absolutely necessary as it's just a metapackage, ie a list of all packages that must be installed if the ubuntu-desktop package is installed; removing it will not mean that you lose the desktop of your Ubuntu.

However, why is the updating of chromium a problem for you? Doing so costs nothing more than a few 10s of megabytes of downloads every now and then; keeping it updated does not, and never will, slow down your computer or cause other difficulties.

---

### Post by maglin2 on 2019-04-06
The OP says in post 1 that they have already uninstalled Chromium.

> [COLOR=#000000]s9032g@comcast.net[/COLOR]
[COLOR=#000000][INDENT]**Stop Chromium updates**
Using 18.10. Have Chrome stable. Uninstalled Chromium but updates keep coming. I tried apt-mark without success. Also tried dpkg set-selections. Better idea? Thanks[/INDENT]
[/COLOR]


Possibly originally a snap version and a repository version?

---

### Post by Impavidus on 2019-04-07
Chromium consists of multople packages. Did you remove all of them? Try autoremove:```
sudo apt autoremove
```That should remove packages that were installed as dependencies of chromium, but were not removed at the same time. If it doesn't work, try this:```
sudo apt remove chromium-*
```Have a look at the list of packages to be removed and abort if you see something unexpected.

---

### Post by s9032g@comcast.net on 2019-04-07
Frogs Hair:

I am looking in synaptic but I don't see what you are referring to

---

### Post by Frogs Hair on 2019-04-07
Under package in the top left menus there is a lock version check box. Navigate to to package/s you want to lock.

---

### Post by s9032g@comcast.net on 2019-04-08
Ok Thanks

---

### Post by s9032g@comcast.net on 2019-04-08
Frogs Hair:

I looked at synaptic and looked up the Lock business. Apparently it is intended to install a program, using synaptic,  AND lock it i.e. prevent synaptic from updating it. In my case I uninstalled Chromium and I don't want it back: also I don't always use synaptic to do updates. If I use software updater it would update anyway. 
I think that I found another way to prevent updating programs that have been deleted.

---

### Post by PaulW2U on 2019-04-10
> **Frogs Hair said:**
> Under package in the top left menus there is a lock version check box. Navigate to to package/s you want to lock.
> **s9032g@comcast.net said:**
> Apparently it is intended to install a program, using synaptic,  AND lock it i.e. prevent synaptic from updating it.
Just for the record the issue of different package management applications not recognising each other's preferences was raised as long ago as **2006** in bug report [#42178]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178").

Comment [#1]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178/comments/1") of the aforementioned bug report confirms the removal of a feature that is probably desired or assumed to exist by many synaptic users.

---

### Post by #&amp;thj^% on 2019-04-10
> **PaulW2U said:**
> Just for the record the issue of different package management applications not recognising each other's preferences was raised as long ago as **2006** in bug report [#42178]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178").

Comment [#1]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178/comments/1") of the aforementioned bug report confirms the removal of a feature that is probably desired or assumed to exist by many synaptic users.

+1 I too was going to mention this, Thanks PaulW2U now I don't have to. :)
CLI for me to many GUI bugs.

---

