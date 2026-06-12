---
title: "Usual question - Wireless PCMCIA Laptop Card for Laptop"
date: 2006-10-15
forum: General Help
---

### Post by ade234uk on 2006-10-15
Usual question, what Wireless PCMCIA Laptop Network Cards work with Ubuntu. I am currently using a BT one which is not covered under the NDIS Wrapper.

---

### Post by koholint1000 on 2006-10-16
Right (Sigh) ...

The VAST majority of wireless cards and integrated wi-fi chips work out-of-the-box; and many USB dongles work out-of-the-box. However, if yours doesnt, use " ndisgtk ". I'm quite sure that it is available through Synaptic, or " sudo apt-get install ndisgtk ".

If all else fails, use trusty Google.

When you do get hold of it; it will need extra files to set itself up, that either requires an active internet connection (trusty cable), or an Xubuntu CD. Fortunately I had one already, but, try this anyway; and it should work.

^_^

---

