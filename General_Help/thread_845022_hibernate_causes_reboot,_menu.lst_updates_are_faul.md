---
title: "hibernate causes reboot, menu.lst updates are faulty, wlan problems"
date: 2008-06-30
forum: General Help
---

### Post by excogitation on 2008-06-30
I still have to resolve these (few) issues to become an even happpier Ubuntu user.

First and most important:

When I chose hibernate from the shutdown menu I get a message like [ 891.422207][fglrx:KCL_enable_pat] *ERROR* Pat entry 2 is already configured

[reported here]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/234125")

But I don't even know if that has anything to do with the reboots.

After the reboot the system returns to it's previous state, so technically hibernation is working.


After resuming my wlan connection isn't working and I have to start network-admin and enter the password again (although the dots are there) and after that the wlan connection works again.

Btw, why doesn't the network-admin display the right location (any) when starting and why doesn't it keep the passwords when switching locations? (isn't it pretty much useless like this?)


When my menu.lst gets updated I the parameters like defoptions, howmany, updatedefaultentry get ignored.
That's annoying. Might gfxboot be causing this problem?

---

### Post by excogitation on 2008-07-01
bump.

Also - if I call /etc/acpi/hibernate.sh 
Hibernation works fine (without any messages - just a black screen).

---

