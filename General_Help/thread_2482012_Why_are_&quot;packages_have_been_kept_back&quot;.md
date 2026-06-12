---
title: "Why are &quot;packages have been kept back&quot;?"
date: 2022-12-16
forum: General Help
---

### Post by smeerbartje on 2022-12-16
I have a couple of Ubuntu 22.04 LTS servers running on a Proxmox host. Every now and then "apt upgrade" gives me the following message saying that it skipped packages. But why is that? Why is -in this case- tmux being skipped? I usually solve this by running "aptitude safe-upgrade", but I would like to understand this behaviour.

[FONT=Courier New]me@playlist-exchange [~]$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
The following packages have been kept back:
  tmux
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[/FONT]

---

### Post by coffeecat on 2022-12-16
This recent thread explains about phased updates: [https://ubuntuforums.org/showthread.php?t=2481914](https://ubuntuforums.org/showthread.php?t=2481914)

---

### Post by smeerbartje on 2022-12-16
Oh wow, this is actually by-design!
Sorry, I wasn't aware of that. Well this explains it all, thanks!

(and it's true that aptitude safe-upgrade indeed forces the install and skips the "waiting period"?)

---

