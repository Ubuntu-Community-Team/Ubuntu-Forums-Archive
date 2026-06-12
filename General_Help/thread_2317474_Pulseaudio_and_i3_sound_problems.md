---
title: "Pulseaudio and i3 sound problems"
date: 2016-03-16
forum: General Help
---

### Post by willwh2 on 2016-03-16
Hi guys,

If I log in via unity, my sound works just fine.

I'm using i3 as a window manager, and when I restart my machine, when I first start chromium, (or google-chrome), my sound doesn't work.

I see the following in syslog: [https://gist.github.com/willwh/21e8dbc94ee754e48b64](https://gist.github.com/willwh/21e8dbc94ee754e48b64)

In that gist I also have screenshots from pavucontrol, on boot, after starting chrome, where my sound is broken. Then what pavucontrol looks like after I restart chrome, and my sound works.

I'm trying to understand how I might troubleshoot this.

I tried enabling autospawn in ```
/etc/pulse/client.conf

```

That didn't seem to help, and I'm not sure where to go from here. Any advice appreciated :)

---

### Post by mastablasta on 2016-03-17
so chromium/chrome is started on boot?

I dont' think this has to do with i3.

---

### Post by Tadaen_Sylvermane on 2016-03-17
Start pulse in your ~/.i3/config

I also had to comment out /etc/pulse/default.pa line that suspended the sinks.

Make sure your user is in the audio group as well.

---

