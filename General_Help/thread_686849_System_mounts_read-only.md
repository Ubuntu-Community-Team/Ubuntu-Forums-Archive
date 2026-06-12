---
title: "System mounts read-only"
date: 2008-02-03
forum: General Help
---

### Post by dwabraxus on 2008-02-03
First off...
I am not a beginner linux person. I have a lot of experiance with init, but not much with upstart...

I have Ubuntu Gutsy install on a computer with Mythtv, mysql-server, php, apache2,ivtv drivers, nvidia drivers(not 'nv', but 'nvidia'), and webmin. Other than that it is a base install. It its my PVR. So about a week ago, it started mounting the root FS as read-only.

Huge issue. 

Many services can't start on boot anymore. There were no changes to any configs and fsck returns no issues with any drives. If I remount the drive and restart all runlevel 2 inits then it works fine. Im fairly sure it is booting runlevel 2. Of course, GDM won't load because it is RO but it works fine one I remount as RW and run it.

Please help... Im sure it is just a simple issue but I can't figure out what it is.

dmesg does not show any issues on boot.

Thanks in advance...

---

### Post by geraldm on 2008-02-03
Fairly sure of runlevel is not certain enough.  Use
man runlevel
```

runlevel

```

Gerald

---

