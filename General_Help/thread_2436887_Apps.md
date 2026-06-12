---
title: "Apps"
date: 2020-02-14
forum: General Help
---

### Post by mraamohamed on 2020-02-14
OK guys I am still learning so please forgive for stupid questions.

OpenShot-v2.5.0-x86_64.AppImage I have this file I download but can not install, what I can do with it how do I install?

I have tried to install apps from the Ubuntu App store but they are not the updated apps, I have found.

Thanks

---

### Post by Skaperen on 2020-02-14
we are all still learning.  the first day we don't learn something new is the day we died.

what version of Ubuntu are you running?  where did you download this file from?  what is its complete name?  how did you discover that the apps in the store are not updated?

---

### Post by deadflowr on 2020-02-14
Appimage aren't installable, per se.
They are click and run programs.
You need to mark them as executable and then just click, or double click to run.

---

### Post by mraamohamed on 2020-02-14
I am running ubuntu 18.4 the file came from the OpenShot web page, and the apps on store just scroll and look at the version info and you see that they are different.

---

### Post by Skaperen on 2020-02-14
i want to understand more about this file.  is there a dot in the file name?  if so, what is after the dot in the file name?

can you open a terminal shell session where you can type in commands?  there is a command that can tell me more about this file.

---

### Post by CatKiller on 2020-02-14
> **mraamohamed said:**
> I have tried to install apps from the Ubuntu App store but they are not the updated apps, I have found.

A higher version number doesn't mean that it's better, and it doesn't even mean that it's newer. 

A couple of months before each Ubuntu release (which are versioned by date) the packages that will be included are fixed - known as feature freeze. There will then be testing and bug fixes done on all of those packages until the Ubuntu release. 

After release, all security fixes and bug fixes will be applied to each of those packages. The version numbers won't change, but they're still being updated. New features won't be added except in special circumstances: new versions of the kernel and graphics come through the Hardware Enablement Stack, new versions of web browsers - which update frequently and mix security updates with feature updates - will be made available, and particularly desirable new features may go through the Stable Release Update process. 

This isn't Windows where you might need to download the least-tested version from some random website to not be vulnerable to exploits. 

If you desperately *need* some feature from some application that wasn't available when that application's package went into feature freeze you can add a PPA to have another source for your package manager to collect software from and keep it updated along with everything else. There are also containerised distribution methods, like snaps, flatpaks, or appimages, which bundle everything into one file, but might not be updated automatically, or might have other restrictions compared to installing through the package manager.

---

### Post by vanadium on 2020-02-15
Right-click the .appimage file in your file manager, then choose "Properties". On the "Permissions" tab, check the box "Allow executing file as a program". Now double-click the .appimage file and the program OpenShot will be started.

---

