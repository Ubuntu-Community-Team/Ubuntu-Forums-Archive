---
title: "How to setup ssh so I can access securely over android device?"
date: 2018-07-21
forum: General Help
---

### Post by freeworld4 on 2018-07-21
I have it installed already I tried many guides online and a lot of them are incomplete or don't make sense to me. Could someone help me out?

---

### Post by HermanAB on 2018-07-22
SSH consists of two parts, the client and the server.  My guess is that you only installed the client.

---

### Post by freeworld4 on 2018-07-22
I want to be able to ssh into my computer over home network and from the outside. I installed the server via this command: "sudo tasksel install openssh-server". I am trying to connect from an android device because I would like to use a command line app called youtube-dl.  I tried the following guides with no luck maybe it is the client I am using with android?? I think it is juicessh or something my phone is off and charging so don't know. I think I'll try out connectbot next for ssh client on android see if it is a client issue. I followed these guides with no luck: [https://help.ubuntu.com/14.04/serverguide/openssh-server.html](https://help.ubuntu.com/14.04/serverguide/openssh-server.html) [https://linuxconfig.org/how-to-install-ssh-server-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-ssh-server-on-ubuntu-18-04-bionic-beaver-linux) [https://idroot.net/linux/install-ssh-server-ubuntu-18-04-lts/](https://idroot.net/linux/install-ssh-server-ubuntu-18-04-lts/) [https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1804](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1804)

---

### Post by freeworld4 on 2018-07-22
I used this guide and solved my issue. [https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

---

### Post by freeworld4 on 2018-07-23
How do I Upnp forward ports so I can use ssh behind a router?

---

### Post by freeworld4 on 2018-07-23
nevermind I port forward the port in the router

---

