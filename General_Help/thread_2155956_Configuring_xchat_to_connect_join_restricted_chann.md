---
title: "Configuring xchat to connect join restricted channels automatically"
date: 2013-06-20
forum: General Help
---

### Post by japhyr on 2013-06-20
I am trying to configure xchat on a new installation of 12.04. I want to automatically join two channels, one is restricted and one is not. I have xchat configured to run my nickser identify command on connection. But when I start xchat, it tries to connect to the restricted channel before the nickserv identification process has completed. I can wait a moment and then join that channel manually, but it never joins the channel automatically.

Is there any way to have xchat wait until the identify command completes, before connecting to a restricted channel?

---

### Post by japhyr on 2013-06-20
I ended up figuring this out. I put my nickserv password in as the server password under freenode's configuration settings, and removed the nickserver identify command.

---

