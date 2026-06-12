---
title: "enabling iptables in kernel .config"
date: 2006-07-07
forum: General Help
---

### Post by nismohasan on 2006-07-07
acording to firestater i've somehow managed to disable iptables in my new kernel (2.6.17.4) and can't seem to find the option in xconfig

what do i need to enable?

i've got a copy of my .config file that i can edit in gedit or w/e if someone could tell me which lines to modify.

cheers.

---

### Post by RavenOfOdin on 2006-07-07
> **nismohasan said:**
> acording to firestater i've somehow managed to disable iptables in my new kernel (2.6.17.4) and can't seem to find the option in xconfig

what do i need to enable?

i've got a copy of my .config file that i can edit in gedit or w/e if someone could tell me which lines to modify.

cheers.

Hit Ctrl-Alt-F1 and go in through menuconfig instead.

2.6.16.18 had the entries located in Network Options > Network packet filtering (required for iptables) > Core Netfilter Configuration / IP : Netfilter Configuration.

For "Core Netfilter Configuration", unless I'm wrong, you should build in CONNTRACK, MARK, STATE, TCPMSS, MAC, LENGTH, LIMIT, HELPER. You can build all of the core modules in if you want and they'll be used on demand by the kernel, but these are just some you may want to keep.

Then in "IP: Netfilter Configuration" . . . Look for the entry that says "iptables support" on the left side of the screen. Its symbol should be CONFIG_NF_IPTABLES. Build it in as a module by hitting the "M" key. Once you do that, if you're on the right module, a bunch of other options should pop up. 

Its been a while since I compiled any kernels, I've been playing around with my iMac and the last one I did was 2.6.16.18. I still have to get 2.6.17.4 to work on either of my PC's.

---

