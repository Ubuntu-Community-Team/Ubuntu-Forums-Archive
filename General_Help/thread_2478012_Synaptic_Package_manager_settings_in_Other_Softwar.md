---
title: "Synaptic Package manager settings in Other Software tab"
date: 2022-08-14
forum: General Help
---

### Post by skoles on 2022-08-14
I am currently running Ubuntu 20.04.04

I am noting that my Ubuntu software is not getting updated automatically or at least based on a certain software package, WSJTX, its not showing the latest version. I am stuck at 2.1.2 while others have used the Ubuntu Software updater to upgrade to 2.5.4 


 In the Software and Updates there are a slew to tabs for different sources for updates. The only ones checked are in the first Ubuntu Software tab. All the other tabs are not checked boxed.


Are there general settings for configuring updates in Ubuntu Software ?

I suspect I have an issue with getting updated versions but not quite sure what the root cause is...

---

### Post by deadflowr on 2022-08-14
Unless you add some outside source like a 3rd party repository or a PPA, the WSJTX package will remain at the version you have.
It's never been updated in the 20.04 official repositories.

Ubuntu typically freezes packages at the version used at release time.
With a few exceptions most updates will keep the versions of packages at the same as they were at that release.
Most updates will be for security related fixes or small fixes for basic features.
The small fixes for basic features also need to follow Ubuntu's [Stable Release Update protocol]("https://wiki.ubuntu.com/StableReleaseUpdates").

---

### Post by Dennis N on 2022-08-14
> I am noting that my Ubuntu software is not getting updated automatically or at least based on a certain software package, WSJTX, its not showing the latest version.

If you need the latest version of certain software, it may be available as a Flatpak. In this case, it is:

dmn@Tyana-vm:~$ flatpak search wsjtx
```
Name          Description                                 Application ID                      Version         Branch        Remotes
wsjtx         Amateur Radio Weak Signal Operating         edu.princeton.physics.WSJTX         2.5.4           stable        flathub

```

---

### Post by Holger_Gehrke on 2022-08-14
Another possibility is that the people who got a current version of wsjtx on their Ubuntu did an upgrade to a newer version of Ubuntu - specifically to 22.04. If I do 'apt show wsjtx' on my XUbuntu 22.04 it gives the available version as '2.5.4+repack-1'.

Holger

---

### Post by skoles on 2022-08-14
> **deadflowr said:**
> Unless you add some outside source like a 3rd party repository or a PPA, the WSJTX package will remain at the version you have.
It's never been updated in the 20.04 official repositories.

Ubuntu typically freezes packages at the version used at release time.
With a few exceptions most updates will keep the versions of packages at the same as they were at that release.
Most updates will be for security related fixes or small fixes for basic features.
The small fixes for basic features also need to follow Ubuntu's [Stable Release Update protocol]("https://wiki.ubuntu.com/StableReleaseUpdates").

Understood. I am tracking down the repository/PPA link I need for this to be updated automatically. Thank you

---

### Post by skoles on 2022-08-14
> **Dennis N said:**
> If you need the latest version of certain software, it may be available as a Flatpak. In this case, it is:

dmn@Tyana-vm:~$ flatpak search wsjtx
```
Name          Description                                 Application ID                      Version         Branch        Remotes
wsjtx         Amateur Radio Weak Signal Operating         edu.princeton.physics.WSJTX         2.5.4           stable        flathub

```

Flatpak is a new one to me. Just did some reading on this. Sounds like what I am after as it is all bundled in the app upgrade. Nice. Thanks

---

### Post by skoles on 2022-08-14
> **Holger_Gehrke said:**
> Another possibility is that the people who got a current version of wsjtx on their Ubuntu did an upgrade to a newer version of Ubuntu - specifically to 22.04. If I do 'apt show wsjtx' on my XUbuntu 22.04 it gives the available version as '2.5.4+repack-1'.

Holger

The other Ubuntu user was running the same release as me, 20.04. 

I understand the app releases are bundled with the OS release now.

Thanks for the reply

---

