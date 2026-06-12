---
title: "Git authentication problem with 18.10"
date: 2019-03-07
forum: General Help
---

### Post by vagrod on 2019-03-07
Hi! I am using git to access my repos on azure devops. I recently switched from Manjaro (long story short -- Manjaro killed itself after another update), so I decided to stick with something more stable. I clean-installed Ubuntu 18.10.
But here is a problem: when I try to git clone or git pull, I get Fatal: Authorization failed, for my devops repo. 
I have another machine, with KDE Neon on it. I tried to git clone there... and it worked, with same command and same username-password. It worked on Manjaro too. So there is some problem with Ubuntu 18.10 that prevents git from logging in and cloning a repo.
I really don't want to jump to yet another distro because of that, but it is a dealbreaker. If this won't work on Ubuntu, I will be forced to install distro that works.
I created test private repo on github, and it worked. I've no idea what in devops ubuntu does not like.
Thank you in advance ;)

UPDATE: I was able to set up devops repo on this machine using ssh. It still does not work with https devops repos thou.

---

