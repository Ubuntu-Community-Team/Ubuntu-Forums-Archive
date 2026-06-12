---
title: "Swap file size is 0"
date: 2018-02-21
forum: General Help
---

### Post by raleigh3 on 2018-02-21
I made a swap file exactly as shown here.

[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F)

However, swap is showing 0?

```
andyk_~/Downloads$ free -h
              total        used        free      shared  buff/cache   available
Mem:           6.8G        659M        5.2G         29M        939M        5.8G
Swap:            0B          0B          0B
```

---

### Post by deadflowr on 2018-02-21
What does
```
swapon -s
```
show?

---

### Post by raleigh3 on 2018-02-21
Thanks.

It took a power off to show up. A reboot was not enough.

Swap:          1.0G          0B        1.0G


Filename                Type        Size    Used    Priority
/mnt/1GiB.swap                             file        1048572    0    -2

---

### Post by deadflowr on 2018-02-21
> It took a power off to show up. A reboot was not enough.


Now it shows?

[s]It's unclear what you mean.[/s]
nevermind, I think I understand you now.

---

