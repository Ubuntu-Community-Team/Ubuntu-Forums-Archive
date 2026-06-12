---
title: "how to read boot time messages?"
date: 2007-06-13
forum: General Help
---

### Post by mdurham on 2007-06-13
Is there a way to slow down the messages that scream up the screen at boot time, to make them readable. I'm interested on one particular message but cntrl-S doesn't stop the scrolling at the correct point. Do these messages get written to a file anywhere? What is the point of the messages if they can't be read?
Cheers, Mike

---

### Post by danhm on 2007-06-13
For some reason, boot logging isn't enabled by default.

To enable:

```

$ sudo gedit /etc/default/bootlogd

```

Change the "no" to a "yes", and you'll be set. On your first boot with this, it might complain about the bootlog not exisiting, but it will still work.

---

### Post by mdurham on 2007-06-13
> **danhm said:**
> For some reason, boot logging isn't enabled by default.

To enable:

```

$ sudo gedit /etc/default/bootlogd

```

Change the "no" to a "yes", and you'll be set. On your first boot with this, it might complain about the bootlog not exisiting, but it will still work.

Thanks danhm, I did as you suggested but can't find any output file. Can you tell me where to find it and it's likely name please.
Thanks, Mike

---

### Post by infol on 2007-06-13
the log should be in /var/log/

---

### Post by Patrick K on 2007-06-13
Mine is here:
/var/log/boot

---

### Post by mdurham on 2007-06-13
> **Patrick K said:**
> Mine is here:
/var/log/boot

I do have a /var/log/boot text file but it was created 13th Feb 2007, so it's probably not the one I'm looking for.
Cheers, Mike

---

### Post by reclusivemonkey on 2007-06-13
```

dmesg | less

```

to learn more;

```

man dmesg

```

---

### Post by mdurham on 2007-06-13
> **reclusivemonkey said:**
> ```

dmesg | less

```

to learn more;

```

man dmesg

```

This does not help with boot screen messages!

---

### Post by reclusivemonkey on 2007-06-13
> **mdurham said:**
> This does not help with boot screen messages!

Yes it does. You clearly did not read the man page.

```

DMESG(8)                                                              DMESG(8)

NAME
       dmesg - print or control the kernel ring buffer

SYNOPSIS
       dmesg [ -c ] [ -n level ] [ -s bufsize ]

DESCRIPTION
       dmesg is used to examine or control the kernel ring buffer.

       **The program helps users to print out their bootup messages.**  Instead of
       copying the messages by hand, the user need only:
              dmesg > boot.messages
       and mail the boot.messages file to whoever can debug their problem.

```

I suggest before you dismiss people's help you do a little more reading.

---

### Post by mdurham on 2007-06-13
> **reclusivemonkey said:**
> Yes it does. You clearly did not read the man page.

```

DMESG(8)                                                              DMESG(8)

NAME
       dmesg - print or control the kernel ring buffer

SYNOPSIS
       dmesg [ -c ] [ -n level ] [ -s bufsize ]

DESCRIPTION
       dmesg is used to examine or control the kernel ring buffer.

       **The program helps users to print out their bootup messages.**  Instead of
       copying the messages by hand, the user need only:
              dmesg > boot.messages
       and mail the boot.messages file to whoever can debug their problem.

```

I suggest before you dismiss people's help you do a little more reading.

reclusivemonkey , I did as you kindly suggested but the message that I see flash by at boot time does not appear in the dmesg output. I see a message something  about disk lable followed by quite a few lines of info about the fstab file but it goes so fast I'm unable to read it. **None **of this appears in the dmesg file.
Thanks for you help anyway, Mike

---

### Post by reclusivemonkey on 2007-06-14
> **mdurham said:**
> reclusivemonkey , I did as you kindly suggested but the message that I see flash by at boot time does not appear in the dmesg output. I see a message something  about disk lable followed by quite a few lines of info about the fstab file but it goes so fast I'm unable to read it. **None **of this appears in the dmesg file.
Thanks for you help anyway, Mike

Try

```

grep -r fstab /var/log

```

---

### Post by RedSquirrel on 2007-06-14
There might be something in /var/log/fsck/checkfs or /var/log/fsck/checkroot.

---

### Post by mdurham on 2007-06-14
Thanks for all your help guys, I have found my problem. The last boot did an fsck full check on my root partition, thus stopping the scrolling for a while, enabling me to see what the message was. It was telling me that I had a LABEL= error in my fstab. I had > LABEL=Gutsy hda4 	/ ext3 rw,errors=remount-ro 0 1
instead of > LABEL=Gutsy_hda4 	/ ext3 rw,errors=remount-ro 0 1 missing the '_'. The amazing thing (to me anyway) is that it still used that partition for root. I wonder how that works?.
Anyway it's fixed now but I'd still like to know how to read those messages that scream up the screen.
Cheers, Mike

---

