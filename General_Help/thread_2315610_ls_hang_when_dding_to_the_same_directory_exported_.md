---
title: "ls hang when dding to the same directory exported by NFS"
date: 2016-03-01
forum: General Help
---

### Post by maorui on 2016-03-01
I mounted a NFS share exported by another Ubuntu box, and used dd to generate a 10GB file. When I tried to ls the target directory to see the file size, ls command returned after more than 20 seconds! But the dd performace is ok, more than 85MB/s. And if ls any other directory, parent or sub, it returned immediately.

I also tried NFS exported by Solaris & Windows, all got same result.

Could anyone tell me how to fix this issue?

---

### Post by maorui on 2016-03-02
More findings:
1. the ls would suspend IO of dd to get result back.
2. dd read and write same file, the dd read had same behaviour as ls command. It would suspend write IO to finish the read operation after several seconds.
3. dd read and write different files had no this issue.

So some kind of lock mechanism or an issue of cache?

iostat output in Solaris box:
   tty         p1          rpool          sd0           sd1            cpu
 tin tout kps tps serv  kps tps serv  kps tps serv  kps tps serv   us sy dt id
   0   42 120708 1852  107    0   0    0    0   0    0    0   0    0    0  4  0 96
   0  120 120712 1808  118    0   0    0    0   0    0    0   0    0    0  5  0 95
   0   42 120707 1797  115    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 120698 1698  118    0   0    0    0   0    0    0   0    0    0  5  0 95
   0   42 80650 1351   97    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   41 120702 1799  113    0   0    0    0   0    0    0   0    0    0  5  0 95
   0   42 121276 1920  117    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 120124 1680  116    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 120202 1705  114    0   0    0    0   0    0    0   0    0    0  5  0 95
   0   42 94643 1280  144    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 106176 1730   98    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 120703 1858  108    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 120702 1806  114    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 120683 1802  111    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 119823 1536  118    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 80547 1320   98    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   42 69103 935  123    0   0    0    0   0    0    0   0    0    0  2  0 98
   0   41   0   0    0    0   0    0    0   0    0    0   0    0    0  0  0 100 <====== read/ls operation got result back at this point
   0   41 45361 837  102    0   0    0    0   0    0    0   0    0    0  2  0 98
   tty         p1          rpool          sd0           sd1            cpu
 tin tout kps tps serv  kps tps serv  kps tps serv  kps tps serv   us sy dt id
   0   41 120125 1602  124    0   0    0    0   0    0    0   0    0    0  4  0 96
   0  120 80188 1223  111    0   0    0    0   0    0    0   0    0    0  4  0 96
   0   41 120190 1692  111    0   0    0    0   0    0    0   0    0    0  4  0 95

---

