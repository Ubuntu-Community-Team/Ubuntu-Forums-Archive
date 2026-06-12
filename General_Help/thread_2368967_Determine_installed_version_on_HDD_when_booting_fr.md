---
title: "Determine installed version on HDD when booting from LiveCD"
date: 2017-08-17
forum: General Help
---

### Post by Xubuntist on 2017-08-17
Hi

I've got my son's Ubuntu laptop that won't boot up because of an impending HD failure. I've cloned the disk so all the data is safe. The clone is now in the laptop but the laptop won't boot up. I ran boot-repair from a LiveCD to try to fix grub but it's not booting up - an error on the original HDD has cloned over to the new one. I'm not going to fight this, I freely admit I'm out of my depth and anyway it's easier to just format the drive and reinstall Ubuntu and restore his apps and data. The thing is, I don't know which flavour of Ubuntu he has. It could be Lubuntu or Xubuntu, I can't remember. If I booth from a LiveCD, how can I determine the version of Ubuntu that is installed on the hard drive?

Many thanks in advance for your help.

---

### Post by dragonfly41 on 2017-08-17
If you can access the dead filesystem using liveCD then you can inspect contents of /etc/lsb-release.

e.g. in my case ...

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"

---

### Post by shridhar-kapshikar on 2017-08-17
[COLOR=#333333][FONT=Ubuntu]This method will tell you which version of Ubuntu or desktop environment you are running.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST=1]
[*=left][FONT=inherit]Open the **Terminal** (keyboard shortcut: Ctrl+Alt+T)[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Enter the command ```
lsb_release -a[FONT=inherit]
```[/FONT][/FONT]
[/LIST]

---

### Post by Xubuntist on 2017-08-17
@[**[COLOR=#000000]shridhar-kapshikar[/COLOR]**]("https://ubuntuforums.org/member.php?u=2062852") This only gives you the release of the LiveCD I'm using, not the OS on the HDD.

---

### Post by Xubuntist on 2017-08-17
@[**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878") I get almost the same as you:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"

But that doesn't tell me what desktop environment is on there.

---

### Post by jeremy31 on 2017-08-17
The DE might be named in the hidden dmrc file in the /home folder

---

### Post by Xubuntist on 2017-08-17
Think I found it. When I go into /usr/bin and do a search for *ubuntu* I see a file openbox-lubuntu, lubuntu-logout and another lubuntu-software-center so I guess it's safe to say it's Lubuntu on that drive.

Many thanks for the help.

---

### Post by Xubuntist on 2017-08-17
> **jeremy31 said:**
> The DE might be named in the hidden dmrc file in the /home folder

Yep - that works too! (and easier than the solution I found)

Thanks!

---

### Post by deadflowr on 2017-08-17
For what it's worth, the DE will be listed in the xsessions folder at /usr/share/xsessions

You can also determine the original flavor that was installed by looking at the file /var/log/installer/media-info

Though moot now, but perhaps something that may be helpful later on.

---

