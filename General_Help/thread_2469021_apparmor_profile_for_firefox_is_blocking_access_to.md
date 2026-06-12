---
title: "apparmor profile for firefox is blocking access to GPU resulting in poor performance"
date: 2021-11-17
forum: General Help
---

### Post by experimenter2 on 2021-11-17
Ubuntu 20.04 LTS: tested with both kernel linux-generic-5.4 and linux-generic-hwe-5.11

Apparmor profile for firefox is blocking access to GPU resulting in poor performance of Firefox


sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
Setting /etc/apparmor.d/usr.bin.firefox to enforce mode.
with apparmor active:


~:$ firefox
[GFX1-]: No GPUs detected via PCI
[GFX1-]: glxtest: process failed (received signal 11)




sudo aa-disable /etc/apparmor.d/usr.bin.firefox
Disabling /etc/apparmor.d/usr.bin.firefox.


Post disabling:


~:$ firefox
runs without a problem and doesn't stutter


What changes can be made to the apparmor profile of firefox to fix this.

---

### Post by MAFoElffen on 2021-11-18
Years ago, intermittently, things like this would happen (rarely) when the User's Firefox profile got corrupted...

What happens if you have it enforced and backup, then remove that profile...
```
cd ~/.mozilla && mkdir backup
cp -r ./extensions ./backup
cp -r ./firefox* ./backup
rm -rf ./firefox* ./extensions

```
On the next start of FireFox it would create a new profile, and see if that was it.

If not, you could delete the new, and restore the backed up directories of...

And if it doesn't I could post mine and you could compare with diff...Though AppArmor files "usually" do not have problems...

---

