---
title: "URGENT: Ubuntu won't start"
date: 2020-02-18
forum: General Help
---

### Post by davy jones on 2020-02-18
I use Ubuntu 14.04 and this morning, it just wouldn't start up. I see this message and then the startup screen comes on but it never takes me to the login stage. [ATTACH=CONFIG]285043[/ATTACH][ATTACH=CONFIG]285043[/ATTACH]

I have a dual boot system with Windows 8 and I'm using a Dell Inspiron with a Radeon graphics card + inbuilt Intel graphics card.

---

### Post by guiverc on 2020-02-18
You do realize Ubuntu 14.04 LTS reached EOL last year ([http://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/](http://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/))

If you're using Ubuntu 14.04 ESM, it is supported by Canonical through Ubuntu Advantage.

In your case, I'd boot a 'live' media (such as Ubuntu install thumb-drives) and check out your hardware (SMART etc), `fsck` (file system check) your disks and explore for issues...  I'd also then just backup your data & either upgrade to a supported release of Ubuntu (ie. 16.04 LTS) or re-install a modern release.

You didn't say if you were running desktop, server - as server install media that old usually used '*debian-installer*' thus didn't have a 'live' mode (modern media does where using `subiquity`) so I'd just use a 'desktop installer if your handy media is old & debian-installer based.

---

