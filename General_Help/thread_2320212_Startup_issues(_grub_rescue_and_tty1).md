---
title: "Startup issues( grub rescue and tty1)"
date: 2016-04-11
forum: General Help
---

### Post by Evil Wayz on 2016-04-11
I cloned a bad drive, and then expanded the partition to make use of all available space.  WHen I did this, the first time I got an error and invalid filesystem and it dropped to grub rescue prompt.  So I rebooted with a live usb key, and using boot repair, fixed my grub.  I rebooted, and I got this error:

```
 error attempt to read or write outside(Hd0)
```

But before I could do anything, it started running tasks.  And then it dropped to

```
Ubuntu 14.04,4 LTS tty1
shaitan login:
```

but before I could log in, it went back to the verbose text mode, and then it popped me straight to the login screen.  Everything seems to be working fine once I get there, but I don't like these errors, I would prefer my system to be operating normally instead of appearing to operate normally. 

I am using Ubuntu 14.04.4 LTS, with CInnamon 2.8 and the 4.3 kernel.  THe drive I cloned was 35 gb, the new drive is 1.8 tb.

---

