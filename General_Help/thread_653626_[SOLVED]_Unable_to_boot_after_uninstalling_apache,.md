---
title: "[SOLVED] Unable to boot after uninstalling apache, MySQL and mono"
date: 2007-12-30
forum: General Help
---

### Post by mardawi on 2007-12-30
Hi,

After uninstalling apache, MySQL and mono using synaptic, I've restarted the PC and ubuntu 7.10 no longer boots. I don't see any error messages, after loading is complete, it just displays a blank screen with the beam on the upper right corner. I was able to boot and start X using the recovery option from grub.

Any ideas what the problem might be? how to fix it?

Thanks in advance!

---

### Post by tgilber1 on 2007-12-30
> **mardawi said:**
> Hi,

After uninstalling apache, MySQL and mono using synaptic, I've restarted the PC and ubuntu 7.10 no longer boots. I don't see any error messages, after loading is complete, it just displays a blank screen with the beam on the upper right corner. I was able to boot and start X using the recovery option from grub.

Any ideas what the problem might be? how to fix it?

Thanks in advance!

You could try the following.  Also, check out your logfiles /var/log/* for errors

[LIST=1]
[*]From the GRUB menu, use the recovery mode.  Recovery should dump you to a root prompt.  Hence, you do not have to use sudo
[*]"dpkg -l gnome-session" to see if you accidently uninstalled it
[*]Whether it is installed or not, try apt-get install --reinstall gnome-session
[*]Check for broken dependencies, "apt-get check"
[/LIST]

---

### Post by mardawi on 2007-12-30
I've tried that already, everything seemed fine. Thanks for the reply anyway.

I'm ganna do a fresh installation now :(
I can't wait longer plus there isn't much on the old broken installation to worry about.

---

