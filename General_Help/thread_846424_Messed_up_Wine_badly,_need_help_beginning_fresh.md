---
title: "Messed up Wine badly, need help beginning fresh"
date: 2008-07-01
forum: General Help
---

### Post by tsphere on 2008-07-01
Hi,
I played with wineloc and winetricks and winecfg and now it is all messed up (can't run anything, lots of errors etc.)
I want to remove everything to do with wine from my installation and begin fresh and I can't seem to be able to do it.

When I remove wine, even complete remove (in synaptic), firstly it doesn't remove the installed applications, and second when I reinstall wine all my settings are the way I left them, and I get all the errors.

I need a brute force way to remove everything and anything to do with wine, and begin completely fresh with no wine and wine settings or installed apps (ie4linux, ms office etc...).

thanks,

Eyal

---

### Post by STVA on 2008-07-01
type:

cd ~
rm -rf .wine


You'll be as good as new.

---

### Post by brian_p on 2008-07-01
> **tsphere said:**
> 

I need a brute force way to remove everything and anything to do with wine, and begin completely fresh with no wine and wine settings or installed apps (ie4linux, ms office etc...).

In a terminal:

```
sudo apt-get remove --purge wine libwine

```

Then delete $HOME/.wine

---

### Post by g2g591 on 2008-07-01
I'm pretty sure the uninstalling wine totally (the apt-get stuff) is totally unnecessary. the only things that wine tricks and anything else you did (unless you had to use sudo for it) could mess up is your ~/.wine. just rm -R ~/.wine and then next  time you run wine it will recreate the default.

---

### Post by tsphere on 2008-07-04
Thanks to all of you for your help.
My laptop fan has burnt, and when it fixed I will sequentially check the solutions.

Thanks again,
Eyal

---

