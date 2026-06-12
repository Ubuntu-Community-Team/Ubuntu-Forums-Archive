---
title: "openssl processes hang at 100% cpu usage"
date: 2012-11-22
forum: General Help
---

### Post by koenc86 on 2012-11-22
Hallo all,

The last few days I wake up noticing that my Ubuntu 12.10 server is running very hot due to one or more openssl processes running at 100% cpu usage for hours. I just copied this out of 'top' from the last occurrence:

> 7352 root      20   0 23936 2840 2224 R 100.4  0.0 123:11.20 openssl
3436 root      20   0 23936 2836 2224 R  99.7  0.0 171:51.32 openssl

When I kill these processes, things go back to normal. Obviously I would like to find out what is causing openssl to run at 100% cpu usage and how to prevent this in the future.
There are no messages in syslog indicating that they are related to this problem.

Is there anyone who can help me debug this issue?

Thank you very much in advance!

---

