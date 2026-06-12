---
title: "Could not boot after installing uswsusp"
date: 2013-01-29
forum: General Help
---

### Post by jmspiers on 2013-01-29
This problem is resolved but I wanted to post my solution here since I see quite a few threads about it all over the place. None of the ones I saw mentioned this solution as an easy thing to try first so hopefully this will help someone.

I tried installing the uswsusp package to get my laptop to hibernate (Ubuntu 12.10). Needless to say I should have RTFM first because I needed to do more than just install that package, not to mention that uswsusp doesn't seem to be the right way to enable it for 12.10.

Anyway, after installing it my laptop would not boot. It hung on the Ubuntu loading screen with the 4 dots. Trying to reboot into recovery mode gave this error:

```
Could not stat the resume device file '/dev/dm-0'
```

I saw some threads saying to install gparted and create a swap partition, but when I tried to install gparted through the package manager I got this error:

```
cryptsetup: WARNING: found more than one resume device candidate:
            cryptswap1
            b8117daf...etc
```

The solution that worked for me was:

[LIST=1]
[*]Edit the boot command in grub to include "noresume". This bypasses the error and lets you go ahead and boot
[*]Uninstall uswsusp through the package manager
[*]Comment out the "/dev/mapper/cryptswap1 none swap sw 0 0" line in /etc/fstab
[/LIST]

Unfortunately I do still have two problems. First, shortly after logging into Ubuntu I get an error saying that there's a system problem. I haven't looked into it yet but it doesn't seem to affect anything. The second problem is that the timer is gone from the Grub menu.

I'm sure both of those problems are resolvable now that the system will actually boot. On top of that I learned my lesson: RTFM.

Hope this helps someone else :)

---

