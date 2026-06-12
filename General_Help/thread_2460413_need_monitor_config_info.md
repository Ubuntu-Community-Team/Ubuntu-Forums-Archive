---
title: "need monitor config info"
date: 2021-04-09
forum: General Help
---

### Post by coley9225 on 2021-04-09
I have a laptop with a 40 tv for an external monitor. Until now, I've been the only user, but I'M setting up a user account for my wife. I use 6 desktops, and both monitors, basically have 12 screens. My wife is an extreme noob at computers. I will even have to teach her how to boot up and login. I would like to do is cut my system down so she doesn't get confused with multiple desktops and screens. I can reduce to 1 desktop without issue. My question is, in monitor settings, there is a spot to enable this monitor.If i'm right, I can unmark the external monitor, and it will be like it's not there, but I want to disable the laptop monitor so she is only working with 1 desktop and only the external  monitor. If I do this, is it going to cause any issues, such as being disabled on my login. Any advise would be great, Thanks.

---

### Post by TheFu on 2021-04-09
I would control this in the ~/.xinitrc file in her HOME with an **xrandr** command.  For playing with settings, I'd use lxrandr.

---

### Post by HermanAB on 2021-04-09
Rather set the external monitor to clone the laptop screen, then plug in a keyboard also and set the laptop power settings so that it will NOT sleep when the lid is closed.

---

### Post by guiverc on 2021-04-09
You've not provided enough details for me to provide much specifics.

Modern Lubuntu using LXQt?
Legacy Lubuntu using LXDE (*which don't forget reaches EOL later this month*)

Assuming it's a modern Lubuntu, monitor settings by GUI are found at 

- [https://manual.lubuntu.me/stable/3/3.2/3.2.10/monitor_settings.html](https://manual.lubuntu.me/stable/3/3.2/3.2.10/monitor_settings.html)

Openbox settings for some of what you want are found at 

[https://manual.lubuntu.me/stable/3/3.2/3.2.11/openbox_settings.html](https://manual.lubuntu.me/stable/3/3.2/3.2.11/openbox_settings.html)

Please note: As you didn't provide release details, I've just grabbed the *stable* release, which is also the *latest* or matches Lubuntu 20.10 the latest stable release.  If you're using an older LTS release (eg. 20.04) you can switch out the word *stable* and use *lts* for it's manual page.

These settings are per-user, they don't impact `sddm` (ie. the greeter or anything before you've logged in) but are read on login, so can be very different for each user (and won't impact other users).

---

### Post by coley9225 on 2021-04-10
Many thanks for the tips. I will look into the commands you offered. Herman, I didn't see a 'clone' setting, but the show only monitor 2 seems to be that setting, and that is an idea I hadn't though of. guivec, thanks for the links, they have a lot of useful tips. I'm using lubuntu 20.04 with the lxqt de. You informed me that the settings can be wildly different for each user, which is what I thought but wanted to verify. I went ahead and disabled my laptop monitor and it is working as I had hoped, at least for now. Again, many thanks for the info you guys gave me. I will mark this one as solved.

---

