---
title: "Help with inhibiting suspend with systemd"
date: 2015-05-15
forum: General Help
---

### Post by henrixd on 2015-05-15
Hello!

Can't seem to make this work properly.
I would like to inhibit suspend when minidlnad has active client, vlc is playing video or browser is full screen (playing video).

Best success I have had is with python-script using DBus. Using DBus will inhibit suspend properly but doesn't do normal suspend after uninhibit anymore.

I did try to add script to /usr/lib/systemd/system-sleep/ as was suggested in [https://wiki.archlinux.org/index.php/Power_management#Sleep_hooks](https://wiki.archlinux.org/index.php/Power_management#Sleep_hooks). I did also try systemd service files without any success. With these methods I was not able to get scripts run at all.

I'll rather not use programs like caffeine because I want to be able to control the conditions fully. All ideas are welcome.

I'm running XUbuntu 15.04.

---

