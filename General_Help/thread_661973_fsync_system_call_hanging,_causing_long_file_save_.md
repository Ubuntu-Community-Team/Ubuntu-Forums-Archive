---
title: "fsync system call hanging, causing long file save times"
date: 2008-01-08
forum: General Help
---

### Post by gnychis on 2008-01-08
Hi all,

All of a sudden I've noticed my file save times in VIM and EMACS are taking on the order of 3+ seconds for even just a single byte, which is extremely frustrating.

I used strace to narrow it down to an fsync call taking longer than 3 seconds:
```

  15171      0.000094 fsync(6)            = 0 <3.386504> 

```

Does anyone know what might be causing this?  It is not the hard disk spindown issue as I'm on a desktop and I checked the cycles anyways:
```

193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0

```

So, fsync does not appear to be hanging while waiting for the disk to spin up.

Some system info:
```

  Ubuntu Gutsy Gibbon desktop machine, updated as of time of post
  Linux 2.6.22-14-generic #1 SMP i686 GNU/Linux, running reiserFS. 

```

I would greatly appreciate any help, thanks!

- George

---

### Post by gnychis on 2008-01-08
solved, lpd was causing the hang

---

