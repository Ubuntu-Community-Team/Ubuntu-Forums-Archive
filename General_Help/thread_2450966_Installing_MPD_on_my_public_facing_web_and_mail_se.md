---
title: "Installing MPD on my public facing web and mail server"
date: 2020-09-23
forum: General Help
---

### Post by llamabr on 2020-09-23
Hello, smart ubuntu-ers. I'm thinking of installing mpd on my web server, which is always on, is connected to my router, and runs apache web server and a mail server. It is mostly vanity pages, but it's still public facing.

is there any risk to running mpd on this machine, given that it's facing the world? It seems like the best choice since it's the only machine that's always on and running in the house. Is there any reason not to do this?

Thanks

---

### Post by SeijiSensei on 2020-09-23
At a minimum, make sure you [bind the server]("https://www.musicpd.org/doc/html/user.html#listeners") to listen only on localhost and your local area network. it should not be visible from outside like the web server is.

---

### Post by ActionParsnip on 2020-09-23
Could bind the service to localhost then use an SSH tunnel to the service to securely access it over the web
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)
Has a nice section on SSH running.

---

