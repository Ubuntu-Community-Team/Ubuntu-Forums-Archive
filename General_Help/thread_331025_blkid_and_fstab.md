---
title: "blkid and fstab"
date: 2007-01-04
forum: General Help
---

### Post by seelk on 2007-01-04
Can someone help me write a script (preferrably in bash) that would insert blkid UUID's in /etc/fstab?

Below are my current UUID's:
```
$ blkid -s UUID
/dev/sdb1: UUID="1FBA-DCD5" 
/dev/sdb2: UUID="78263028-4654-409e-9d88-7ab4ec4edde0" 
/dev/sdb5: UUID="d5d58b68-361d-4c9d-ae1d-8bfb29722cbc"
```

I would like the UUID's to be inserted into the appropriate partition in /etc/fstab.

Below is a line from /etc/fstab that needs to be updated (yes they're the same UUID's, it's just an example):
```
/dev/sdb5 UUID=d5d58b68-361d-4c9d-ae1d-8bfb29722cbc none            swap    sw              0       0
```

---

### Post by kidders on 2007-01-04
Hi there,

I'd be happy to help, but I'm a little confused about why you're using both "/dev/sdb5" and "UUID=d5d58b68-361d-4c9d-ae1d-8bfb29722cbc" in /etc/fstab. I don't see the need/advantage.

---

### Post by seelk on 2007-01-04
> **kidders said:**
> Hi there,

I'd be happy to help, but I'm a little confused about why you're using both "/dev/sdb5" and "UUID=d5d58b68-361d-4c9d-ae1d-8bfb29722cbc" in /etc/fstab. I don't see the need/advantage.

Honestly, I don't know what the advantage is to have UUID's in /etc/fstab.  I know fstab had UUID's when I installed Edgy so I thought this is something needed.  Plus I see it as a good learning practice to be able to automatically modify files through scripts and such.  Thanks for your help.

---

### Post by bodhi.zazen on 2007-01-04
You can check out this link:

[http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

---

### Post by fragos on 2007-01-04
UUIDs are a mixed blesssing.  I've been running Edgy with a couple of extra partitions which I mounted as /Share and /Other.  I wanted to try another distro BFX and installed it in my /Other partition aka /media/hda3.  BFX worked fine but when I tried to boot into Ubuntu it wouldn't start X because it didn't like the ext3 format done when BFX was installed.  I managed to get Ubuntu up but it wouldn't automaticaly mount /Share or /Other anymore.  The only way I could get things back to normal was to delete in gparted and then reformat as ext3.  Interesting that the UUID for /dev/hda3 no longer exits but everything mounts automatically.  I haven't tried to reinstall BFX so I don't know if deleteing the UUID for that partition will allow things to function normally again.  BFX is a shrunk down Ubuntu distribution with a 2.6.10 kernel so I would have thought it would be compatible.

---

### Post by bodhi.zazen on 2007-01-04
> **fragos said:**
> UUIDs are a mixed blesssing.  I've been running Edgy with a couple of extra partitions which I mounted as /Share and /Other.  I wanted to try another distro BFX and installed it in my /Other partition aka /media/hda3.  BFX worked fine but when I tried to boot into Ubuntu it wouldn't start X because it didn't like the ext3 format done when BFX was installed.  I managed to get Ubuntu up but it wouldn't automaticaly mount /Share or /Other anymore.  The only way I could get things back to normal was to delete in gparted and then reformat as ext3.  Interesting that the UUID for /dev/hda3 no longer exits but everything mounts automatically.  I haven't tried to reinstall BFX so I don't know if deleteing the UUID for that partition will allow things to function normally again.  BFX is a shrunk down Ubuntu distribution with a 2.6.10 kernel so I would have thought it would be compatible.

LOL fragos :lol:

I'll tell you a secret :-$

You can edit fstab and use /dev/hdxy rather then UUID in Edgy and Feisty. This is helpful if you re-format a partition (frequently) which changes it's UUID. :8-[

HTH

---

