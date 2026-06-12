---
title: "How to add custom module and daemon to Ubuntu 13.04"
date: 2013-05-29
forum: General Help
---

### Post by ryanvade on 2013-05-29
Hello.  I have been working on setting up the KIPR IDE on ubuntu. It allows for programming of the KIPR Link robot controller.  As of right now I made this script that will install it.  [https://github.com/ryanvade/kiss-script](https://github.com/ryanvade/kiss-script) Now I want to get the kernel to recognize the Link and allow the program to communicate with it.  I have built both kovan-kmod [https://github.com/kipr/kovan-kmod](https://github.com/kipr/kovan-kmod) (kernel module to expose the hardware on the kovan via udp) and kovan-serial [https://github.com/kipr/kovan-serial](https://github.com/kipr/kovan-serial) (Kovan serial daemon. Handles incoming USB and network connections.) Both are built and installed.  I am just not sure how to add the Daemon.  I would ask the KIPR developers but they are not helpful; never getting back to me. :confused:

---

