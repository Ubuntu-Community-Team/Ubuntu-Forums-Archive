---
title: "Ubuntu boots very slow but fast with upstart"
date: 2015-08-24
forum: General Help
---

### Post by Canaryguy on 2015-08-24
Hello,

In the Grub menu I have:
- Ubuntu, with Linux 3.19.0.26-generic
- Ubuntu, with Linux 3.19.0.26-generic (upstart)
- Ubuntu, with Linux 3.19.0.26-generic (Recovery mode)

When I choose the first option the system boots very slow. But when I choose upstart it loads very fast. How can I make upstart the default option instead of having to choose if manually when I turn on the computer?

---

### Post by v3.xx on 2015-08-24
see here

[https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart](https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart)

---

### Post by Canaryguy on 2015-08-24
Thank you v3.xx it worked.

sudo apt-get install upstart-sysv
sudo apt-get update update-initramfs -u

The only problem that I see with upstart is that the system doesn't remember the bright level and it's always at the maximum level when the session starts.

---

