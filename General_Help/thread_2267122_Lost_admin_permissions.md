---
title: "Lost admin permissions"
date: 2015-02-27
forum: General Help
---

### Post by piglovesme44 on 2015-02-27
Help!!!!! I upgraded my Ubuntu from 14.04LTS to 14.10 the when I log into my admin account I see that I lost all my permissions.
I can still use the sudo command in terminal, but that's the only admin thing I can do.

---

### Post by deadflowr on 2015-02-27
What other permissions are you missing? Since you seem to still belong to the sudo group and therefore the admin group...

---

### Post by piglovesme44 on 2015-02-27
I can't do anything admin-related. I can't install apps from the software centre, I can't connect to my Wi-Fi, which forces me to use my Windows PC to write this message. I can't access admin privileges on some software.

---

### Post by piglovesme44 on 2015-02-27
> **deadflowr said:**
> What other permissions are you missing? Since you seem to still belong to the sudo group and therefore the admin group...
[COLOR=#000000]I can't do anything admin-related. I can't install apps from the software centre, I can't connect to my Wi-Fi, which forces me to use my Windows PC to write this message. I can't access admin privileges on some software.[/COLOR]

---

### Post by steeldriver on 2015-02-27
possibly an issue with polkit? what does

```

ps -ef | grep [p]olkit

```
say?

Also see [https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336)

---

### Post by piglovesme44 on 2015-02-27
> **steeldriver said:**
> possibly an issue with polkit? what does

```

ps -ef | grep [p]olkit

```
say?

Also see [https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336)

(green color/colour)root             753     1   0   16:57 ?              00:00:01 /usr/lib/policylit-1/(red color/colour)polkit(green color/colour)d --no-debug

---

### Post by piglovesme44 on 2015-02-27
uggh im just confused i might just reinstall ubuntu it will hopefully fix everything and revert back to 14.04LTS

---

