---
title: "System disk is booting very slowly"
date: 2021-01-14
forum: General Help
---

### Post by jazahalka on 2021-01-14
I recently looked at `systemd-analyze blame` and saw, that some service called `dev-nvme0n1p3.device` boots for 12.206 seconds, so I ran the same command on my second laptop, where similar service lasted only for about half a second. Both laptops have SSD disks, so what makes this big difference and how should I make my laptop boot faster? Another interesting information is, that when I ran benchmark on my primary laptop on that "slow" drive, it shows that it has speed 1,4 GB per second, but my second "speeder" laptop, it shows only 520 MB per second. 

`/dev/nvme01p3` is my system partition (mounted as filesystem root) formatted as Ext4 and is 25 GB large and I have ubuntu 20.10 Groovy installed, if that makes some difference.

Thank you very much for your suggestions and please say everything simply, I am such a nooby user. I have Ubuntu 20.10 Groovy installed.

---

### Post by TheFu on 2021-01-16
"Nooby" users shouldn't touch drive performance things without the appropriate background. You can easily end up with a system that won't boot. The issues could be all sorts of things from old firmware, bad BIOS, incorrectly setup EFI, or other devices being found first.  

What background do you need? Basic Unix commands, understanding about different disk types, different bus architectures, different storage architectures, how Linux boots (there are probably 5 different ways), partitioning, file systems, parallel boot processing via systemd, etc.

So with less optimal EFI settings, the OS could have to search and validate connections to the nvme0n[?] device(s) at every boot.

Hint: when asking for help, please show *relevant* the output from commands and limit the interpretations.

I've never understood why people obsess about boot times. It isn't like you are rebooting all the time, is it?
```
$ uptime 
 14:29:55 **up 7 days**,  2:38,  5 users,  load average: 11.45, 12.40, 11.11
```
Say I boot every week, does 1 extra minute to validate the hardware really impact me?  When I reboot, I'll just go and get a cup of tea.
On a fast 6core Ryzen with SSD and 1 HDD:
```
$ systemd-analyze 
Startup finished in 8.046s (kernel) + 1min 30.301s (userspace) = 1min 38.348s
```

On a 5 yr old 2 core Pentium with 32TB+ storage, no SSD:
```
$ systemd-analyze 
Startup finished in 14.024s (kernel) + 43.467s (userspace) = 57.492s

```

On a 1 vCPU VM on the Ryzen:
```
$ systemd-analyze 
Startup finished in 2.666s (kernel) + 6.425s (userspace) = 9.091s
```

Clearly, I should always use virtual machines with 1 core assigned, if fast booting is the goal, right?

On a 2017 Core i5 laptop with a SATA SSD:
```
$ systemd-analyze
Startup finished in 3.782s (firmware) + 5.184s (loader) + 3min 13.250s (kernel) + 48.402s (userspace) = 4min 10.620s
```
4 minutes??!  No way!  Well, it isn't 4 minutes to boot.  systemd-analyze lies. Guess that's the real thing to learn here.

From the manpage:
```
       systemd-analyze blame prints a list of all running units, ordered by the
       time they took to initialize. This information may be used to optimize
       boot-up times. [B]Note that the output might be misleading as the
       initialization of one service might be slow simply because it waits for
       the initialization of another service to complete[/B].
```

---

### Post by grahammechanical on 2021-01-16
I do believe that Ubuntu developers try to reduce the boot time by letting us log in before all services are fully running. In other words, there is still a lot of activity taking place even after we log in. As I understand things, systemd is the start up service. A difference in the number of CPU cores and amount memory might cause differences in times between two machines and not just the storage discs.

Regards

---

