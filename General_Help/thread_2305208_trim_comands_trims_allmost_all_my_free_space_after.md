---
title: "trim comands trims allmost all my free space after reboot"
date: 2015-12-03
forum: General Help
---

### Post by korakios on 2015-12-03
Hi,
I apologise of I am wrong, but after switching to kubuntu 15.10 I have a weird trim behaviour.
In 14.04 I used to manually trim my samsung evo ssd giving 
sudo fstrim -v /
sudo fstrim -v /home

now I notice that every time I manually trim the output is
```
 sudo fstrim -v /
/: 25,2 GiB (27043823616 bytes) trimmed

 sudo fstrim -v /home
/home: 70,2 GiB (75359084544 bytes) trimmed
```

Normally I had some gigabytes trimmed after heavy usage of installing,updating, deleting.Not the partition free space...
```
uname -a
  4.2.0-19-lowlatency #23-Ubuntu SMP PREEMPT Wed Nov 11 12:26:51 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

Any advise what to check?

---

