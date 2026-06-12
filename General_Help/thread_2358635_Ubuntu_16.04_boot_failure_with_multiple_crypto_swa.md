---
title: "Ubuntu 16.04 boot failure with multiple crypto swap disks"
date: 2017-04-15
forum: General Help
---

### Post by bugrider2 on 2017-04-15
Linux 4.8.0-46-generic #49~16.04.1-Ubuntu SMP Fri Mar 31 14:51:03 UTC 2017

**crypttab**
cryptswap1 /dev/disk/by-id/[...] /dev/urandom swap,cipher=aes-xts-plain64,hash=sha256,size=512
cryptswap2 /dev/disk/by-id/[...] /dev/urandom swap,cipher=aes-xts-plain64,hash=sha256,size=512
cryptswap3 /dev/disk/by-id/[...] /dev/urandom swap,cipher=aes-xts-plain64,hash=sha256,size=512
cryptswap4 /dev/disk/by-id/[...] /dev/urandom swap,cipher=aes-xts-plain64,hash=sha256,size=512

**fstab**
[...]
/dev/mapper/cryptswap1 none swap [COLOR=#ff0000]noauto[/COLOR],nofail,pri=63 0 0
/dev/mapper/cryptswap2 none swap [COLOR=#ff0000]noauto[/COLOR],nofail,pri=62 0 0
/dev/mapper/cryptswap3 none swap [COLOR=#ff0000]noauto[/COLOR],nofail,pri=61 0 0
/dev/mapper/cryptswap4 none swap [COLOR=#ff0000]noauto[/COLOR],nofail,pri=60 0 0

When [COLOR=#ff0000]noauto[/COLOR] is removed from the fstab lines, boot hangs on swap activation:
[ATTACH=CONFIG]274567[/ATTACH]

Most attempts, it will activate two cryptswaps - and which two of the four seems to be random.
Picture above shows a relatively rare case of only one cryptswap being activated.

With [COLOR=#ff0000]noauto[/COLOR] present, the result is similar, but of course the problem does not cause boot failure.
From the various excerpts in the appendix below, one can see that the crypto setup with mkswap is successful.
The swap volumes can be activated manually after login.
However, during boot it does not find some of the mapped cryptoswap devices.
After login, the "missing" devices do exist, but the boot jobs are still running:

**systemctl list-jobs**
JOB UNIT                         TYPE  STATE  
 35 dev-mapper-cryptswap1.device start running
 32 dev-mapper-cryptswap2.device start running
 42 dev-mapper-cryptswap3.device start running
3 jobs listed.

**systemctl show 35**
Id=35
Unit=dev-mapper-cryptswap1.device
JobType=start
State=running

[COLOR=#ee82ee]**I am running out of ideas how to further debug this.**[/COLOR]

[COLOR=#0000ff]**Anybody got some clues??**[/COLOR]

Best Regards...[U][B]



APPENDIX[/B][/U]

**journalctl**
Apr 15 21:46:23 puweb systemd[1]: Starting Cryptography Setup for cryptswap1...
Apr 15 21:46:23 puweb systemd-cryptsetup[510]: Set cipher aes, mode xts-plain64, key size 512 bits for device /dev/disk/by-id/ata-VBO
Apr 15 21:46:23 puweb systemd[1]: Starting Cryptography Setup for cryptswap3...
Apr 15 21:46:23 puweb systemd-cryptsetup[519]: Set cipher aes, mode xts-plain64, key size 512 bits for device /dev/disk/by-id/ata-VBO
Apr 15 21:46:23 puweb systemd[1]: Starting Cryptography Setup for cryptswap2...
Apr 15 21:46:23 puweb systemd-cryptsetup[525]: Set cipher aes, mode xts-plain64, key size 512 bits for device /dev/disk/by-id/ata-VBO
Apr 15 21:46:23 puweb kernel: AVX version of gcm_enc/dec engaged.
Apr 15 21:46:23 puweb kernel: AES CTR mode by8 optimization enabled
Apr 15 21:46:23 puweb systemd[1]: Starting Cryptography Setup for cryptswap4...
Apr 15 21:46:23 puweb systemd-cryptsetup[577]: Set cipher aes, mode xts-plain64, key size 512 bits for device /dev/disk/by-id/ata-VBO
[...]
Apr 15 21:46:23 puweb systemd[1]: Started Cryptography Setup for cryptswap3.
Apr 15 21:46:23 puweb mkswap[928]: Setting up swapspace version 1, size = 255 MiB (267382784 bytes)
Apr 15 21:46:23 puweb mkswap[928]: no label, UUID=7fd0ca8d-b3aa-4d12-845d-c7050939bd7b
Apr 15 21:46:23 puweb systemd[1]: Started Cryptography Setup for cryptswap2.
Apr 15 21:46:23 puweb mkswap[932]: Setting up swapspace version 1, size = 255 MiB (267382784 bytes)
Apr 15 21:46:23 puweb mkswap[932]: no label, UUID=8adf6ddc-9666-4cb0-a26e-3cef22ec2340
Apr 15 21:46:23 puweb systemd[1]: Started Cryptography Setup for cryptswap1.
Apr 15 21:46:23 puweb mkswap[938]: Setting up swapspace version 1, size = 255 MiB (267382784 bytes)
Apr 15 21:46:23 puweb mkswap[938]: no label, UUID=078fa266-e057-4eb3-9310-0f08e59dc86e
Apr 15 21:46:23 puweb systemd[1]: Started Cryptography Setup for cryptswap4.
Apr 15 21:46:23 puweb systemd[1]: Found device /dev/mapper/cryptswap4.
Apr 15 21:46:23 puweb systemd[1]: Reached target Encrypted Volumes.


**systemctl --all**
  dev-disk-by\x2did-dm\x2dname\x2dcryptswap4.device loaded    active   plugged         /dev/disk/by-id/dm-name-cryptswap4
  dev-disk-by\x2did-dm\x2duuid\x2dCRYPT\x2dPLAIN\x2dcryptswap4.device loaded    active   plugged         /dev/disk/by-id/dm-uuid-CRYPT-PLAIN-cryptswap4
  dev-mapper-cryptswap1.device                      loaded    inactive dead      start dev-mapper-cryptswap1.device
  dev-mapper-cryptswap2.device                      loaded    inactive dead      start dev-mapper-cryptswap2.device
  dev-mapper-cryptswap3.device                      loade[COLOR=#000000]d    inactive dead      start dev-mapper-cryptswap3.device
  dev-mapper-cryptswap4.device                      loaded    active   plugged         /dev/mapper/cryptswap4
  [/COLOR][COLOR=#000000]systemd-cryptsetup@cryptswap1.servic[/COLOR][COLOR=#000000]e             loaded    active   exited          Cryptography Setup for cryptswap1
  [/COLOR][COLOR=#000000]systemd-cryptsetup@cryptswap2.servic[/COLOR][COLOR=#000000]e             loaded    active   exited          Cryptography Setup for cryptswap2
  [/COLOR][COLOR=#000000]systemd-cryptsetup@cryptswap3.servic[/COLOR][COLOR=#000000]e             loaded    active   exited          Cryptography Setup for cryptswap3
  [/COLOR][COLOR=#000000]systemd-cryptsetup@cryptswap4.servic[/COLOR][COLOR=#000000]e             loaded    active   exited          Cryptography Setup for cryptswap4
  system-systemd\x2dcryptsetup.slice                loaded    active   active          system-systemd\x2dcryptsetup.slice
  cryptsetup-pre.target                             loaded    inactive dea[/COLOR]d            Encrypted Volumes (Pre)
  cryptsetup.target                                 loaded    active   active          Encrypted Volumes

[COLOR=#000000]
[/COLOR]**[COLOR=#000000]systemctl status [/COLOR][COLOR=#000000]systemd-cryptsetup@cryptswap1.servic[/COLOR][COLOR=#000000]e[/COLOR]**[COLOR=#000000]
&#9679; [/COLOR][COLOR=#000000]systemd-cryptsetup@cryptswap1.servic[/COLOR][COLOR=#000000]e - Cryptography Setup for cryptswap1
   Loaded: loaded (/etc/crypttab; bad; vendor preset: enabled)
   Active: active (exited) since Sa 2017-04-15 21:46[/COLOR]:23 CEST; 13min ago
     Docs: man:crypttab(5)
           man:systemd-cryptsetup-generator(8)
           man:systemd-cryptsetup@.service(8)
  Process: 932 ExecStartPost=/sbin/mkswap /dev/mapper/cryptswap1 (code=exited, status=0/SUCCESS)
  Process: 510 ExecStart=/lib/systemd/systemd-cryptsetup attach cryptswap1 /dev/disk/by-id/[...]
 Main PID: 510 (code=exited, status=0/SUCCESS)
Apr 15 21:46:23 puweb systemd[1]: Starting Cryptography Setup for cryptswap1...
Apr 15 21:46:23 puweb systemd-cryptsetup[510]: Set cipher aes, mode xts-plain64, key size 512 bits for device /dev/disk/by-id/[...]
Apr 15 21:46:23 puweb mkswap[932]: Setting up swapspace version 1, size = 255 MiB (267382784 bytes)
Apr 15 21:46:23 puweb mkswap[932]: no label, UUID=8adf6ddc-9666-4cb0-a26e-3cef22ec2340
Apr 15 21:46:23 puweb systemd[1]: Started Cryptography Setup for cryptswap1.

[B][COLOR=#000000]
systemctl status [/COLOR][COLOR=#000000]systemd-cryptsetup@cryptswap4.servic[/COLOR][COLOR=#000000]e[/COLOR][/B][COLOR=#000000]
&#9679; [/COLOR][COLOR=#000000]systemd-cryptsetup@cryptswap4.servic[/COLOR][COLOR=#000000]e - Cryptography Setup for cryptswap4
   Loaded: loaded (/etc/crypttab; bad; vendor pre[/COLOR]set: enabled)
   Active: active (exited) since Sa 2017-04-15 21:46:23 CEST; 15min ago
     Docs: man:crypttab(5)
           man:systemd-cryptsetup-generator(8)
           man:systemd-cryptsetup@.service(8)
  Process: 938 ExecStartPost=/sbin/mkswap /dev/mapper/cryptswap4 (code=exited, status=0/SUCCESS)
  Process: 577 ExecStart=/lib/systemd/systemd-cryptsetup attach cryptswap4 /dev/disk/by-id/[...]
 Main PID: 577 (code=exited, status=0/SUCCESS)
Apr 15 21:46:23 puweb systemd[1]: Starting Cryptography Setup for cryptswap4...
Apr 15 21:46:23 puweb systemd-cryptsetup[577]: Set cipher aes, mode xts-plain64, key size 512 bits for device /dev/disk/by-id/[...]
Apr 15 21:46:23 puweb mkswap[938]: Setting up swapspace version 1, size = 255 MiB (267382784 bytes)
Apr 15 21:46:23 puweb mkswap[938]: no label, UUID=078fa266-e057-4eb3-9310-0f08e59dc86e
Apr 15 21:46:23 puweb systemd[1]: Started Cryptography Setup for cryptswap4.

[B]
systemctl status dev-mapper-cryptswap1.device[/B]
&#9679; dev-mapper-cryptswap1.device
   Loaded: loaded
  Drop-In: /run/systemd/generator/dev-mapper-cryptswap1.device.d
           &#9492;&#9472;90-device-timeout.conf
   Active: inactive (dead)

[B]
systemctl status dev-mapper-cryptswap4.device[/B]
&#9679; dev-mapper-cryptswap4.device - /dev/mapper/cryptswap4
   Follow: unit currently follows state of sys-devices-virtual-block-dm\x2d4.device
   Loaded: loaded
  Drop-In: /run/systemd/generator/dev-mapper-cryptswap4.device.d
           &#9492;&#9472;90-device-timeout.conf
   Active: active (plugged) since Sa 2017-04-15 21:46:23 CEST; 11min ago
   Device: /sys/devices/virtual/block/dm-4
Apr 15 21:46:23 puweb systemd[1]: Found device /dev/mapper/cryptswap4.

---

