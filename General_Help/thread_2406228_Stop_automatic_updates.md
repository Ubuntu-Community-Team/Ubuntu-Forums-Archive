---
title: "Stop automatic updates?"
date: 2018-11-17
forum: General Help
---

### Post by Abe_Hanson on 2018-11-17
Hello, I am using ubuntu 18.04 Studio, how can I stop the automatic updates?
I have a very limited internet connection of 6 GB per month, if I go over, each additional GB costs me an additional $50.
I prefer to defer the updates until I can get to the public library and use the bandwidth there.
All help appreciated.:D

---

### Post by andre802 on 2018-11-18
Follow the instruction below to disable automatic updates on Ubuntu:


>>Open the Unity Dash
>>Search for "Software & Updates"
>>Select the "Updates" tab
>>Change "Automatically check for updates" from "Daily" to "Never"

---

### Post by Skaperen on 2018-11-18
i wonder how many users have no idea what "Unity Dash" means.

---

### Post by Impavidus on 2018-11-18
Just checking for updates only takes a megabyte at a time or even less. What you want to disable is automatic downloading of security upgrades and unattended upgrades. A few kernel upgrades and some big applications like Firefox can amount to several hundred MB, although it's unlikely you'll get more than a GB per month (unless you have several computers downloading the same updates; in that case try to fix it with some sort of local caching arrangement). So maybe you only want to defer the big updates until you get to the library. When you don't use unattended upgrades or automatic downloading of security upgrades, the update manager or whatever tool you use for upgrading will tell you the size of the download before it begins. You can even decide to download and install the small ones, deferring the big ones, as far as dependencies allow.

So go to your settings for Software & Updates, open the Updates tab and make sure the setting for security updates is not "Download automatically" or "Download and install automatically", but "Show immediately" (or something like that, exact words depend on locale). Also uninstall unattended upgrades:```
sudo apt remove unattended-upgrades
```

---

### Post by Abe_Hanson on 2018-11-18
Thank you, this is very helpful.

---

### Post by Abe_Hanson on 2018-11-18
> **Skaperen said:**
> i wonder how many users have no idea what "Unity Dash" means.

I do know what unity dash is, fortunately ubuntu studio does not have the unity DE.

---

### Post by Abe_Hanson on 2018-11-18
):PThank you andre802, ubuntu studio doesn't use the unity DE, but your advice is helpful nonetheless.

---

