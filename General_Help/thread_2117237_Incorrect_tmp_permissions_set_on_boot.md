---
title: "Incorrect /tmp permissions set on boot"
date: 2013-02-17
forum: General Help
---

### Post by MeMo_oMeM on 2013-02-17
Hi Everyone,

I have a weird issue going on with the tmp folder. 

Everytime I reboot the machine, its permissions change into 755 and the owner becomes memo:root. 'memo' is my user account.

I checked init.d and profile.d to see if any of the init scripts are causing this. Some of those do check for permissions but I could not find any script that attempts to change them. I change it back to root:root and 01777 (also 1777), but it always changes back to incorrect settings after I reboot.

This is very annoying since it causes some services to crash with permission denied errors. 

I would appreciate any suggestions!

Thanks :)

---

### Post by rnerwein on 2013-02-18
> **MeMo_oMeM said:**
> Hi Everyone,

I have a weird issue going on with the tmp folder. 

Everytime I reboot the machine, its permissions change into 755 and the owner becomes memo:root. 'memo' is my user account.

I checked init.d and profile.d to see if any of the init scripts are causing this. Some of those do check for permissions but I could not find any script that attempts to change them. I change it back to root:root and 01777 (also 1777), but it always changes back to incorrect settings after I reboot.

This is very annoying since it causes some services to crash with permission denied errors. 

I would appreciate any suggestions!

Thanks :)
hi
check /etc/init and /etc/rc.local too.
what i'll do is:
cd /etc/init --> ls -ltr
cd /etc/init.d --> ls -ltr
too see if there is/are some new start-up script(s).
ciao

---

### Post by spjackson on 2013-02-18
Is /tmp a mount point? If so then it is possible that the permissions of the underlying mount point are incorrect. When you correct the permissions after a reboot, this does not change the underlying mount point.

If this is what's going on, then you would need to correct ownership and permissions when /tmp is not mounted. There are (at least) 2 ways to do this.
[LIST=1]
[*]Boot into single user mode and fix /tmp.
[*]Comment out the /tmp entry from /etc/fstab, reboot, fix, restore /etc/fstab, reboot.
[/LIST]

---

### Post by MeMo_oMeM on 2013-02-22
> **spjackson said:**
> Is /tmp a mount point? If so then it is possible that the permissions of the underlying mount point are incorrect. When you correct the permissions after a reboot, this does not change the underlying mount point.

If this is what's going on, then you would need to correct ownership and permissions when /tmp is not mounted. There are (at least) 2 ways to do this.
[LIST=1]
[*]Boot into single user mode and fix /tmp.
[*]Comment out the /tmp entry from /etc/fstab, reboot, fix, restore /etc/fstab, reboot.
[/LIST]

Actually, tmp used to be a mount point, but currently it is just a directory in '/'. They was no remainder entries in fstab. I tried recreating the directory in single user mount, to no avail. 

Thanks for the suggestions!

---

### Post by MeMo_oMeM on 2013-02-22
> **rnerwein said:**
> hi
check /etc/init and /etc/rc.local too.
what i'll do is:
cd /etc/init --> ls -ltr
cd /etc/init.d --> ls -ltr
too see if there is/are some new start-up script(s).
ciao

Thanks! Yes, this gives me more scripts to look into :)

---

### Post by MeMo_oMeM on 2013-02-23
With help from Canonical, we found that this issue is caused by the couchpotato init script. 

Its PID file should be contained in a directory of its own, e.g., 

/var/run/couchpotato/server.pid

what I had was 

/var/run/couchpotato.pid

Thanks for all replies. :)

---

