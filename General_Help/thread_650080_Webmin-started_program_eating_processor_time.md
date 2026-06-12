---
title: "Webmin-started program eating processor time?"
date: 2007-12-25
forum: General Help
---

### Post by william_hunter on 2007-12-25
OK, here is something I have not one idea about:

I run a game server on 7.10 server, and use VNC and Webmin to control the whole thing headlessly. I start the game server app via shell script, and if I run it in a terminal window through VNC the server tends to run between 10-20% of one of the two processor cores relatively steadily. If I start the same app through a shell command executed in Webmin, it goes crazy, reporting processor usage of more than 100%. 

This usage is verifiable through VNC and System Monitor, so it appears that it is actually running at >100% processor. Anyone have a thought about why this might be?

---

