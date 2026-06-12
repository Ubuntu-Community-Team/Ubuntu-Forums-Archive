---
title: "NTP Question"
date: 2016-07-20
forum: General Help
---

### Post by scojopa on 2016-07-20
I am looking at my ntp server and not sure how some of these entries got in there. Two questions - what does the *,+,- mean next to those entries

and how doe I get rid of them - no need for them. and they are not listed in /etc/ntp.conf

I do use DHCP but they are not listed on my DHCP server

 0.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 1.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 2.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 3.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 ntp.ubuntu.com  .POOL.          16 p    -   64    0    0.000    0.000   0.000
*ntp-northameric 200.98.196.212   2 u   85  128  377    4.152   -4.670   1.894
+kahuna.ruselabs 199.102.46.70    2 u   76  128  377    4.145   -4.097   2.069
+98.234.173.215  216.218.192.202  2 u   88  128  377   79.547   -5.184   1.058
-mail.coldnortha 132.246.11.231   2 u   86  128  377    3.219   -5.618   0.825
-time.aja.com    198.169.208.144  2 u  204  256  377   74.262   -7.093   1.336

---

### Post by scojopa on 2016-07-20
For my first question the answer is


[LIST]
[*]<sp> discarded due to high stratum and/or failed sanity checks;
[*]"x" designated falsticker by the intersection algorithm;
[*]"." culled from the end of the candidate list;
[*]"-" discarded by the clustering algorithm;
[*]"+" included in the final selection set;
[*]"#" selected for synchronization but distance exceeds maximum;
[*]"*" selected for synchronization;
[*]"o" selected for synchronization, PPS signal in use.
[/LIST]

---

