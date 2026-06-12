---
title: "Black screen after Kubuntu Logo"
date: 2013-12-11
forum: General Help
---

### Post by Asheboy on 2013-12-11
Hi

I have only had this laptop for about 2 weeks so the installation is not very old. It is running Kubuntu 13.10 and has had an intermittent problem where when resuming from hibernation (not sleep) it would display a black screen after the Kubuntu logo. I was not able to access any ttys but after a hard reset (holding down of the power button) it would boot up normally.

Today I have restarted my laptop and now I receive this black screen again and resetting does not solve it. I have run the boot-repair program mentioned here [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") but to no avail.

My laptop is a Lenovo ThinkPad T440s (it does have a NVIDIA GeForce GT 750M).

Any help would be much appreciated.

Ash


EDIT: I edited my grub config and removed the quiet and splash options. I was then able to look at the X.org logs and see that it was failing to load some settings I had changed. All fixed!

---

### Post by cpbl on 2013-12-12
Asheboy
-- Can you give an account of how the T440s has worked overall with 13.10? HAve you had to do much fiddling? Would you be willing to list what does and doesn't work, and which things you've been able to fully solve if there are tweaks necessary??

Thanks!!

---

