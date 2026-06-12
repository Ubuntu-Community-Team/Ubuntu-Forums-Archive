---
title: "Target Sources (main/source/Sources) is configured multiple times in /etc/apt/source"
date: 2020-07-31
forum: General Help
---

### Post by Ed_B on 2020-07-31
Hi, I have upgraded my ubuntu from 16.04 to 20.04, and I am getting numerous problems, here is one.

```
 apt update
```
gives,
```

Fetched 33,0 MB in 16s (2&#8239;071 kB/s)                                            

(appstreamcli:21157): GLib-CRITICAL **: 16:54:48.079: g_atomic_ref_count_dec: assertion 'g_atomic_int_get (arc) > 0' failed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
10 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:17
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:17


```

But the line 6 and 17 of /etc/apt/sources.list look like
```

deb-src http://cz.archive.ubuntu.com/ubuntu/ focal main restricted
...
deb-src http://cz.archive.ubuntu.com/ubuntu/ focal main  universe

```

That is, one is for restricted packages and the other for universe.  Of course, I can get rid of the warning by commenting out one of the two lines, but
then I won't have access to one family of packages, right?  So how do I fix this?

---

### Post by ActionParsnip on 2020-07-31
What is the output of:
```

cat -n /etc/apt/sources.list

```

Thanks

---

### Post by deadflowr on 2020-07-31
> But the line 6 and 17 of /etc/apt/sources.list look like
```
deb-src http://cz.archive.ubuntu.com/ubuntu/ focal main restricted
...
deb-src http://cz.archive.ubuntu.com/ubuntu/ focal main  universe
```
That is, one is for restricted packages and the other for universe. Of course, I can get rid of the warning by commenting out one of the two lines, but
then I won't have access to one family of packages, right? So how do I fix this?

Look closer.
you have two entries for main...

---

