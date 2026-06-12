---
title: "Encrypted swap problem"
date: 2008-05-28
forum: General Help
---

### Post by YannH on 2008-05-28
Hi,

Until today I had the perfectly-working setup :

[LIST]
[*]gutsy
[*]software raid-1 (actually I probably should have used raid-0 for swap, but I doubt it is relevant here)
[*]luks-encrypted /, /home and swap
[*]hibernation on swap
[/LIST]

The boot sequence was roughly :
[LIST]
[*]unlock / by password
[*]unlock swap by password
[*]recover my session (/home being unlocked by a keyfile under /etc)
[/LIST]

I don't know what has changed since yesterday (I may have performed an "aptitude safe-upgrade", don't remember but the kernel is now 2.6.22-14-generic), but now at boot time I have
[LIST]
[*]unlock / just the same
[*]something like "cannot stat resume device /dev/mapper/cryptswap ... press enter to skip"
[*] ...some things...
[*]unlock swap by password
[*] ...finish boot...
[/LIST]

So in the end, I'm able to boot the system, but not to wake from hibernation, as it seems my swap is "luksOpened" too late. Any idea where I could fix this ?

My /etc/uswsusp.conf is as following :
```
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = /dev/mapper/cryptswap
compress = y
early writeout = y
image size = 976995368
RSA key file = /etc/uswsusp.key
shutdown method = platform
```

My /etc/initramfs-tools/conf.d/resume :
```
RESUME=/dev/mapper/cryptswap
```

And my /etc/crypttab :
```
# <target name> <source device>         <key file>      <options>
croot   /dev/md2        none    luks
cryptswap       /dev/md1        none    luks
chome   /dev/md3        /etc/keys/home.key      luks
```

Note: I've already done a "update-initramfs -u" but with no success.

Thanks in advance for any hint !

---

### Post by YannH on 2008-05-29
Finally I upgraded to Hardy during the night (hoping that nothing would break), and the problem is gone. Still, it's not very reassuring.:-k

---

