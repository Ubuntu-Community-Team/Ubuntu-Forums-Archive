---
title: "So before I do the HWE ugrade..."
date: 2017-07-29
forum: General Help
---

### Post by DigiAngel on 2017-07-29
So this has always bugged me, and since I just redid my laptop I was going to find out the source of the issue.  Situation:  Installed and dist-upgraded 16.04, running kernel is 4.4.  I follow this:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

As of right now, that will install a 4.10 kernel.  Nice.  However, two things to notice....when the 4.4 kernel gets updated, dist-upgrade will continue to upgrade the 4.4 kernel, even though it's not in use:

```
[06:12:09 box:~$] apt-cache policy linux-image-generic
linux-image-generic:
  Installed: (none)
  Candidate: 4.4.0.87.93
  Version table:
     4.4.0.87.93 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     4.4.0.21.22 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

How can I tell my system to stop updating old kernel version?  Thank you.

---

### Post by mc4man on 2017-07-29
Either stop using dist-upgrade (generally not needed) or remove all of the 4.4.0.x packages

---

### Post by Bucky Ball on 2017-07-29
If you did something like this:

```
sudo apt update
sudo apt full-upgrade
sudo apt autoremove
```

... it should install the HWE upgrade and the last command should get rid of any unecessary kernels (4.4). You are usually left with the current kernel and the last one (in case the newest is broken or breaks).

Be aware that the 'sudo apt full-upgrade' command will NOT upgrade your 16.04 to a newer release. Just upgrades the software you already have installed in 16.04, including kernel. Also, in case you are unaware, you should always do the 'sudo apt update' command before any upgrade commands. ;)

---

### Post by Perfect Storm on 2017-07-29
Thread moved.

---

### Post by Keith_Helms on 2017-07-30
> **DigiAngel said:**
> So this has always bugged me, and since I just redid my laptop I was going to find out the source of the issue.  Situation:  Installed and dist-upgraded 16.04, running kernel is 4.4.  I follow this:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

As of right now, that will install a 4.10 kernel.  Nice.  However, two things to notice....when the 4.4 kernel gets updated, dist-upgrade will continue to upgrade the 4.4 kernel, even though it's not in use:

```
[06:12:09 box:~$] apt-cache policy linux-image-generic
linux-image-generic:
  Installed: (none)
  Candidate: 4.4.0.87.93
  Version table:
     4.4.0.87.93 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     4.4.0.21.22 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

How can I tell my system to stop updating old kernel version?  Thank you.

If I recall, when I installed the hwe packages, I removed the non hwe kernel versions with
```
sudo apt-get purge linux-generic linux-image-generic linux-headers-generic
```

---

### Post by speartip on 2017-07-31
Simple answer. Install Synaptic, & search for all 4.4.0 packages. Remove anything that you still have installed, & no more updates.

---

