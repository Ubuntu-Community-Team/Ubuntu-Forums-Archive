---
title: "SSH - Agent admitted failure to sign using the key"
date: 2016-09-09
forum: General Help
---

### Post by dn1987p on 2016-09-09
Hello everyone,

I just set up a second SSH-Key on my VPS (I did so by using ssh-copy-id). Now I have the issue, that I just receive the error message "Agent admitted failure to sign using the key" when trying to log onto the server with the new key, while the first key is working just fine (on another computer with another account though - I set both keys up identically).

I did some research [1] [2] and found out that when adding SSH_AUTH_SOCK=0 right before the ssh command everything works just fine.

While all of the solutions I found simply did "ssh-add" or removed the ssh key agent from starting automatically, this did not fix the issue for me.

Anyone got an idea?

I'm using Lubuntu 14.04 LTS on both, server and client.

[1] [https://chrisjean.com/ubuntu-ssh-fix-for-agent-admitted-failure-to-sign-using-the-key/](https://chrisjean.com/ubuntu-ssh-fix-for-agent-admitted-failure-to-sign-using-the-key/)
[2] [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/201786](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/201786)

---

