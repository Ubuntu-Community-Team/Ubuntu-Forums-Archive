---
title: "Language support appears to be incomplete even after installing all packs?"
date: 2015-08-19
forum: General Help
---

### Post by roland-logikalsolutions on 2015-08-19
Ubuntu-15 64-bit

Building a custom ISO for machines which have less than zero network, let alone Internet connection. A user complained, rightly so, that a few minutes after installation they saw this "Language support appears to be incomplete" nag-o-gram popup. "No problem" I said. "We will simply install all language packs since there is more than enough room on the DVD." So I did.

During the build script I chroot into what I'm building and basically run this:

```

apt-get clean
rm -rf /tmp/* ~/.bash_history

rm /var/lib/dbus/machine-id

rm /sbin/initctl
dpkg-divert --rename --remove /sbin/initctl

umount /dev/pts
umount /sys
umount /proc || umount -lf /proc


```

I wait the extra 45+ minutes it added to the build to pull down and apply all packs. I install into a VM with Network connection turned of. After it runs a few minutes I __still__ get the "Language support appears to be incomplete" nag-o-gram.

Question 1: Should I be using something else to identify everything to install?

Question 2: Is this really just a timed nag-o-gram too stupid to realize there is no network connection? If so, how do I nuke it from existence when creating the ISO. I assume there is a file I can delete.

Thanks,

---

