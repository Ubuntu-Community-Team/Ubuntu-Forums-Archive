---
title: "/etc/crypttab entry isn't processed at boot time"
date: 2017-09-20
forum: General Help
---

### Post by temmokan on 2017-09-20
Ubuntu 16.04.3, 64-bit, all latest updates applied.

Problem: /etc/crypttab entry isn't processed at boot time. Details:

Contents of /etc/crypttab:
```
crypttmp1 /dev/vdb5 /dev/urandom cipher=aes-xts-plain64
```

Entries in /var/log/boot.log
```
[[COLOR=#ff0000]FAILED[/COLOR]] Failed to start Cryptography Setup for crypttmp1.
See 'systemctl status systemd-cryptsetup@crypttmp1.service' for details.
[[COLOR=#daa520]DEPEND[/COLOR]] Dependency failed for dev-mapper-crypttmp1.device.
[[COLOR=#daa520]DEPEND[/COLOR]] Dependency failed for Encrypted Volumes.
```

Output of
# systemctl status [EMAIL="systemd-cryptsetup@crypttmp1.servic"]systemd-cryptsetup@crypttmp1.servic[/EMAIL]e :
```
 systemd-cryptsetup@crypttmp1.service - Cryptography Setup for crypttmp1
   Loaded: loaded (/etc/crypttab; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2017-09-21 05:51:31 +07; 7min ago
     Docs: man:crypttab(5)
           man:systemd-cryptsetup-generator(8)
           man:systemd-cryptsetup@.service(8)
  Process: 770 ExecStart=/lib/systemd/systemd-cryptsetup attach crypttmp1 /dev/vdb5 /dev/urandom cipher=aes-xts-plain64 (code=exited, status=1/FAILURE)
 Main PID: 770 (code=exited, status=1/FAILURE)

Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: Starting Cryptography Setup for crypttmp1...
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: systemd-cryptsetup@crypttmp1.service: Main process exited, code=exited, status=1/FAILURE
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: Failed to start Cryptography Setup for crypttmp1.
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: systemd-cryptsetup@crypttmp1.service: Unit entered failed state.
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: systemd-cryptsetup@crypttmp1.service: Failed with result 'exit-code'.
```

Results of
# grep crypttmp1 /var/log/syslog
```
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: Starting Cryptography Setup for crypttmp1...
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: systemd-cryptsetup@crypttmp1.service: Main process exited, code=exited, status=1/FAILURE
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: Failed to start Cryptography Setup for crypttmp1.
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: Dependency failed for dev-mapper-crypttmp1.device.
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: dev-mapper-crypttmp1.device: Job dev-mapper-crypttmp1.device/start failed with result 'dependency'.
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: systemd-cryptsetup@crypttmp1.service: Unit entered failed state.
Sep 21 05:51:31 ubuntu-1604-amd64 systemd[1]: systemd-cryptsetup@crypttmp1.service: Failed with result 'exit-code'.'
```

Note: when, after boot completes, I run the command

```
sudo cryptdisks_start crypttmp1
```

then the expected encrypted device is created and can be mounted and used.

Question: what failed dependency shall I look for? There are no /etc/fstab entries the /dev/vdb5 device could depend on.

Thanks.

**[Updated: October 09, 2017]**: the below configuration, surprisingly, works:

/etc/crypttab:
```
cryptswap1 UUID=790ea2bf-5587-4c84-a3b7-ed7e832b79e2 /dev/urandom swap,offset=1024,cipher=aes-xts-plain64
ctmp  /dev/sdb6 /dev/urandom tmp
```

/etc/fstab:
```
/dev/mapper/ctmp /tmp ext4 defaults,noatime 0 2
/dev/mapper/cryptswap1 none swap sw 0 0
```

I had issues with /tmp always being mounted with permissions mask 0755; however, after I logged in to init 1 mode and did

```
chmod 1777 /tmp
```

the above permissions problem was gone.

<irony>I thank this forum for your extremely detailed and fruitful assistance</irony>. I posted bug report on the original problem; perhaps it will some day be at least read.

---

