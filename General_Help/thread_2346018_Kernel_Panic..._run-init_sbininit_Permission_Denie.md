---
title: "Kernel Panic... run-init: /sbin/init: Permission Denied"
date: 2016-12-10
forum: General Help
---

### Post by Imperium Guard on 2016-12-10
This morning I attempted to boot up Ubuntu 16.04 LTS and the following occurred:

```

Begin: Running /scripts/local-bottom ... done.
Begin: Running /scripts/init-bottom ... done.
run-init: /sbin/init: Permission denied
[    3.488774] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000100
[    3.488774]
[    3.491354] CPU: 0 PID: 1 Comm: run-init Tainted: P                 OE    4.4.0-53-generic #74-Ubuntu
[    3.492616] Hardware name: Hewlett-Packard 500-017c/2AE0, BIOS 80.52 11/11/2014
[    3.493875]  0000000000000086 000000003a75e7b0 ffff880235213e38 ffffffff813f5fc3
[    3.495144]  ffffffff81cb5c50 ffff880235213ed0 ffff880235213ec0 ffffffff8118c707
[    3.496421]  ffff880200000010 ffff880235213ed0 ffff880235213e68 000000003a75e7b0
[    3.497694] Call Trace:
[    3.498960]  [<ffffffff813f5fc3>] dump_stack+0x63/0x90
[    3.500224]  [<ffffffff8118c707>] panic+0xd3/0x215
[    3.501478]  [<ffffffff811855ae>] ? perf_event_exit_task+0xbe/0x350
[    3.502732]  [<ffffffff81084701>] do_exit+0xaf1/0xb00
[    3.503975]  [<ffffffff81084747>] SyS_exit+0x17/0x20
[    3.505212]  [<ffffffff81836072>] entry_SYSCALL_64_fastpath+0x16/0x71
[    3.506510] Kernel Offset: disabled
[    3.507790] ---[ end Kernel panic - not syncing: Attempted to kill init! exitcode 0x00000100
[    3.507790]
_

```

I was able to boot yesterday and updated through Software Updater before I shutdown. I'm fairly new to Ubuntu and thought it was a problem with permissions. I booted from a LiveCD and through a terminal tried:
```

sudo mount /dev/sda7 /mnt
sudo chmod 755 /mnt/sbin/init

```

But to no avail, the problem still persists. Any ideas?

Thanks

---

### Post by #&amp;thj^% on 2016-12-10
Ouch that looks nasty! - Basic question first have you tried booting to a older kernel?
This looks to be related to a resume Bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1615333](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1615333)
With the Intel processors "CState""

You might get somewhere with using that boot disc and then executing "chmod u+x /usr/bin" and the same for "/bin" .
This is just a stab in the dark though.

---

### Post by Imperium Guard on 2016-12-10
I have an AMD processor and I'm not really sure if this issue has anything to do with a resume bug. Most of the executables in /bin and /usr/bin already had the "x" modifier. I tried executing the command anyway but it didn't have an effect. 

Output of ls -l /mnt/sbin/init:
```
lrwxrwxrwx 1 root root 20 Dec 10 15:33 /mnt/sbin/init -> /lib/systemd/systemd
```
...of ls -l /mnt/lib/systemd/systemd/
```
-rwxr-xr-x 1 root root 1577232 Oct 26 13:05 /mnt/lib/systemd/systemd
```

---

### Post by #&amp;thj^% on 2016-12-10
Ok I would not have known you had AMD no mention of that here.
I did mention that was a Stab in the Dark though.
And I assume you have tried booting from and older kernel form grub.
Just trying to help.
That is just a Flat Nasty error though "[COLOR=#000000][FONT=&amp]Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000100[/FONT][/COLOR]"

---

