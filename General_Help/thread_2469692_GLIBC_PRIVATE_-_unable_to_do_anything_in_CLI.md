---
title: "GLIBC_PRIVATE - unable to do anything in CLI"
date: 2021-12-06
forum: General Help
---

### Post by OiPenguin on 2021-12-06
After attempting to install Citrix I may have done something seriously wrong with my system. In the command line, whatever I do, the output is
```
sudo: symbol lookup error: /usr/local/lib/AppProtection/libAppProtection.so: undefined symbol: _dl_sym, version GLIBC_PRIVATE

```
Hence, I'm unable to update, purge packages or do anything to remedy the problem. At the moment I'm reluctant to do anything at all out of fear of messing up. I'm on v 20.10. Can anyone help?

---

### Post by dragonfly41 on 2021-12-06
This looks similar ..

[https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg5967006.html](https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg5967006.html)

---

### Post by OiPenguin on 2021-12-06
I gave up and did a complete reinstall. I tried to reboot, but the machine didn't even boot.

---

### Post by john-lsrv1 on 2021-12-13
> **OiPenguin said:**
> After attempting to install Citrix I may have done something seriously wrong with my system. In the command line, whatever I do, the output is
```
sudo: symbol lookup error: /usr/local/lib/AppProtection/libAppProtection.so: undefined symbol: _dl_sym, version GLIBC_PRIVATE

```
Hence, I'm unable to update, purge packages or do anything to remedy the problem. At the moment I'm reluctant to do anything at all out of fear of messing up. I'm on v 20.10. Can anyone help?

You can boot from a "Ubuntu Live cd/usb" and remove de files **/usr/local/lib/AppProtection/libAppProtection.so***, and remove or comment line "/usr/local/lib/AppProtection/libAppProtection.so" in the file /etc/ld.so.preload" 
After that reboot and login again.
When you still see errors about /usr/local/lib/AppProtection/libAppProtection.so, just execute ldconfig as root.

---

### Post by _salem_ on 2022-04-28
> **john-lsrv1 said:**
> You can boot from a "Ubuntu Live cd/usb" and remove de files **/usr/local/lib/AppProtection/libAppProtection.so***, and remove or comment line "/usr/local/lib/AppProtection/libAppProtection.so" in the file /etc/ld.so.preload" 
After that reboot and login again.
When you still see errors about /usr/local/lib/AppProtection/libAppProtection.so, just execute ldconfig as root.

Thank you :) Just made the same mistake as the OP today. I was trying to get citrix workspaces to run (it was working fine yesterday, but today just....nothing happened when I tried to launch from the dash) by uninstalling and reinstalling, over and over, and it wasn't fixing it, so one reinstall I tried ticking the "AppProtection" box and it completely stuffed my system.

Then followed a series of dramas with my ubuntu USB having been overwritten with a bunch of MP3s at some point, my laptop running out of battery and not registering the usb when plugged in to create a new bootable usb stick...etc etc.

But, the instructions you gave worked perfectly (even though my main ubuntu install was on an encrypted partition, I was still able to mount it in the live usb as I was prompted for the password).

---

