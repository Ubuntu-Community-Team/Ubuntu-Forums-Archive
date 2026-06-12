---
title: "Hyper Threading - wont enable"
date: 2008-05-09
forum: General Help
---

### Post by FireCall on 2008-05-09
Hey, 

I have a brand spanking new install of 8.04 on a P4 2.8 box. 

For some reason HT wont turn on. The result of **uname -a** is:

```
2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
```

and I've edited this line to read:
```

kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=7b41f149-b250-48bd-8a86-7c752963de4d ro quiet splash ht=on
```


But I'm not seeing two CPUs in the System Monitor, so I'm guessing HT isnt on?

any help is much appreciated :)

---

### Post by ryanhaigh on 2008-05-09
What do you get as the output of 
```

cat /proc/cpuinfo 
``` or ```

cat /proc/cpuinfo  | grep processor
``` for a more concise output.

---

