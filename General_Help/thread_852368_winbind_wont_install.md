---
title: "winbind wont install"
date: 2008-07-07
forum: General Help
---

### Post by BuckleyInDaHouse on 2008-07-07
```
winbind:
  Depends: samba-common (=3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.4 is to be installed
```

Whenever I try to install Wine through Synaptic packager or through the website I get an error about Winbind not being able to be installed. What is causing this?

Thanks, 
 Buckley.

---

### Post by mempman on 2008-07-07
wine depends on winbind, which depends on samba.

have you tried to install samba-common, if not, try:

```

sudo apt-get install samba-common && sudo apt-get install wine

```

---

### Post by BuckleyInDaHouse on 2008-07-07
> **mempman said:**
> wine depends on winbind, which depends on samba.

have you tried to install samba-common, if not, try:

```

sudo apt-get install samba-common && sudo apt-get install wine

```

Well, this is what I get when I run that in terminal.

```
joshua@joshua-desktop:~$ sudo apt-get install samba-common && sudo apt-get install wine
[sudo] password for joshua: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
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
  wine: Depends: winbind but it is not going to be installed
E: Broken packages

```

---

### Post by BuckleyInDaHouse on 2008-07-08
-Bump-

Does anyone know, I need Wine to install so I can run some nice Windows programs.

Sorry to double post.

 Thanks,
  Buckley.

---

### Post by cyprusxr3 on 2008-08-11
This may be too little to late, but I'll post my solution for the googler's out there.

Try enabling the hardy-proposed repository.

I had the same problem (couldn't install winbind due to variance in samba-common versions). I suspect the difference in version was because I had to install the new broadcom driver from the proposed repository. Not quite sure how samba got screwed up in that, but as I had disabled it afterward, I had a newer version of samba than was available under hardy-release, causing my problems. Hope this helps.

---

