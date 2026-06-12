---
title: "Bcache tuning seems to be impossible because /sys echo &gt; whatever is denied"
date: 2020-11-01
forum: General Help
---

### Post by pksings2 on 2020-11-01
I have an NVME drive cacheing two spinning disks, I noticed that it seems to be slower than it was. Turns out that my script file that tunes bcache during boot is being denied the ability to write to the configuration files like it used to.
So I tried them all from the command line, same result, denied, cannot write to these files anymore.  I used to change some parameters, like read_ahead and congestion tuning by using the echo > technique to change the settings, which really helped performance, and now it doesn't work, cannot write to the files.

Is there a different procedure to tune bcache on-the-fly now?

Thanks in advance.

Paul Kelly

---

### Post by CatKiller on 2020-11-01
What command were you trying to run?

---

### Post by pksings2 on 2020-11-01
echo 50M > /sys/fs/bcache/f5ea8db3-eedc-4ff4-bbd4-15be90a13719/cache0/set/stats_total/cache_readaheads

This was the prescribed method of changing bcache settings on the fly. I wrote a script to do this during boot which has stopped working as it cannot write to these files anymore.

---

### Post by HermanAB on 2020-11-01
Are you sure that "/sys/fs/bcache/f5ea8db3-eedc-4ff4-bbd4-15be90a13719/cache0/set/stats_total/cache_readaheads" exists???

---

