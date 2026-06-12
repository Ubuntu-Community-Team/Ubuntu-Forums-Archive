---
title: "My Ubuntu partition runneth over"
date: 2014-03-03
forum: General Help
---

### Post by anemone42 on 2014-03-03
The result of running this command is:

```
lise@lise-HP-620:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sda5         983040 966843     16197   99% /
udev              215029    594    214435    1% /dev
tmpfs             218672    509    218163    1% /run
none              218672      6    218666    1% /run/lock
none              218672      7    218665    1% /run/shm
/dev/sda2      138498092 329586 138168506    1% /media/sda2
/dev/sdb               0      0         0     - /media/HP_SW
lise@lise-HP-620:~$
```

I've solved the problem here and now by deleting 11,000 files I didn't need anymore, but there has to be a better strategry.

Looking around reveals a lot of these guys:

```
/lib/modules/*/kernel/drivers/
```

with about 4,300 files each. Can I delete something here? Or here:

```
/proc
```

---

### Post by westie457 on 2014-03-03
Hi There is no point to deleting anything in '/proc' because it is a virtual file-system.

You might have a lot of old kernels though.

Post the output - in ```
 tags of [CODE][COLOR=#000000][FONT=Ubuntu Mono]dpkg -l | grep linux-image[/FONT][/COLOR]
```

Do you have Synaptic Package Manager installed, if you have it will make life a little easier.

If not and you cannot install it we will try a different way.

Thank you.

---

### Post by Impavidus on 2014-03-03
Apart from the old kernels, there may also be a lot of old kernel headers, using far more inode[COLOR=#000000]s.```
dpkg -l | grep linux-headers
```[FONT=Ubuntu Mono][/FONT][/COLOR]Best to uninstall both old kernels and old kernel headers.

---

### Post by dragonfly41 on 2014-03-03
My partition is filling up .. so this thread prompted me to read further here ..

[http://ubuntuforums.org/showthread.php?t=1587462&highlight=synaptic+package+manager+cleanup+kernels](http://ubuntuforums.org/showthread.php?t=1587462&highlight=synaptic+package+manager+cleanup+kernels)

and I'll now use System Tools > Ubuntu Tweak > Computer Janitor > System > Old Kernels to jettison baggage.

---

### Post by anemone42 on 2014-03-03
Thank you for all the suggestions! Here are some answers.

Unfortunately I have almost no files in /tmp.

Yes, I do have Synaptic Package Manager installed.

Using find | wc -l to count files:

```
/home                34176
/lib                97555
/media                354748
/proc                102636
/sys                28391
/usr                814481
/var                24581

/media/sda2            354744

/usr/lib            32451
/usr/share            158893
/usr/src            614637

/usr/src/linux-headers-3.2.0-34                    13877
/usr/src/linux-headers-3.2.0-34-generic            8415
/usr/src/linux-headers-3.2.0-34-generic-pae        8434
/usr/src/linux-headers-3.2.0-35                    13877
/usr/src/linux-headers-3.2.0-35-generic            8415
/usr/src/linux-headers-3.2.0-35-generic-pae        8434
/usr/src/linux-headers-3.2.0-36                    13877
/usr/src/linux-headers-3.2.0-36-generic            8415
/usr/src/linux-headers-3.2.0-36-generic-pae        8434
/usr/src/linux-headers-3.2.0-37                    13877
/usr/src/linux-headers-3.2.0-37-generic            8415
/usr/src/linux-headers-3.2.0-37-generic-pae        8434
...
/usr/src/linux-headers-3.2.0-58                    13879
/usr/src/linux-headers-3.2.0-58-generic            8420
/usr/src/linux-headers-3.2.0-58-generic-pae        8439
/usr/src/linux-headers-3.2.0-59                    13879
/usr/src/linux-headers-3.2.0-59-generic            8420
/usr/src/linux-headers-3.2.0-59-generic-pae        8439

$ dpkg -l | grep linux-image
rc  linux-image-2.6.38-12-generic          2.6.38-12.51                                        Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-2.6.38-8-generic           2.6.38-8.42                                         Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-3.0.0-12-generic           3.0.0-12.20                                         Linux kernel image for version 3.0.0 on x86/x86_64
...
ii  linux-image-3.2.0-59-generic           3.2.0-59.90                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.59.70                                         Generic Linux kernel image
$ dpkg -l | grep linux-image | wc -l
39

$ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-34                 3.2.0-34.53                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic         3.2.0-34.53                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-34-generic-pae     3.2.0-34.53                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
...
ii  linux-headers-generic                  3.2.0.59.70                                         Generic Linux kernel headers
ii  linux-headers-generic-pae              3.2.0.59.70                                         Generic Linux kernel headers
$ dpkg -l | grep linux-headers | wc -l
62

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        15G   13G  1.5G  90% /
udev            965M  4.0K  965M   1% /dev
tmpfs           389M  944K  388M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            972M  492K  971M   1% /run/shm
/dev/sda2       281G  150G  132G  54% /media/sda2
/dev/sdb        118M   17M  102M  14% /media/HP_SW
```

---

### Post by sandyd on 2014-03-03
> **anemone42 said:**
> Thank you for all the suggestions! Here are some answers.

Unfortunately I have almost no files in /tmp.

Yes, I do have Synaptic Package Manager installed.

Using find | wc -l to count files:

```
/home                34176
/lib                97555
/media                354748
/proc                102636
/sys                28391
/usr                814481
/var                24581

/media/sda2            354744

/usr/lib            32451
/usr/share            158893
/usr/src            614637

/usr/src/linux-headers-3.2.0-34                    13877
/usr/src/linux-headers-3.2.0-34-generic            8415
/usr/src/linux-headers-3.2.0-34-generic-pae        8434
/usr/src/linux-headers-3.2.0-35                    13877
/usr/src/linux-headers-3.2.0-35-generic            8415
/usr/src/linux-headers-3.2.0-35-generic-pae        8434
/usr/src/linux-headers-3.2.0-36                    13877
/usr/src/linux-headers-3.2.0-36-generic            8415
/usr/src/linux-headers-3.2.0-36-generic-pae        8434
/usr/src/linux-headers-3.2.0-37                    13877
/usr/src/linux-headers-3.2.0-37-generic            8415
/usr/src/linux-headers-3.2.0-37-generic-pae        8434
...
/usr/src/linux-headers-3.2.0-58                    13879
/usr/src/linux-headers-3.2.0-58-generic            8420
/usr/src/linux-headers-3.2.0-58-generic-pae        8439
/usr/src/linux-headers-3.2.0-59                    13879
/usr/src/linux-headers-3.2.0-59-generic            8420
/usr/src/linux-headers-3.2.0-59-generic-pae        8439

$ dpkg -l | grep linux-image
rc  linux-image-2.6.38-12-generic          2.6.38-12.51                                        Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-2.6.38-8-generic           2.6.38-8.42                                         Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-3.0.0-12-generic           3.0.0-12.20                                         Linux kernel image for version 3.0.0 on x86/x86_64
...
ii  linux-image-3.2.0-59-generic           3.2.0-59.90                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.59.70                                         Generic Linux kernel image
$ dpkg -l | grep linux-image | wc -l
39

$ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-34                 3.2.0-34.53                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic         3.2.0-34.53                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-34-generic-pae     3.2.0-34.53                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
...
ii  linux-headers-generic                  3.2.0.59.70                                         Generic Linux kernel headers
ii  linux-headers-generic-pae              3.2.0.59.70                                         Generic Linux kernel headers
$ dpkg -l | grep linux-headers | wc -l
62

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        15G   13G  1.5G  90% /
udev            965M  4.0K  965M   1% /dev
tmpfs           389M  944K  388M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            972M  492K  971M   1% /run/shm
/dev/sda2       281G  150G  132G  54% /media/sda2
/dev/sdb        118M   17M  102M  14% /media/HP_SW
```
You might need to make a larger root partition - 15G is too small.

---

### Post by anemone42 on 2014-03-03
Uninstalling some older versions of Ubuntu seems like a good idea, so I'm going to try that. Thanks for the help!

---

### Post by Impavidus on 2014-03-03
Uninstall all **linux-image-*** and **linux-headers-*** packages with versions below 3.2.0-58. This should be easy in synaptic.

---

