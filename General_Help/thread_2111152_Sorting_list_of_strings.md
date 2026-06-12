---
title: "Sorting list of strings"
date: 2013-02-01
forum: General Help
---

### Post by CrewDK on 2013-02-01
I'm sorting list of strings in file with [B]sort -h {filename}
[/B]
When i'm sorting list of ip's in file like (only IP's)

```

46.61.52.18
92.124.61.71
109.165.5.78
176.117.132.8
37.148.182.70
5.199.175.63
77.247.234.32
31.23.112.42
70.168.55.29
77.43.254.180
46.61.10.32
109.205.252.105
178.77.66.228
62.193.232.12
91.124.99.246
195.177.121.105
178.201.47.216
94.23.84.217

```it's sorting like 

```
1.234.31.20
1.234.70.62
5.135.71.12
5.139.117.116
5.199.175.63
5.9.20.186
31.23.110.155
31.23.112.42
31.23.126.15
31.23.21.252
31.23.232.226
31.23.4.145
37.148.182.70
e.t.c.

```But if i'm sorting list like (IP's + commands for iptables)

```
-A BAN -s 217.118.78.99/32 -j DROP
-A BAN -s 31.23.110.155/32 -j DROP
-A BAN -s 31.23.112.42/32 -j DROP
-A BAN -s 106.186.16.164/32 -j DROP
-A BAN -s 80.93.126.10/32 -j DROP
-A BAN -s 82.140.132.137/32 -j DROP
-A BAN -s 82.192.90.142/32 -j DROP
-A BAN -s 188.138.88.171/32 -j DROP
-A BAN -s 188.40.68.138/32 -j DROP
-A BAN -s 195.177.121.105/32 -j DROP
-A BAN -s 198.101.242.243/32 -j DROP
-A BAN -s 210.209.121.203/32 -j DROP
-A BAN -s 213.239.202.112/32 -j DROP
-A BAN -s 217.118.78.104/32 -j DROP
e.t.c.

```it's sorting like

```
-A BAN -s 106.186.16.164/32 -j DROP
-A BAN -s 109.165.5.78/32 -j DROP
-A BAN -s 109.165.83.196/32 -j DROP
-A BAN -s 109.205.249.168/32 -j DROP
-A BAN -s 109.205.249.171/32 -j DROP
-A BAN -s 109.205.252.105/32 -j DROP
-A BAN -s 109.205.252.41/32 -j DROP
-A BAN -s 1.234.31.20/32 -j DROP
-A BAN -s 1.234.70.62/32 -j DROP
-A BAN -s 150.214.188.47/32 -j DROP
-A BAN -s 176.117.132.8/32 -j DROP
-A BAN -s 178.184.37.8/32 -j DROP
-A BAN -s 178.201.47.216/32 -j DROP
```I mean that in the first case, after sorting IP are in ascending order - first one, then dozens, then hundreds. In the second case, they are sorted by the first digit of the IP.

I clearly explained? Why it's happens and how i can sort both list with same result?

---

### Post by steeldriver on 2013-02-01
try it with the sort 'keyed' on only the IP column

```
$ sort -h **-k4,4** bans
-A BAN -s 31.23.110.155/32 -j DROP
-A BAN -s 31.23.112.42/32 -j DROP
-A BAN -s 80.93.126.10/32 -j DROP
-A BAN -s 82.140.132.137/32 -j DROP
-A BAN -s 82.192.90.142/32 -j DROP
-A BAN -s 106.186.16.164/32 -j DROP
-A BAN -s 188.138.88.171/32 -j DROP
-A BAN -s 188.40.68.138/32 -j DROP
-A BAN -s 195.177.121.105/32 -j DROP
-A BAN -s 198.101.242.243/32 -j DROP
-A BAN -s 210.209.121.203/32 -j DROP
-A BAN -s 213.239.202.112/32 -j DROP
-A BAN -s 217.118.78.104/32 -j DROP
-A BAN -s 217.118.78.99/32 -j DROP

```

---

