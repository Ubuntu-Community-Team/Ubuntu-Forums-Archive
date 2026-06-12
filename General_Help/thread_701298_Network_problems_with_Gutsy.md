---
title: "Network problems with Gutsy"
date: 2008-02-19
forum: General Help
---

### Post by jackschmidt on 2008-02-19
I have a problem.  I'm using Xubuntu 7.10.  My connection keeps dropping after a while and it's not convenient.

At times I am able to revive it by stopping the network services and rmmod and modprobing skge again.

My motherboard is ASUS P4P800-E Deluxe and I'm using the onboard Network card.

Here's what I get normally.

ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available

When I try to restart network services...
 * Configuring network interfaces...                                            Ignoring unknown interface eth0=eth0.

And this is in the var log messages
ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 21
ACPI: PCI interrupt for device 0000:02:05.0 disabled
skge: probe of 0000:02:05.0 failed with error -95

---

### Post by jackschmidt on 2008-02-19
Some updates.

At times when I reload the skge module, it seems to be half-enabled or something, I couldn't get an IP address from my router.  I need some help.  Please.

I'm going to try to shut down acpi as per this thread:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=82291](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=82291)

---

### Post by jackschmidt on 2008-02-20
Just tried it and it didn't work.  Pulled out some more var log messages.

kernel: [ 4455.259843] skge eth0: addr 00:11:2f:6f:67:d5
kernel: [ 4455.514927] skge eth0: enabling interface
kernel: [ 4455.520061] ADDRCONF(NETDEV_UP): eth0: link is not ready
kernel: [ 4456.181686] skge eth0: disabling interface
kernel: [ 4465.349104] skge 1.11 addr 0xfeaf8000 irq 22 chip Yukon-Lite rev 7
kernel: [ 4465.350229] skge eth0: addr 00:11:2f:6f:67:d5
kernel: [ 4497.675480] skge 0000:02:05.0: unable to clear error (so ignoring them)

Please help me.  I need my Ubuntu box to work.  And no pun intended but I also need it for work.  Please help me!

---

