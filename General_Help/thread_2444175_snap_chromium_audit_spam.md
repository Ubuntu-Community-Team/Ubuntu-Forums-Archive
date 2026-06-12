---
title: "snap chromium audit spam"
date: 2020-05-26
forum: General Help
---

### Post by PatrickMay16 on 2020-05-26
chromium floods 'dmesg' with stuff like this:

```
[ 1029.375585] audit: type=1326 audit(1590490257.530:645): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1029.375798] audit: type=1326 audit(1590490257.530:646): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1033.488451] audit: type=1326 audit(1590490261.642:647): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1033.488562] audit: type=1326 audit(1590490261.642:648): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1034.505417] audit: type=1326 audit(1590490262.662:649): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1034.505498] audit: type=1326 audit(1590490262.662:650): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1037.888456] audit: type=1326 audit(1590490266.042:651): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1037.888584] audit: type=1326 audit(1590490266.042:652): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1051.971840] audit: type=1326 audit(1590490280.126:653): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1051.971945] audit: type=1326 audit(1590490280.126:654): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1068.505760] audit: type=1326 audit(1590490296.662:655): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1068.505892] audit: type=1326 audit(1590490296.662:656): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1073.088808] audit: type=1326 audit(1590490301.241:657): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1073.088922] audit: type=1326 audit(1590490301.241:658): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1087.172397] audit: type=1326 audit(1590490315.325:659): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1087.172551] audit: type=1326 audit(1590490315.325:660): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1102.139133] audit: type=1326 audit(1590490330.293:661): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1102.139478] audit: type=1326 audit(1590490330.293:662): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1116.206488] audit: type=1326 audit(1590490344.361:663): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1116.206581] audit: type=1326 audit(1590490344.361:664): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1131.172720] audit: type=1326 audit(1590490359.325:665): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000
[ 1131.172877] audit: type=1326 audit(1590490359.325:666): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4998 comm="chrome" exe="/snap/chromium/1165/usr/lib/chromium-browser/chrome" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7febc9972b8f code=0x50000

```

It's making it harder to diagnose hardware problems I'm having because it's buried under all these audit messages. How do you disable this?

---

### Post by TheFu on 2020-05-26
Looks to be snap related. Contact the snap package maintainer.
Or
don't use the snap version.  Yesterday, I ran the chromium app included in the snap package, but without the overheard from the snap.  I still wish for the program to be constrained, just need for those constraints to be under my control since snaps don't seem to support NFS mounted data or HOMEs.

The command to run that worked for me was:
```
 /snap/chromium/current/usr/lib/chromium-browser/chrome &
```

---

