---
title: "how to be certain that an external HD is mounted?"
date: 2022-06-26
forum: General Help
---

### Post by Old Jimma on 2022-06-26
Hello Ubuntuers:

I need a method for determining with certainty that an external hard drive is mounted. I mount external drives using a USB connection.

There is a reason why I need a method: "Things happen. Inadvertent errors are made. Sometimes things change, like UUIDs."

The effect of not being certain that a hard drive is mounted is that the operating system can be over written when an external hard drive is not really mounted. When this happens things will be written to the mount point.... and disaster is near! 

I've scoured the internet, and get things like "Check your fstab." 

However, if an error is made in verifying the fstab has the correct UUID, you are up the creek.

Friends, I'd be grateful to how I can determine with certainty of my external hard drives are mounted.

Thank you,
Old JImma

---

### Post by The Cog on 2022-06-26
**[FONT=Courier New]lsblk -fmap[/FONT]** shows the current mounts including the UUID.

---

### Post by #&amp;thj^% on 2022-06-26
Not pretty but it works:
```
 cat /etc/mtab
```
I can shorten that to look only for SD's
```
cat /etc/mtab | grep /dev/sd

```
Just remembered this as well:
```
cat /proc/mounts | grep /dev/sd

```

---

### Post by Old Jimma on 2022-06-26
Thank you, The Cog!!!

Sincerely,
Old Jimma

---

