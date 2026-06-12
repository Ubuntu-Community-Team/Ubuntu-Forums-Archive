---
title: "Ubuntu Server 7.04 suddenly hanging on boot up"
date: 2007-09-25
forum: General Help
---

### Post by hebetude on 2007-09-25
I decided to give my server a break (finally) so I turned it off for a weekend.  When I turned it on the following monday, it won't start.  I put a head back on it (been running all from ssh previously), and it appears to be hanging while mounting local filesystems.  Here's the last message it puts out...

```
* Mounting local filesystems...
[mntent]: warning: no final newline at the end of /etc/fstab
```

I can't be absolutely positive, but I don't believe I changed ANY software since the last time I rebooted the machine.

p.s. Don't tell me I have a bad hard drive, I'll cry irl

---

### Post by hebetude on 2007-09-26
So far, I've managed to ctrl-alt-del at some point when the fstab is being processed.  This allowed me to boot the system, it turns out mount is hanging while trying to mount one of my SECONDARY hard drives.

Really shitty linux, really shitty of you.  Shouldn't it be protected from problems like this?  I couldn't even boot into rescue mode without it hanging on the mounting procedures

---

### Post by hebetude on 2007-09-27
after 6hrs or so of reiserfsck doing different scans on the hdd, it said I should go buy a new one b/c this one is fubar.  So if any hdd ever goes bad (as if that never happened before) ubuntu doesn't boot.

Good luck folks

---

