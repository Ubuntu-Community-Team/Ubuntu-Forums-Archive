---
title: "[SOLVED] How to tunnel Synaptic through SSH socks proxy?"
date: 2008-01-18
forum: General Help
---

### Post by T0MA on 2008-01-18
Hi All,
I have a secure ssh tunnel working on port 4567 and I'm able to set up firefox, pidgin and everything that has SOCKS support to use this tunnel but I'm unable to install anything from Synaptic. I tried forwarding Synaptic through the ssh tunnel but no success.

Does anyone know how to do that?
Thx!

---

### Post by T0MA on 2008-01-18
Solution: install tsocks, configure it and start synaptic: sudo tsocks synaptic

---

