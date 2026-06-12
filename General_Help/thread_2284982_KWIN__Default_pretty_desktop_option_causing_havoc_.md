---
title: "KWIN / Default pretty desktop option causing havoc ... well, not too much havoc"
date: 2015-07-02
forum: General Help
---

### Post by subcook on 2015-07-02
So I recently installed Kubuntu 14.04 LTS on my toshiba Satellite Laptop (L855-S5383) (i7 processor, 8GB Ram, can't seem to find the vid card specs anywhere though)

I am under the impression that kubuntu 14.04 comes with Kwin for fancy desktop teeks, appearances, and especially the desktop cube (rather than having to install kwin or compiz).

I can find all the menus, etc but have run into problems with getting the settings to actually stay......good thing I backup.

The first time I tried this, it said something like I had 25 errors and when I clicked onto "details" it said that it was to technical to define the errors.  I had to reinstall Kubuntu anyway (...for other reasons...) and the next time I tried about 1/2 of the settings took (still no cube though).  to be safe I restored the backup to make sure I was  starting with the original settings from scratch, and this time it continuously locked my computer up, did a deja dup restore yet again.

Am I doing something wrong or missing something very elementary ?

Am I better off just going to Compiz ?

If I can manage to get this working, how do I activate the cube to switch desktops? ....

The only thing that I can think of is that my video card is a little too weak for this, but I strongly doubt it (my max resolution is 1366x788 ish.  I apologize for not providing the vid card spec but cannot find it anywhere.

Never had these issues w/ Compiz, but am under the impression that it's on it's way out, unfortunatly, so trying to get a feel for KWIN.

I know this is cosmetic, but it's driving me nuts.

Thanks in advance,

Cheers!

---

### Post by him610 on 2015-07-02
subcook, 

> can't seem to find the vid card specs anywhere though

[http://www.cnet.com/products/toshiba-satellite-l855-s5383-15-6-core-i7-3630qm-windows-8-8-gb-ram-640-gb-hdd-series/specs/]("http://www.cnet.com/products/toshiba-satellite-l855-s5383-15-6-core-i7-3630qm-windows-8-8-gb-ram-640-gb-hdd-series/specs/")

It appears that you have an Intel HD Graphics 4000 graphics processor.

---

### Post by grahammechanical on 2015-07-02
This will explain a little about Kwin

[https://userbase.kde.org/KWin](https://userbase.kde.org/KWin)

All window managers/compositors that run on the X server are on the way out. But not for a few years. X server is being replaced either by compositors built to the Wayland specification or by Mir, the Ubuntu built replacement of X server.

I cannot see Ubuntu or any of the other members of the Ubuntu family changing compositors during the life time of a version. It will be the new releases that come out with a new window compositor. I cannot see developers releasing a new version of the distribution that runs on a new compositor without it being fully tested first.

Regards.

---

### Post by subcook on 2015-07-02
Thanks for that !  ...with that said, is it my vid card that is giving me the issues w/ Windows appearance settings and/or errors ?

---

