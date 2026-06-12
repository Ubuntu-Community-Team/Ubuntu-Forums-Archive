---
title: "Can't boot after removing old kernels  vfs sync kernel panic with luks"
date: 2013-11-26
forum: General Help
---

### Post by sharkey77 on 2013-11-26
My boot partition was full and I followed this post.

[http://ubuntuforums.org/showthread.php?t=1435818](http://ubuntuforums.org/showthread.php?t=1435818)

```
dpkg --get-selections | \
  grep 'linux-image*' | \
  awk '{print $1}' | \
  egrep -v "linux-image-$(uname -r)|linux-image-generic" | \
  while read n
  do
    apt-get -y remove $n
  done
```

I am now getting kernel panic errors and of course can't go back to the old kernel since I deleted it.  :(

Using Kernel 3.8.0-33

I'm over my head as how to restore it.

Thanks for any help.

---

