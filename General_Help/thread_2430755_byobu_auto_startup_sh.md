---
title: "byobu auto startup sh"
date: 2019-11-07
forum: General Help
---

### Post by Whiteice on 2019-11-07
I have recently had a power outage on my ubuntu server and it is kind of annoying to manually need to restart two of my minecraft servers  in separate screens when this happens. I'm wondering how I can start up the servers that I have .sh written for automatically when the server boots. I need them to be in two separate byobu windows so I'm unsure if cron can do this. Any suggestions?

---

### Post by webaake on 2019-11-07
I think the best way for that is the old rc.local file. It's read and executed at boot. You probably have to create it - /etc/rc.local

More about it here: [https://vpsfix.com/community/server-administration/no-etc-rc-local-file-on-ubuntu-18-04-heres-what-to-do/](https://vpsfix.com/community/server-administration/no-etc-rc-local-file-on-ubuntu-18-04-heres-what-to-do/)

---

