---
title: "systemd overrides xfce4-power-manager"
date: 2014-07-25
forum: General Help
---

### Post by David_Abergel on 2014-07-25
Hi all,

I'm using xubuntu 14.04 LTS.

A couple of days ago, after the system updater installed some updates, I noticed that my laptop had changed its behavior when the lid was shut. Previously, I used xfce4-power-manager so that when the laptop was on AC, shutting the lid did nothing, but when it was on battery power, shutting the lid caused the laptop to suspend. Everything was working fine.

After the update, I found that shutting the lid would cause the laptop to suspend regardless of the power source.

I did some reading, and found that the settings in /etc/systemd/logind.conf also affect these events. After playing around with the various combinations, I find that the settings in /etc/systemd/logind.conf always take precedence over the xfce4-power-manager settings. However, other settings from xfce4-power-manager (such as what happens when I press the power button, or screen brightness) work as expected.

Anyone have any clue what is going on? I'm stumped.

Thanks!

---

### Post by Toz on 2014-07-25
Most probably, a recent version update of systemd added further functionality (control) that overrode xfce4-power-manager functionality.

Ubuntu's implementation of systemd and xfce4-power-manager's support for systemd are in flux. Currently, the xfce4-power-manager version shipped with Xubuntu 14.04 doesn't support (work with) systemd well. That has been fixed in the [xfce4-power-manager git tree]("http://git.xfce.org/xfce/xfce4-power-manager/") and we are just waiting for it to be picked up by Xubuntu. Not exactly sure when that will happen.

The Xfce team is looking at releasing 4.12 sometime later this year, so maybe around then.

---

### Post by David_Abergel on 2014-07-25
Hi Toz, and thanks for getting back to me.

I guess I shall just have to be patient and wait for xubuntu to catch up. I'll keep reading in the meantime though, and post back anything that is useful.

---

