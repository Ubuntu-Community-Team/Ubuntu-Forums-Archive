---
title: "Nothing gets saved in my keyring"
date: 2006-10-28
forum: General Help
---

### Post by tenjin on 2006-10-28
Hi,

I have Edgy installed from RC and fully updated.

Whenever I connect to SMB shares on my LAN I get asked to type in the Workgroup name and password. The dialog asks me if I want to save the information in my keyring.

I always tick the box to save it. However, the information never seems to get saved.

I don't know if it is an issue, but I connect to my LAN via a wireless NIC.

Any help you can offer would be appreciated.

Cheers

D.

---

### Post by vibestriton on 2006-10-28
I suspect your wireless router is setup to dynamically assign IPs.  If so, try assigning specific mac addresses to specific IPs.  If your router doesn't offer this option, you can setup your systems to make static IP requests rather than doing the DHCP thing.

---

### Post by tenjin on 2006-10-28
Hi,

Thanks for the posting.

I already have assigned IPs rather than by DHCP.

I now find this error when running /usr/bin/gnome-keyring-manager:

"Gnome Keyring daemon is not running"

- but it is running, and I have restarted it several times.

Any ideas?

Cheers

D.

---

### Post by vibestriton on 2006-10-28
gnome-keyring-daemon is running... and running as user rather than root?

have you tried sudo apt-get install --reinstall gnome-keyring-daemon gnome-keyring-manager?  (then restart)

---

### Post by tenjin on 2006-10-28
Hi,

Thanks for the posting.

That fixed the error, thanks, but I'm still not getting any keys displayed in the Keyring Manager other than "session", and that doesn't have anything defined inside it.

Any ideas?

Cheers

D.

---

### Post by wpwood3 on 2006-11-01
I'm having the same problem.:( 

With Dapper the keyring worked fine with Samba.
I did a clean install of Edgy and the keyring will not work. None of my passwords for Samba shares are being saved in the keyring.

There appears to be a [BUG REPORT HERE]("https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/67189") but no action has been taken as of today to fix the issue.

---

### Post by punkass on 2006-11-02
I am having the same problem as well.

---

### Post by wpwood3 on 2006-11-02
There's a bug report on this one and it has been assigned to the Ubuntu Desktop Bugs team.
It is [BUG# 67189]("https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/67189")
Unfortunately it doesn't look like anything is being done. It has a status of "Needs Info". I don't know what else they need beyond what is already in the bug report.

---

