---
title: "gsettings During Boot"
date: 2013-06-23
forum: General Help
---

### Post by astrolinux22 on 2013-06-23
Hi, I am writing a python program to change the wallpaper background depending on the time of day (Google Now Style) and have got it working nicely. Set it up as a cron job to run every 15 mins.

The only remaining issue is that if I log out at night for example and then restart my pc in the morning the paper is still on night until the cron job gets run.

So what I would like to do is run the same program on boot. I tried the @reboot command in cron but I think it executes too early during boot to make any changes to gsettings. So at what point during boot can I run a gsettings command to change the background? I can't think of where to find this out.

I assume gnome will have had to load for it work but at what point does it load and can I change the paper before/at the lightdm login?

Thanks,

Matt

---

