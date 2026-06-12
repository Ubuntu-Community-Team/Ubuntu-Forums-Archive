---
title: "understand kern.log"
date: 2013-09-28
forum: General Help
---

### Post by swapnil-indore on 2013-09-28
Hi,


kern.log there are 5 different fields

Sep 28 12:02:07 ubuntu kernel: [1282809.716539] some message

1) Date time (Sep 28 12:02:07)
2) hostname (ubuntu)
3) kernel: its says its a kernel log (kernel:)
4) some number [1282809.716539]
5) actual log message []


I need to understand more about the 4th, [1282809.716539], what is this ?

---

### Post by Gyokuro on 2013-09-28
The  4th is a time stamp and the time mentioned in kern.log is in seconds since kernel startup. For this reason dmesg have an additional switch -T which show you the time stamp in human readable form. -HTH

---

