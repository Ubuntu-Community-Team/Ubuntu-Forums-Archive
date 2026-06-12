---
title: "Discovering mount directory"
date: 2008-02-03
forum: General Help
---

### Post by UmbraSolis on 2008-02-03
Hi, people.
I'd like to discover the mount point of a device.

I know i can simply type "mount" and look for the device, but I'd like to get something different.
I mean: if my device is /dev/hda1 and my mount point is /mnt/hda1, I'm looking for a command or a script which returns only "/mnt/hda1" as output, giving "/dev/hda1" as input.
I tried "mount | grep /dev/hda1", but the output is a long string of which I need just a substring.

What's the solution, then? Is there a command telling me exactly information I need or I have to go on trying with grep and regular expressions?

Thanks to all from now!

---

