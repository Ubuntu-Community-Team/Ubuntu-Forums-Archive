---
title: "[SOLVED] Empty /dev/ folder"
date: 2008-01-04
forum: General Help
---

### Post by Zer0d on 2008-01-04
Somehow my /dev/ folder doesn't even contain one device anymore it only has a file named null, the content of this file is:
```
Failed to kill daemon: No such file or directory
```

This happened after I used gparted to format a new hard drive. I have some strange processes still running:

```

25196 ?        00:00:00 scsi_eh_8
25197 ?        00:00:00 usb-storage
25254 ?        00:00:00 scsi_eh_9
25255 ?        00:00:00 usb-storage

```

But they wont go away when I try to kill them with **kill -9 25196** or only **kill** command.

---

### Post by p_quarles on 2008-01-04
So, your /dev folder is (all but) empty, and /dev/null contains data? I'm surprised that your computer is working at all. 

Can you switch to another TTY (i.e., alt-ctrl-F2)? Can you mount a CD-ROM or USB flash drive? Is /var/log/kern.log reporting attached devices?

---

### Post by Zer0d on 2008-01-04
My computer seemed to work normal until I tried to play music then it couldn't find the sound card device and the computer locked up. But now Ubuntu is working again, strange why it happened in the first place.

---

### Post by p_quarles on 2008-01-04
> **Zer0d said:**
> My computer seemed to work normal until I tried to play music then it couldn't find the sound card device and the computer locked up. But now Ubuntu is working again, strange why it happened in the first place.
Wait, so you restarted and everything is back to normal? Is /dev still empty? 

I gotta say this is pretty strange. You may want to run fsck on the partition containing the /dev directory.

---

### Post by Zer0d on 2008-01-04
I restarted and everything inside /dev is back but the computer lost hard drive mount positions so going to fix my fstab file. It also lost sound card configurations, like I had IEC958 checked but it went away after crash.

---

### Post by eXeCuTeR+ on 2008-01-04
Edit: WRONG TOPIC, SORRY!

---

