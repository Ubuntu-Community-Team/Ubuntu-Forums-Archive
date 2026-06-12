---
title: "Protocols (rsync, ssh, nfs, ipp) working only in one direction"
date: 2007-08-16
forum: General Help
---

### Post by jackn on 2007-08-16
I've got two boxes connected to a router. One is a wirelessly connected laptop, the other a USB-connected desktop.
This is crucial: both boxes always have access to the net, and they can always ping each other

In contrast, four protocols - rsync, nfs, ssh and ipp - will often only work in one direction. Sometimes, they work fine, allowing communication from either box to the other. But such episodes are short-lived, and often the protocols only work from the desktop to the laptop, but not the other way around. The four protocols always work or do not work in unison. It seems to be a general issue having to do with communication protocols that are higher level than pinging.

When things are alright, I will be working for a while when another test suddenly shows failure from the laptop to the desktop again. The next moring, say, things will be fine again.
When the laptop can't get through to the desktop, the cursor just hangs until the attempt times out.

Looking at the desktop's /var/sys/syslog, there is no trace of communication attempts from the laptop, suggesting that the desktop is not aware of the laptop's attempts.

At one point, I thought I sorted this out by [restarting NetworkManager]("http://ubuntuforums.org/showthread.php?t=341357"). This procedure does not restore bidirectional communication now.

I don't know whether this a networking issue at all.

What can be done?

Thanks,
jackn

---

