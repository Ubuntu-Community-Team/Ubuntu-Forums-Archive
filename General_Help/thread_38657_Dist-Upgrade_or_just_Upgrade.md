---
title: "Dist-Upgrade or just Upgrade?"
date: 2005-06-01
forum: General Help
---

### Post by Kyral on 2005-06-01
Okay, I've stopped using Synaptic in favor of the command line APT interface. Now I'm curious, should I use apt-get dist-upgrade or apt-get upgrade to get updates? According to the man page for APT, dist-upgrade is the "smart" upgrade method, which would seem better. Oh, before anyone asks, I'm NOT using the Debian Repos.

---

### Post by angkor on 2005-06-01
sudo apt-get update
sudo apt-get upgrade
is good enough

apt-get dist-upgrade comes in when changing branches, for example when you want to change from Hoary to Breezy

---

