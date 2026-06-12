---
title: "Repeated system restarts required"
date: 2016-09-02
forum: General Help
---

### Post by philled on 2016-09-02
Every few days I SSH into my Ubuntu 16.04 server and am greeted with a message telling me *** System restart required ***. It doesn't seem to matter whether or not I've recently done sudo apt-get update/upgrade.  

I've also noticed that it also says "7 packages can be updated" every time I SSH in. It still says this after doing sudo apt-get update/upgrade. Surely if I do sudo apt-get upgrade it should update those 7 packages? I'm not sure if this is may be related in some way to the system restart prompting. 

Can anyone advise why it's telling me to do a system restart so often? I never had this problem on earlier Ubuntu versions. Is it a feature of xenial? I've had Windows PCs that needed less restarts than this.

---

### Post by QIII on 2016-09-02
Just doing the upgrade or dist-upgrade may not be enough.  Some updates require a restart -- for instance those that would update or upgrade the kernel.  If the system is not restarted, some updates cannot complete and they still appear to be in need of updates.  Thus, you may get those messages in perpetuity.

---

### Post by philled on 2016-09-02
> **QIII said:**
> Just doing the upgrade or dist-upgrade may not be enough.  Some updates require a restart -- for instance those that would update or upgrade the kernel.  If the system is not restarted, you may get those messages in perpetuity.

I'll double check, but I believe I am doing restarts after some upgrades, not running any more upgrades and it's still asking me to restart. I wonder if perhaps I've got some sort of auto package upgrading happening? This is a non-gui, headless server - what could I check to see if that's turned on or off?

---

### Post by philled on 2016-09-03
> **philled said:**
> I wonder if perhaps I've got some sort of auto package upgrading happening? This is a non-gui, headless server - what could I check to see if that's turned on or off?

I've looked into this, and I do indeed have unattended upgrades occurring for security packages. 
In file /etc/apt/apt.conf.d/50unattended-upgrades:
```
[FONT=courier new]// Automatically upgrade packages from these (origin:archive) pairs[/FONT]
[FONT=courier new]Unattended-Upgrade::Allowed-Origins {[/FONT]
[COLOR=#ff0000][FONT=courier new]        "${distro_id}:${distro_codename}-security";[/FONT][/COLOR]
[FONT=courier new]//      "${distro_id}:${distro_codename}-updates";[/FONT]
[FONT=courier new]//      "${distro_id}:${distro_codename}-proposed";[/FONT]
[FONT=courier new]//      "${distro_id}:${distro_codename}-backports";[/FONT]
[FONT=courier new]};
[/FONT]
```
I don't want any unattended upgrades occurring so I edited /etc/apt/apt.conf.d/20auto-upgrades:
```
[FONT=courier new]APT::Periodic::Update-Package-Lists "1";
// Automatic installation of upgraded packages turned off 
APT::Periodic::Unattended-Upgrade "[COLOR=#ff0000]0[/COLOR]";[/FONT]
```


Lots of good info on there at [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates) and [http://ask.xmodulo.com/disable-automatic-updates-ubuntu.html](http://ask.xmodulo.com/disable-automatic-updates-ubuntu.html)

---

