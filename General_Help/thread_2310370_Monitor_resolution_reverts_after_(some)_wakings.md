---
title: "Monitor resolution reverts after (some) wakings"
date: 2016-01-18
forum: General Help
---

### Post by jamesisin on 2016-01-18
I am running Ubuntu 14.04 (64) on a ThinkPad 520 with the latest NVidia driver through an external Dell IPS 4K monitor (at resolution 2560x1440).

I have set this resolution in Display and I have saved the config file (/etc/X11/xorg.conf) using the NVidia utility.

I have confirmed (cat /etc/X11/xorg.conf) that my preferred resolution remains in the file, yet my resolution still occasionally reverts to 1920x1080.

(Also, my open applications get shuffled from desktop to desktop even if the resolution doesn't change.  Also also, very rarely the conf file reverts to default and I have again save it through the NVidia utility.)

(Just for clarity, the display goes to sleep not the laptop.)

How can I get my resolution to stay where I put it?

---

### Post by jamesisin on 2016-01-19
Anybody know how to get the resolution to stay where I set it?

I'm thinking it might be related to compositing.  It seems to happen after sleep and when I show all apps using spread all apps the first time.

---

### Post by jamesisin on 2016-01-20
Nope, it's not compositing.  This morning I waited without spreading applications (or any other compositing related action) and after maybe 20 seconds the display resolution downgraded itself nonetheless.  (Again with the conf file in order.)  (It seems rebooting may be what sets the conf file.)

Is there anybody who has any insight into this?  It is happening ***every single time*** I return from leaving my desk.  It should not happen.

---

### Post by jamesisin on 2016-03-08
Does no one have any insight into this issue.  It's really driving me nuts.

---

