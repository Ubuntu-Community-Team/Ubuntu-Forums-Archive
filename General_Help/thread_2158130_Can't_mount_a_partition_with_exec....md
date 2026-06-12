---
title: "Can't mount a partition with exec..."
date: 2013-06-27
forum: General Help
---

### Post by Horbo on 2013-06-27
I'm mounting a partition with this line in fstab:
```
UUID=ae38e823-a0b0-4b18-bc44-ef9411500e6f /storage        ext3    rw,suid,dev,exec,auto,user,async,noatime        0       2
```

but if I check my mounted file systems with "mount" I see this:
```
/dev/sda6 on /storage type ext3 (rw,noexec,nosuid,nodev,noatime)

```

??? What happened? I've set suid, dev,and exec but it's mounted without any of these!  I have no clue what's going on...

BTW, if you were wondering blkid confirms I have the correct UUID: ```
/dev/sda6: UUID="ae38e823-a0b0-4b18-bc44-ef9411500e6f" TYPE="ext3" 
```

---

### Post by steeldriver on 2013-06-27
No mount expert, but I think that would be because the *user* option is overriding the preceding *suid,dev,exec* options

```

      user   Allow an ordinary user to mount the filesystem.  The name of the mounting user is written to mtab so that he can unmount  the  filesystem  again.   [B]This  option
              implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line user,exec,dev,suid)[/B].

```

---

### Post by Horbo on 2013-06-27
Doh. Thanks steeldriver, I'm sure you're right.

Is there a way of marking theads as "solved" these days?  It isn't showing up under Thread Tools...

---

