---
title: "[SOLVED] Trying to mount ext3 partition as rw need help"
date: 2007-06-29
forum: General Help
---

### Post by cjax1 on 2007-06-29
I know this has probably been asked before but once again I can not find an answer. I have found several pages on fstab. These are just two of them.

[http://www.bellevuelinux.org/etc_fstab.html]("http://www.bellevuelinux.org/etc_fstab.html")

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")


I've tried editing fstab by replacing 'defaults' with several options. Here's the line I'm refering to in fstab.

/dev/hda3      /media/hda3     ext3     defaults     0     2

That's how it is now like it was before. It's mounted a boot but read only.

If I open nautilus as root I can write to it. I learned that 'defaults' is supposed to mount it as rw but in reality it doesn't. I've tried changing that line several ways.

The command

```
mount -l
```

says it is mounted as rw.

I just want to be able to read and write to it as I please without having to become root.

Oh yeah, would chmod 777 work for this? If so exactly how would I type it?

Thanks

---

### Post by merlinus on 2007-06-29
Try this:

```

sudo chown -R username:username /media/hda3

```

username is your login id.

-merlin

---

### Post by cjax1 on 2007-06-29
WOW. That seemed to work. Thanks a bunch merlinus. I don't know too much about chown but I think that gave the owner, me, rw permission but no one else right? I mean that's fine, that's what I want but that's how I understand it.

I'm always learning something new.

Thanks again

---

