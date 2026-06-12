---
title: "Laptop Shuts Down / Freezes When Idle"
date: 2008-04-13
forum: General Help
---

### Post by xarathustra on 2008-04-13
I am running Kubuntu Gutsy with a year-old Dell Inspiron 1501 Laptop (Mobile AMD Sempron 3500+ [1.8GHz/512KB])  .  It has recently - the last month - begun to "shut down" or "freeze" on me leaving me with a blank screen except for the blinky cursor in the upper-left corner.  I then have to power off with the power button and power back on.  This happens every time I have my laptop on unless I shut down manually.  I don't seem to be losing anything, but having this happen so often is relatively annoying.

In all instances, I believe, KTorrent has been running in the background.  In some instances Amarok has been running (playing music - it is always on in the background) and in others Kaffeine, but never both.  It is also the case that Kontact and Firefox are sometimes running.  The only times it doesn't happen to me are when I am physically manipulating my computer (i.e. typing, moving the mouse).

For the past year I would put the average daily time that the computer is on at around 15 hours since I only shut it down to transport it and when I feel the rare urge to do so.  I don't think that my laptop is overheating since the couple of times it has done so I was unable to reboot it for a few minutes and these instances all allow immediate reboots.

I'm not sure what else to post that would help, but here is what I pulled from KSystemlog for what I believe to be the last instance of this happening.  This particular instance seems to me to have occurred much more quickly than past instances.:


6:59:08 restart.
Job `cron.daily' terminated
Normal exit (1 job run)
-- MARK --
[ 1243.792000] APIC error on CPU0: 40(40)
(root) CMD (   cd / && run-parts --report /etc/cron.hourly)
-- MARK --
-- MARK --
Interface eth1.IPv4 no longer relevant for mDNS.
Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.104.
Withdrawing address record for 192.168.1.104 on eth1.
Withdrawing address record for fe80::219:7dff:fe99:8bc9 on eth1.
[ 4431.704000] ACPI: PCI interrupt for device 0000:08:00.0 disabled
[ 4431.788000] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[ 4431.836000] ieee80211_crypt: unregistered algorithm 'NULL'
8:05:53 [ 4434.624000] PM: suspend-to-disk mode set to 'shutdown'

Any and all help is appreciated.  Thanks for your time.  Let me know if there is anything else I can post that will make it easier to diagnose.

tom

---

