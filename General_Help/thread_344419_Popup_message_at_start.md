---
title: "Popup message at start?"
date: 2007-01-22
forum: General Help
---

### Post by SZF2001 on 2007-01-22
After rebooting my Xubuntu computer, I get this message:

```
Could not look up internet address for ColeComp.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
ColeComp to the file /etc/hosts on your system.
```

Then asks if I want to continue as normal or try again.

Strangely enough, I can still get on the internet, even though this happens...

I downloaded the Network Manager app before the reboot, checked my setting and saved them. Well, I'm thinking that could be a reason for trouble?

Also, when I type in "cat /etc/hostname" and "cat /etc/hosts", I get this (in order of posting):

```
ColeComp
```

```
127.0.0.1 localhost
127.0.1.1 ColeComp.Belkin ColeComp.ColeComp

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I'm not quiet sure what to change in the file that the popup told me to screw around with, and by God I don't want to do another fresh install - I mean, this is Edgy *finally working for me at last*, except with this minor kink. It's kinda humbling when my Windows friends noticed and said, "Hey, a popup in Ubuntu, huh" and snickered. :mad:

---

### Post by riven0 on 2007-01-22
I'm not too knowledgeable about this, but if you changed **ColeComp.ColeComp** to just **ColeComp** would that make any difference?

---

### Post by SZF2001 on 2007-01-22
I could give it a try. If I don't post for a few hours, then you know what happened...

ONWARD! :guitar:

EDIT: Seems like that did the trick. Thanks!

---

