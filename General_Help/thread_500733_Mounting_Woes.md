---
title: "Mounting Woes"
date: 2007-07-14
forum: General Help
---

### Post by firebadger on 2007-07-14
I have a external USB drive that i'd like to mount on startup.  I've edited the /etc/fstab file adding the following entry to the bottom.

```
UUID=86c8e74c-9135-4ea3-a2c5-0a4ee0b1837f /media/disk ext3 defaults 0 0
```

However, when I reboot the drive does not get mounted, but if I run...

```
sudo mount -a
```

...it does!

Any ideas?

---

### Post by merlinus on 2007-07-14
You might try this:

UID=86c8e74c-9135-4ea3-a2c5-0a4ee0b1837f /media/disk ext3 defaults,auto 0 1

-merlin

---

### Post by firebadger on 2007-07-15
Thanks, I tried that and the process now fails spitting me into a shell displaying messages like this...

```
fsck ext3: Unable to resolve 'UUID=86c8e74c-9135-4ea3-a2c5-0a4ee0b1837f'
fsck died with exit status 8
```

If I run blkid it returns
```
/dev/sde1: UUID="86c8e74c-9135-4ea3-a2c5-0a4ee0b1837f" SEC_TYPE="ext2" TYPE="ext3"
```

I'm wondering if the USB drive simply isn't available at the stage in the boot process that the mounting is attempted.  Could this be the case and if so how can I resolve it?

---

### Post by firebadger on 2007-07-15
Any thoughts?

---

### Post by merlinus on 2007-07-15
You might try this, which means it can be mounted by any user rather than only root:

UUID=86c8e74c-9135-4ea3-a2c5-0a4ee0b1837f /media/disk ext3 [COLOR=#330099][FONT=Bitstream Vera Sans Mono][COLOR=#000000]rw,user  0  0

-merlin
[/COLOR][/FONT][/COLOR]

---

