---
title: "network is not set on automatically"
date: 2007-10-22
forum: General Help
---

### Post by fabrun on 2007-10-22
Dear users,

I have a simple problem: my network is not started when I log in. I have to type 'ifup eth0' to have network working.

Here is the content of my 'interfaces' file:
---
auto lo
iface lo inet loopback

auto etho
iface eth0 inet dhcp
---

Thanks for any help.
Have a nice day.

---

### Post by bit4 on 2007-10-22
the 'auto' line (before last line) refers to etho (with a lowercase Oh, instead of a zero). Is that a typo in the post, or is it really that way in the file? It should be a zero...

---

### Post by seldenthuis on 2007-10-22
If you use NetworkManager, your /etc/network/interfaces should only contain the first two lines.  NetworkManager will automatically bring the other interfaces up when you log in.

---

