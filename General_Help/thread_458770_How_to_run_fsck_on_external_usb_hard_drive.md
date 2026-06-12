---
title: "How to run fsck on external usb hard drive?"
date: 2007-05-30
forum: General Help
---

### Post by mdurham on 2007-05-30
Anyone have any ideas?
Cheers, Mike

---

### Post by smylie on 2007-05-30
should be able to run it the same as normal

```
 fsck /dev/sda1 
```

Just need to replace sda1 with the the actual device (use df, or mount with no args if you're not sure which it is)

You'll probably want to make sure it's not mounted as well.

---

### Post by mdurham on 2007-05-30
> **smylie said:**
> should be able to run it the same as normal

```
 fsck /dev/sda1 
```

Just need to replace sda1 with the the actual device (use df, or mount with no args if you're not sure which it is)

You'll probably want to make sure it's not mounted as well.

Thanks smylie, but it doesn't seem to do any checking it just reports 
> ~$ sudo fsck -V -a /dev/sdb6
fsck 1.40-WIP (14-Nov-2006)
[/sbin/fsck.ext3 (1) -- /dev/sdb6] fsck.ext3 -a /dev/sdb6 
EXT_EXT3BKUP: clean, 1938114/6786080 files, 11666005/13566884 blocks How can I force a check?
Cheers, Mike

---

### Post by mozetti on 2007-05-30
Use the -f switch.

Also, just type **man fsck** or **man e2fsck**, etc to see all the switches/options.

---

### Post by mdurham on 2007-05-30
> **mozetti said:**
> Use the -f switch.

Also, just type **man fsck** or **man e2fsck**, etc to see all the switches/options.

Thanks I'll try the -f switch but I didn't see it in "man fsck", why is that?

---

### Post by mozetti on 2007-05-30
I'm at work, so I can't check it, but I think it was in there. You might also want to check the "See also" section, because AFAIK, fsck just invokes the apprpriate file-checking tool (e2fsck, dosfsck, etc). So, that could be why it wasn't listed -- but I know for sure that the e2fsck man page shows the -f switch.

Also, I found this site that lists [Linux Man Pages](http://www.linuxmanpages.com/)

---

### Post by mdurham on 2007-05-30
Thanks mozetti, it worked fine.
Cheers, Mike

---

