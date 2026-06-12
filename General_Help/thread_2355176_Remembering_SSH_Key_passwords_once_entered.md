---
title: "Remembering SSH Key passwords once entered?"
date: 2017-03-10
forum: General Help
---

### Post by PrinceVince on 2017-03-10
In the past I've been using SSH keys generated without password, but now that I use one, I noticed that **Xubuntu** doesn't remember them, prompting me every time I connect. I would like to enter it when connecting to my VPS and have it remembered for the duration of my Desktop session.

Simply running an instance of **ssh-agent** and adding the key manually won't work for newly opened terminals (due to reliance on environment variables). I looked into [keychain]("https://code.launchpad.net/ubuntu/+source/keychain"), but that seems to be designed for entering your password into a terminal on login, i.e. it wouldn't suit me logging into an XFCE session directly, wishing to unlock the key on demand.

Is there a convenient way to accomplish this in **Xubuntu**, preferably without being asked upfront, but rather when I invoke SSH with that key?

---

