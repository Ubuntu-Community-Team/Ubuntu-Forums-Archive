---
title: "How can I measure/test performance of different swap configurations?"
date: 2013-12-14
forum: General Help
---

### Post by NTL2009 on 2013-12-14
I've been experimenting with different swap configurations to try to improve swap performance on my machine (a bit more in this [thread]("http://ubuntuforums.org/showthread.php?t=2192415")). Basically, my machine is limited to 3GB RAM, I rarely re-boot, and my Chromium browser activity ends up using up memory after a few days and starts to swap in/out, slowing things down.

So even though SDCards and USB thumb drives are slower than the HDD, it _seems to have helped responsiveness_ to add these with the same priority as the HDD. This gives me three devices running in parallel on different buses. 

But I'm looking for some more objective measurement - **anyone know of a tool that could tell me how fast the actual swap process is?** It's doing a 'round-robin' read/write from each of the devices, but I don't know how efficiently it parallels these tasks. I'd like to try different configs to evaluate. I'm considering adding a hub and filling it with cheap 1GB USB sticks, I think 4 in parallel won't exceed the bus speed. I'm aware of potential wear out problems, but I'll take my chances with some cheap memory cards/sticks until I re-purpose this machine for less memory intensive tasks, probably next year. And partially I want to do this just out of geeky curiosity. Can anyone relate? ;)

For reference, here's my swap config (I'm also running zram):

fstab

```
UUID=c8e94d8b-26dd-4eca-b81a-3bd8eabc8242 none swap defaults,pri=4 0 0
UUID=ff3bca9f-3e22-498e-9e89-18935afa6c34 none swap defaults,pri=4 0 0
UUID=c7abcd37-a043-447e-8a1d-138a9752ec53 none swap defaults,pri=4 0 0




```

```

~$ cat /proc/swapsFilename                
Type        Size    Used    Priority
/dev/sda3                               partition    5119996    202604    4
/dev/sdc1                               partition    3944444    204060    4
/dev/sdb1                               partition    3868156    203532    4
/dev/zram0                              partition    756872    750848    5
/dev/zram1                              partition    756872    750764    5

```

TIA -NTL2009

---

### Post by mikelavekkia on 2013-12-14
install zram-config this create 4 fake swap fs ...this fs is compress block of ram this optimize performance of ram and in moment you go to swapping not freeze because swaping is perform on rcompressed ram...this drain little bit consuption of processor resorse for uncrompress ram
edit: sorry i see you use zram already
you can add kernel lin "zswap.enabled=1 zcache" argument (onlu in the last kernel)

---

