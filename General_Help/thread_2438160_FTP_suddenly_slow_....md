---
title: "FTP suddenly slow ..."
date: 2020-03-06
forum: General Help
---

### Post by michael351 on 2020-03-06
I have FileZilla installed on two ubuntu machines on the same LAN. Normally  when I ftp files between them, I easily get 100 MiB/second speeds for 10  concurrent sessions. (about 80% of my gigabit LAN).

Today, for some reason, I am only getting 10 MiB/second speeds - only  10% of the speed I use to have. Any thoughts on what may be going on? I  don't understand the slow down. Both computers are quiet (not active for the  moment) with only FTP operating to move files over (media).

Any suggestions?

---

### Post by HermanAB on 2020-03-07
Run *top* and *ntop* to see what is going on in your system.

---

### Post by michael351 on 2020-03-08
Found the problem .... 

The NIC was locked at 100 MB/sec for some reason.
I used ethtool to set the speed at maximum (1000) with auto-negotiation set to "on" for both NIC cards and that did the trick.
Immediately my background ftp transfer speed jumped ten fold from 10 MB/sec (ten transfers at a time) to well over 100 MB/sec. Big difference.

---

