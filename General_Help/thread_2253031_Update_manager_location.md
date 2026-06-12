---
title: "Update manager location?"
date: 2014-11-16
forum: General Help
---

### Post by Camilia on 2014-11-16
I want to check the update manager manually. How do I do that? Last time it popped up I had 133 updates to download.

I checked the System settings and files.

---

### Post by Bashing-om on 2014-11-16
Camilia; Hello;

> **Camilia said:**
> I want to check the update manager manually. How do I do that? Last time it popped up I had 133 updates to download.

I checked the System settings and files.

Terminal commands ?
If so, then:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
where 'dist-upgrade' will install new kernels ( regular 'upgrade' will not ) .

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by Dennis N on 2014-11-16
> **Camilia said:**
> I want to check the update manager manually. How do I do that? Last time it popped up I had 133 updates to download.

I checked the System settings and files.

Your information shows Ubuntu 12.04. So, I would use the Dash search, and enter "Update Manager" in the search box. It will show up. Use the "Check" button to get the latest information. "Settings" button at the bottom allows setting how often it checks.

---

### Post by grahammechanical on 2014-11-16
You can also search the Dash for "software updater" or just "software" usually finds it for me. Software Updater will then become one of your recently used applications and its icon should make its appearance soon after opening the Dash.

Regards.

---

### Post by Camilia on 2014-11-16
yes it is in Dash. Thanks!!

---

