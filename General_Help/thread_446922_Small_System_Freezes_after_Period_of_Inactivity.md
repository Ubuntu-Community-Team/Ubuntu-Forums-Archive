---
title: "Small System Freezes after Period of Inactivity"
date: 2007-05-17
forum: General Help
---

### Post by futureal on 2007-05-17
Hi all,

I have a computer that I just installed Feisty on, that's having an odd issue. I have openssh and samba running on it, and when I tab out of the shell to do something else, when I come back it freezes for about 5-10 seconds after one keystroke.

Similarly, if I access a samba share after a period of inactivity, it freezes up for a few seconds before displaying the directory list.

I previously had Edgy on this, although this was a completely fresh install, not a dist-upgrade. Could there be a setting somewhere that is causing a hard drive to power down, or something else that may be causing this?

Thanks!

---

### Post by mbradlcu on 2007-05-17
you may want to install gkrellm to see what spikes when it happens. My guess is it isn't the HD powering down but more network/connection issue assuming this issue only happens when you have a samba/ssh session established.
1 last thing, I had this issue once but it was due to my mail client retrieving messages from the server, most likely a different cause but the problem looked the same.

---

### Post by futureal on 2007-05-17
Not a bad idea!

I installed gkrellm and went about duplicating the freezes, but it doesn't look like any of the CPU, memory, or disk is spiking particularly high when this happens.

I'd agree that it's pretty reasonable to assume it's a networking problem, although I'm at a loss as to how to further debug it.

---

### Post by mbradlcu on 2007-05-17
this gets a little above my threshold but if you want to get down and dirty use the tcpdump command, here's a couple examples of common usages:
tcpdump -t -i eth0 host {host_you_want_to_allow_through_filter} and tcp port {port-number}

you can omit the host and port to see all traffic.

---

