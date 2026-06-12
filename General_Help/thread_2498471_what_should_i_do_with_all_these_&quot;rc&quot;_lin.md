---
title: "what should i do with all these &quot;rc&quot; linux packages?"
date: 2024-06-14
forum: General Help
---

### Post by Skaperen on 2024-06-14
what should i do with all these "rc" linux packages i see when i do "dpkg -l|egrep -v '^ii'"?  can i safely delete them?

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                                     Architecture Description
+++-=============================================-===========================================-============-======================================================================================================
rc  linux-image-5.13.0-44-generic                 5.13.0-44.49~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-48-generic                 5.13.0-48.54~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-51-generic                 5.13.0-51.58~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-52-generic                 5.13.0-52.59~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-43-generic                 5.15.0-43.46~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-46-generic                 5.15.0-46.49~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-52-generic                 5.15.0-52.58~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-53-generic                 5.15.0-53.59~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-56-generic                 5.15.0-56.62~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-70-generic                 5.15.0-70.77~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-73-generic                 5.15.0-73.80~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-75-generic                 5.15.0-75.82~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-82-generic                 5.15.0-82.91~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-83-generic                 5.15.0-83.92~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-84-generic                 5.15.0-84.93~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-86-generic                 5.15.0-86.96~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-89-generic                 5.15.0-89.99~20.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.15.0-92-generic                 5.15.0-92.102~20.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.15.0-94-generic                 5.15.0-94.104~20.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.15.0-97-generic                 5.15.0-97.107~20.04.1                       amd64        Signed kernel image generic
rc  linux-modules-5.13.0-44-generic               5.13.0-44.49~20.04.1                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-5.13.0-48-generic               5.13.0-48.54~20.04.1                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-5.13.0-51-generic               5.13.0-51.58~20.04.1                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-5.13.0-52-generic               5.13.0-52.59~20.04.1                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-43-generic               5.15.0-43.46~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-46-generic               5.15.0-46.49~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-52-generic               5.15.0-52.58~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-53-generic               5.15.0-53.59~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-56-generic               5.15.0-56.62~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-70-generic               5.15.0-70.77~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-73-generic               5.15.0-73.80~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-75-generic               5.15.0-75.82~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-82-generic               5.15.0-82.91~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-83-generic               5.15.0-83.92~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-84-generic               5.15.0-84.93~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-86-generic               5.15.0-86.96~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-89-generic               5.15.0-89.99~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-92-generic               5.15.0-92.102~20.04.1                       amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-94-generic               5.15.0-94.104~20.04.1                       amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-97-generic               5.15.0-97.107~20.04.1                       amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.13.0-44-generic         5.13.0-44.49~20.04.1                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.13.0-48-generic         5.13.0-48.54~20.04.1                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.13.0-51-generic         5.13.0-51.58~20.04.1                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.13.0-52-generic         5.13.0-52.59~20.04.1                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-43-generic         5.15.0-43.46~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-46-generic         5.15.0-46.49~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-52-generic         5.15.0-52.58~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-53-generic         5.15.0-53.59~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-56-generic         5.15.0-56.62~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-70-generic         5.15.0-70.77~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-73-generic         5.15.0-73.80~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-75-generic         5.15.0-75.82~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-82-generic         5.15.0-82.91~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-83-generic         5.15.0-83.92~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-84-generic         5.15.0-84.93~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-86-generic         5.15.0-86.96~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-89-generic         5.15.0-89.99~20.04.1                        amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-92-generic         5.15.0-92.102~20.04.1                       amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-94-generic         5.15.0-94.104~20.04.1                       amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-97-generic         5.15.0-97.107~20.04.1                       amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP

```

---

### Post by TheFu on 2024-06-14
They are already gone, so you can just ignore them.  If you want them removed from the list, you can "purge" them.  Using **synaptic** is probably the easiest way, though you can use **apt purge** too with some wildcard pattern matching.

---

### Post by Bashing-om on 2024-06-14
Skaperen -

My go to for "rc" marked packages:
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
The state is rc, the package is removed, but the config files are not removed
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package.

[INDENT]me likes clean
[/INDENT]

---

### Post by ajgreeny on 2024-06-15
I'm with TheFu on this.
Install synaptic if you don't already have it and in the left hand pane click on the  box that says "Retained configuration" or something similar.
Select them all then go to "packages" menu and choose to remove completely.
That will get rid of everything.

If you want a GUI for package management forget all the other available software-store type applications and try synaptic.
Although I seldom now use it, it is so much more informative about what is happening or will happen, particularly if you set it to show output action in a terminal window which is an option in its preferences.

---

### Post by VMC on 2024-06-15
> **Bashing-om said:**
> Skaperen -

My go to for "rc" marked packages:
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
The state is rc, the package is removed, but the config files are not removed
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package.
[INDENT]me likes clean
[/INDENT]


Thanks Bashing-om, worked great. Didn't even know I had any.

---

### Post by ian-weisser on 2024-06-15
"rc" marked packages are already completely removed.

You are merely seeing the entry *that they once existed* in your package database.

---

### Post by ajgreeny on 2024-06-19
> **ian-weisser said:**
> "rc" marked packages are already completely removed.

You are merely seeing the entry *that they once existed* in your package database.
Not quite.
The ***rc*** means that the package itself has been uninstalled but the configuration files and folders, except for those in your home which are never removed, are still in the filesystem somewhere.

---

### Post by Skaperen on 2024-06-20
can i still purge them?  is that safe?  *i* did *not* do any configuration of any of these.

---

### Post by Doug S on 2024-06-21
> **Skaperen said:**
> can i still purge them?  is that safe?  *i* did *not* do any configuration of any of these.Yes and yes.

I do it all the time.

---

### Post by ajgreeny on 2024-06-22
So do ,I but it can be useful not to do so if you are likely to reinstall that package in the future at some point particularly if you have changed any config details  that are in system files rather than in your home.

---

### Post by Doug S on 2024-06-22
> **ajgreeny said:**
> So do ,I but it can be useful not to do so if you are likely to reinstall that package in the future at some point particularly if you have changed any config details  that are in system files rather than in your home.The example given was all kernels. I am not aware of any user ability to change kernel configuration information post compile. If there is, I would be interested to learn how to do it.

---

### Post by #&amp;thj^% on 2024-06-22
> **Doug S said:**
> Yes and yes.

I do it all the time.

+1 Me as well...I like like it tidy, no free-loaders....LOL

> **Doug S said:**
> The example given was all kernels. I am not aware of any user ability to change kernel configuration information post compile. If there is, I would be interested to learn how to do it.

Sign me up as well.

---

### Post by ajgreeny on 2024-06-23
And I was thinking of other packages than kernels.

---

