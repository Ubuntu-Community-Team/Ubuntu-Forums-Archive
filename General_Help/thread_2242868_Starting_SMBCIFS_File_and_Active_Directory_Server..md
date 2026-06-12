---
title: "Starting SMB/CIFS File and Active Directory Server. [FAIL]"
date: 2014-09-04
forum: General Help
---

### Post by joejvj on 2014-09-04
I recently upgraded my ubuntu server from 12.04 to 14.04 LTS and get the following error message during startup:

[FONT=Courier New]Starting SMB/CIFS File and Active Directory Server. [FAIL][/FONT]

Note: Samba works 100% and I have no issues. I would however like to clean this up.

Anyone know what could be causing this and how to fix it?

---

### Post by 101010CBEnt on 2014-09-30
I, too, have this exact same issue, and would just like to correct the offending code.

---

### Post by Glenn_Thomas_Hvids on 2014-10-23
I recently installed 14.04 and encountered the same issue.
Seeing as I didn't want to use my server as an Active Directory server I set out to find out what was trying to start this service and how to disable it.

I learned that Ubuntu now also use a service initializer called "Upstart", which starts the services listed in [FONT=courier new]/etc/init[/FONT]

So I just deleted the startup script called [FONT=courier new]samba-ad-dc.conf[/FONT]

After a restart I no longer got the *"Starting SMB/CIFS File and Active Directory Server. [FAIL]"* message, and Samba still works for shares.

---

### Post by alexandr-o on 2015-05-28
source:[URL="http://askubuntu.com/questions/455418/samba-started-twice-on-boot-up-after-upgrade-to-14-04"]
http://askubuntu.com/questions/455418/samba-started-twice-on-boot-up-after-upgrade-to-14-04[/URL]

[COLOR=#111111][FONT=Ubuntu] In a root shell do:
[/FONT][/COLOR]echo manual > /etc/init/samba-ad-dc.override

---

### Post by Scott_Combrink on 2016-01-02
> **Glenn_Thomas_Hvids said:**
> I recently installed 14.04 and encountered the same issue.
Seeing as I didn't want to use my server as an Active Directory server I set out to find out what was trying to start this service and how to disable it.

I learned that Ubuntu now also use a service initializer called "Upstart", which starts the services listed in [FONT=courier new]/etc/init[/FONT]

So I just deleted the startup script called [FONT=courier new]samba-ad-dc.conf[/FONT]

After a restart I no longer got the *"Starting SMB/CIFS File and Active Directory Server. [FAIL]"* message, and Samba still works for shares.

I am new to ubuntu how did you delete and please feel free to explain as if I know nothing

---

### Post by uduvgp on 2016-02-01
> **Scott_Combrink said:**
> I am new to ubuntu how did you delete and please feel free to explain as if I know nothing
```
sudo rm /etc/init/samba-ad-dc.conf 

```
But better
```
echo manual |sudo tee /etc/init/samba-ad-dc.override
```

---

