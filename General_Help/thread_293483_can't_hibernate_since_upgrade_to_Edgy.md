---
title: "can't hibernate since upgrade to Edgy"
date: 2006-11-05
forum: General Help
---

### Post by jnoreiko on 2006-11-05
When I choose Hibernate, I get:

- a quick flash of screensaver
- a black screen
- then the "switch user" dialog -- as if I was restoring from hibernation

All I can do is log back into my gnome session.

Hibernate used to work absolutely fine before the upgrade to Edgy.

---

### Post by Freddd on 2006-11-06
Same problem here, worked before :(

---

### Post by jnoreiko on 2006-11-07
Found a bug already filed for this:

[https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/69882](https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/69882)

---

### Post by Tim.thelion on 2006-11-07
this is the problem: [http://ubuntuforums.org/showthread.php?t=287096](http://ubuntuforums.org/showthread.php?t=287096)

---

### Post by Tim.thelion on 2006-11-07
wait wait! there is more... [http://ponderer.org/ubuntu_edgy?reply](http://ponderer.org/ubuntu_edgy?reply) I also had to add the resume line...

---

### Post by jnoreiko on 2006-11-09
Thanks for the links! :D

I followed the exact instructions here: [https://launchpad.net/distros/ubuntu/+bug/66637/comments/23](https://launchpad.net/distros/ubuntu/+bug/66637/comments/23)

and hibernating works as normal. 

(Of course, 'normal' means I have to wait 10 minutes after resuming to launch any new apps... [https://launchpad.net/distros/ubuntu/+bug/61924](https://launchpad.net/distros/ubuntu/+bug/61924) *sigh*)

---

### Post by Mr. Picklesworth on 2006-11-24
This is a really weird bug.

I have had hibernate work for me twice with Edgy, but it has never worked again.

First time I tried Hibernate, it went fine. I got some really weird and horrible graphics glitches (I filed [a bug](https://bugs.launchpad.net/distros/ubuntu/+source/usplash/+bug/70543) on those!) but it shut down and restored my session *faster* than with a regular shutdown.
Since then, it has inexplicably not worked except just recently when, by some fluke, I managed to trick it into working by trying again and again and again and again at clicking that little Hibernate button...

This is with a full install of Edgy from CD (not an update from Dapper), by the way. (Although it's actually updated from a beta).

I believe my swap partition is working:
```

$ sudo swapon -s
Filename                                Type            Size    Used    Priority
/dev/hda5                               partition       554200  198348  -1

```

---

### Post by jnoreiko on 2007-05-08
This bug is back in Feisty.
It looks like the swap is off, so I'm in the process of following the same steps as last time. mkswap has given me a new UUID so everything needs changing.

I'm getting some errors I don't understand:

```
$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.20-15-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.

```

---

