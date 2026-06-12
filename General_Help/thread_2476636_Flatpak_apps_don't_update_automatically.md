---
title: "Flatpak apps don't update automatically"
date: 2022-07-01
forum: General Help
---

### Post by aplistir on 2022-07-01
How to get flatpak apps to update automatically? (Or when I run "apt upgrade")


I thought Flatpak apps were supposed to update automatically. But on my system (Kubuntu 22.04) they don't!
Today I noticed that I was still running (flatpak) Firefox version 99.0.1

I googled and found a command to update flatpaks. And I ran:
```
flatpak update
```

After that, all my flatpaks were updated and now my firefox is version 102.0

So, anyone know how to get flatpak apps to update automatically?

And I prefer using flatpak instead of snap, because program starting speed is important to me.

---

### Post by #&amp;thj^% on 2022-07-01
Well It's supposed to, It is done automatically by the flatpak updater service that runs 10 minutes after every boot. For me anyway.
have a look here:
```
flatpak update -y > ~/.cache/mintinstall/flatpak-update.log

```
Dose that exist on your system?
If not follow this: [https://www.jwillikers.com/automate-flatpak-updates-with-systemd](https://www.jwillikers.com/automate-flatpak-updates-with-systemd)
```
systemctl status update-system-flatpaks.timer
&#9679; update-system-flatpaks.timer - Update system Flatpaks daily
     Loaded: loaded (/etc/systemd/system/update-system-flatpaks.timer; enabled>
     Active: active (waiting) since Fri 2022-07-01 11:05:21 MDT; 3min 43s ago
      Until: Fri 2022-07-01 11:05:21 MDT; 3min 43s ago
    Trigger: Sat 2022-07-02 00:00:00 MDT; 12h left
   Triggers: &#9679; update-system-flatpaks.service

```

---

### Post by coley9225 on 2022-07-01
Because I don't shutdown or reboot often, if I wanted to be sure the flatpak apps got updated, I would set a cron job to do the updates. If sudo is required, use sudo crontab -e, otherwise use crontab -e. These will either set a root cronjob, or a user cronjob.
Set them to run however often you want, daily(overkill, inho) or weekly, or even monthly. Doing that makes it happen automatically so you don't have to remember to do it. If you shutdown your computer at night then it should do the upgrades on it's own after ypu boot the computer.

---

### Post by vanadium on 2022-07-02
Flatpaks do *not* update automatically. Use the command "flatpak update" to do so.

If your software center has a flatpak plugin, then *that* may cause flatpaks to update automatically.

---

