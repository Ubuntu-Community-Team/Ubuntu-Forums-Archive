---
title: "hang on bootup [gusty]"
date: 2007-10-22
forum: General Help
---

### Post by dracomordag on 2007-10-22
the problem has drastically changed: please see [http://ubuntuforums.org/showpost.php?p=3687364&postcount=8](http://ubuntuforums.org/showpost.php?p=3687364&postcount=8)

---

### Post by dracomordag on 2007-10-25
any ideas? it's working more consistently now, despite the fact that I haven't changed anything. Maybe there was some random update.

---

### Post by dracomordag on 2007-10-27
alright, now i literally just can't boot into ubuntu.

kern.log reports (I can only access it because I can read/write to ext with vista... i can't even get to a terminal if i try to boot into ubuntu) the following:

[http://pastebin.com/f373701f](http://pastebin.com/f373701f)

---

### Post by dracomordag on 2007-10-29
no one?

---

### Post by nowshining on 2007-10-29
is ur board an intel board?

---

### Post by dracomordag on 2007-10-29
yessir.

"2.4 GHz Dualcore Intel t7700, 2 GB RAM, nVidia 8400, Windows Vista attempting to dualboot with Gusty Gibbon"

---

### Post by nowshining on 2007-10-29
it's a know problem if ur using SATA or ATA IDE drives ur lucky to at least boot up into the OS Gutsy this will be fixed in 2.6.23 kernels and I do have and use 2.6.22-12 which works fine, or intel boards and waiting for hardy to show up with the 2.6.23 kernel. :) so urs may be the same probs others are having with the 2.6.22-14 kernel. :)

if u want I can get u the -12 kernel and headers and junk but u'll have to go thru a torrent. :) and I'm on dialup so u'll have to be patient and I only get 3hrs. a session. AS also I don't what could be happening on ur side at all and it's just a guess and such...

---

### Post by dracomordag on 2007-11-01
alright, I've done some poking around (editing my GRUB, xorg.conf, etc), and I've gathered the following:

on standard bootup, I can now press ctrl-alt-F2 to get a terminal, 
before I type anything, the screen reads this:
```
[19.769980] PCI: failed to allocate mem resource #6:20000@e0000000 for 0000:0
1:00.0
Loading, please wait...
Warning: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'uvc video'
Warning: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'uvc video'
kinit: name_to_dev_t (dev/disk/by-uvid/86a2594a-f056-4c96-aab4-72151d12592) = sda4(8,4)
kinit: trying to resume from 86a2594a-f056-4c96-aab4-72151d12592
kinit: no resume image, doing normal boot...

```

when I login and type startx (after removing the X0.lock):
```
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up
xinit: unable to connect to x server
xinit: no such process (errno 3): server error
```

I forget when this one comes up, but:
```
Failed to initalize GLX extension (compatible NVIDIA X driver not found) Atom 4, Card 32 4, unsigned lang 4
```

---

### Post by dracomordag on 2007-11-02
i hate to be that guy, but seriously... if you're going to try to win over users to Ubuntu, you can't let someone come in and say "I literally can't boot into the OS despite the fact that it worked 10 minutes ago" and not give one single hint over the course of a week. Over the year or so that i've been using ubuntu, i've had great support... but as soon as I actually have a serious issue, no one helps.

---

