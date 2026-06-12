---
title: "mt-st, stinit and alternate tape devices not found on first use"
date: 2016-12-23
forum: General Help
---

### Post by David_Partridge on 2016-12-23
I installed mt-st on 16.04 LTS, and it appears to be working well, but part of the function isn't quite working.

The pseudo devices for differing compression etc are created:

```
amonra@Charon:~$ ll /dev/st0*
crw-rw---- 1 root tape 9,  0 Dec 23 10:56 /dev/st0
crw-rw---- 1 root tape 9, 96 Dec 23 10:56 /dev/st0a
crw-rw---- 1 root tape 9, 32 Dec 23 10:56 /dev/st0l
crw-rw---- 1 root tape 9, 64 Dec 23 10:56 /dev/st0m
amonra@Charon:~$ 
```

but immediately after connecting to the iSCSI tape and attempting to use st0l

```
amonra@Charon:~$ mt -f /dev/st0l erase
/dev/st0l: No such device or address
amonra@Charon:~$
```

but after issuing an erase command to the base device st0, I then got:

```
amonra@Charon:~$ mt -f /dev/st0l status
/dev/st0l: Device or resource busy
amonra@Charon:~$
```

is there anywhere I can report this problem and are there any work rounds other than using the base device before the st0l device?

Dave

---

### Post by David_Partridge on 2016-12-23
Running stinit manually seems to resolve the problem, but I can't see how the alternative device names could show up unless stinit had been auto-run?

Any thoughts?
Dave

---

