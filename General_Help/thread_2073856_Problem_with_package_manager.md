---
title: "Problem with package manager"
date: 2012-10-20
forum: General Help
---

### Post by jonburton on 2012-10-20
Hi Everyone,

Linux Newbie here after some help please, just upgraded from 12.04 to 12.10 and now have a no entry sign in the top right corner telling me there is a problem with package manager. I have tried to do as it suggests but I am not root

Ive attached a screen shot if anyone could help

Thanks

---

### Post by oldos2er on 2012-10-20
Try ```
sudo apt-get install -f
```

---

### Post by jonburton on 2012-10-20
worked a treat, thanks very much
May I ask what that command means / does for future knowledge?

---

### Post by raja.genupula on 2012-10-20
> **-f**, **--fix-broken** Fix. Attempt to correct a system with broken dependencies in  place. This option, when used with install/remove, can omit any packages  to permit APT to deduce a likely solution. Any **package**(s) that are specified must  completely correct the problem. This option is sometimes necessary when  running APT for the first time; APT itself does not allow broken package dependencies to  exist on a system. It is possible that a system's dependency structure  can be so corrupt as to require manual intervention. Use of this option together with **-m** may produce an error in some situations. Configuration Item: *APT::Get::Fix-Broken*. 

please mark your thread as solved from thread tools

---

### Post by oldos2er on 2012-10-20
*sudo* is a way of elevating your user's privileges to root privileges, as the message "Unable to lock the administration directory (var/lib/dpkg), are you root?" is telling you. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Use the *man* command to get help apt-get: ```
man apt-get
```

---

