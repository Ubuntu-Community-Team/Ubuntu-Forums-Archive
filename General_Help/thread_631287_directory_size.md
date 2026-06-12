---
title: "directory size"
date: 2007-12-04
forum: General Help
---

### Post by bradleyd on 2007-12-04
Hello everyone,
I am having some discrepancies in the size of a directory. The directory is a mail directory with a lot of sub directory's. du, ls, stat all return different results. For example:
```
du -h /maill/00038/22038  
``` 
This returns the value of  17M

```
ls -alh /mail/00038/22038 | awk '{ SUM += $5} END { print SUM/1024/1024 }'

``` 
This returns the value 854322

```
stat --format=%s /mail/00038/22038/
```
This returns this value 10485760

The whole reason is that the mta will stop delivering mail to directory's over 10M. I am trying to search for those directory's. Anyone know why all the different results in the size output?
Thanks for your time,
Brad

---

### Post by pointone on 2007-12-04
du reports actual disk usage by number of clusters, and ext3 defaults to 4096 byte (4 KB) clusters. You can only put one file in any single cluster, although a file can span multiple clusters. If your mail directory contains a lot of small files (which it likely does) then the size reported by du will be larger than the actual number of bytes of information contained in those files (what ls returns).

For example, if I have a file that only contains 200 bytes of data, it will still use an entire cluster. ls -l will show 200, du will show 4096.

If another file contains 4097 bytes of data, it will use two clusters; the first 4096 bytes in one, the last byte in the second. ls -l will show 4097, du will show 8192.

I don't know about stat, but I'm sure it's somewhat related to this issue.

---

### Post by metalheart on 2007-12-04
You can use Baobab to get graphical view of directory sizes. Run baobab from the command prompt or select Disc Usage Analyzer from Application->Tools menu. Select directory to analyze.

---

### Post by bradleyd on 2007-12-04
thanks for the responses. So basically one of those mail dirs will have a space of 10M(via stat), but the actual files inside of the dir equal less than 10M. These directory's are kept on a net-app filer that is mounted via nfs, and the filer has a 10M directory cap. So even though the dir may only have 3M of stuff, but the filer reports the size of the dir much larger. It is like it never re indexes or something?
thanks,
brad

---

