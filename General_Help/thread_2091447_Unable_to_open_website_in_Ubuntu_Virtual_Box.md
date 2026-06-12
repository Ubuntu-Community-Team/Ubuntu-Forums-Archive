---
title: "Unable to open website in Ubuntu Virtual Box"
date: 2012-12-05
forum: General Help
---

### Post by AR2012 on 2012-12-05
I have installed Ubuntu Linux VM in my Windows XP box.
I am able to open a test site of my company on Windows XP but when I login to Ubuntu linux and launch this site: I am getting an error: Server not found.

The network settings I have on LinuxUbuntu VM is
Adapter1 : attached to Bridge adapter.

I tried NAT as well. But nothing seems to work.

I also tried the following:
I deleted etc/udev/rules.d/70-persistent-net.rules but it does not help.

The output of ifconfig -a and lspci within Ubuntu is attached along with the output of ipconfig on my windows box.

Please help.

---

### Post by howefield on 2012-12-05
Is the issue confined to your test website, or can you not browse any website in your Ubuntu VM ?

---

### Post by AR2012 on 2012-12-05
It is confined to this test site.

---

