---
title: "Firefox about:config setting automatically changed"
date: 2007-11-15
forum: General Help
---

### Post by popophobia on 2007-11-15
Especially the line network.http.max-connections, network.http.max-connections-per-server, network.http.max-persistent-connections-per-proxy and  network.http.max-persistent-connections-per-server.

I tried to lower it to 48, 16, 16, 8 respectively (still a boost from default value), but after a few restart of firefox, it automatically changed to 204, 120, 16, 51. I don't know how to make the setting "stick". It's very annoying when firefox become sluggish because of this high settings. I have to set it back every time!! Is it a well known bug or is it just me?

---

### Post by popophobia on 2007-11-19
Any help, please? Where should I look for the startup scripts of firefox (which can possibly be the source of error).

---

### Post by noynac on 2007-11-19
You can make those settings permanent by placing them in the user.js file in the ~/.mozilla/firefox/*.default/ directory. Unless the higher settings are already set in the user.js file, I don't know why they wouldn't stick in about:config.

---

### Post by popophobia on 2007-11-21
I figured it out. It's DownThemAll plugin that keeps changing the value. I got it fixed though. Thanks

---

