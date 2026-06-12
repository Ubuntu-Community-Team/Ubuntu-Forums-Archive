---
title: "setcap does not know about CAP_PERFMON in 20.04 LTS"
date: 2021-07-04
forum: General Help
---

### Post by John Nagle on 2021-07-04
I wanted to run Rust's flamegraph to profile something. This requires that "flamegraph" be given the "CAP_PERFMON" capability.

Setting that capability with "setcap" doesn't work, because "setcap" doesn't recognize "CAP_PERFMON" as a valid capabiilty. It recognizes other capabilities, but not that one.

Reported bug: [https://bugs.launchpad.net/ubuntu/+bug/1934608](https://bugs.launchpad.net/ubuntu/+bug/1934608)
This was a known bug for CentOs/RedHat, and it's been fixed over there. Something was apparently built with the wrong library.

Is there a workaround for this on Ubuntu?

---

### Post by norobro on 2021-07-04
What kernel are you running? From man capabilities: > CAP_PERFMON (since Linux 5.8)
Works fine on 21.04.```
$ echo foo > foo
$ sudo setcap cap_perfmon+ep foo
$ sudo getcap foo
foo cap_perfmon=ep

$ uname -r
5.11.0-17-generic
```

---

### Post by John Nagle on 2021-07-07
20.04 LTS, as mentioned above.

 That's supported until 2025.

---

