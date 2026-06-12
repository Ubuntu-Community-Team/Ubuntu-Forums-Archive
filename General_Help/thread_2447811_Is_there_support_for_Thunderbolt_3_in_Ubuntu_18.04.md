---
title: "Is there support for Thunderbolt 3 in Ubuntu 18.04?"
date: 2020-07-26
forum: General Help
---

### Post by miner_tom on 2020-07-26
New to this particular community and I hope that I have been able to access the correct help forum.

Yes, I have been searching posts here and in other areas but I can not get a definitive answer to the question concerning Thunderbolt 3 support. Found some posts that denied thunderbolt support.

I have Ubuntu working, on NON Thunderbolt compliant PCs, but I have one laptop that does support Thunderbolt 3 (I tested it under windows). But under windows I have not been able to get some important programs to work that I have had working on Ubuntu 18.04. I would like to replace the OS to Ubuntu 18.04 but I want to make sure that Ubuntu 18.04 does have Thunderbolt 3 support as it is imperative to the operation of my programs.

If there is support, do I need to do a kernel build?

Thank You.
Tom

---

### Post by collisiondomain on 2020-07-29
You could try live booting Ubuntu 18.04 to test if Thunderbolt works without having to commit to installing it (if Thunderbolt doesn't work at first, try installing the "bolt" package during the live session and see if anything changes).

---

### Post by oldfred on 2020-07-29
In my 20.04 Kubuntu install, synaptic says this.

Bolt
system daemon to manage thunderbolt 3 devices

> Thunderbolt 3 features different security modes that require
devices to be authorized before they can be used.

My system has no Thunderbolt, so cannot test, but was installed by default.

---

