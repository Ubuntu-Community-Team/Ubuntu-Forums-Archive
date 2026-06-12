---
title: "ubuntu 12.10 slow boot time"
date: 2012-12-20
forum: General Help
---

### Post by domak on 2012-12-20
Since upgrading from precise (12.04), my ubuntu PC boot very slowly.

I checked dmesg and I see a big gap:

```

[    2.769327] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.382362] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    3.382366] EXT4-fs (sda5): write access will be enabled during recovery
[    4.625913] EXT4-fs (sda5): recovery complete
[    4.636909] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   28.456177] Adding 2096444k swap on /dev/sda6.  Priority:-1 extents:1 across:2096444k 
[   28.461205] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.467773] udevd[396]: starting version 175

```

Any idea of what append here? I have not found any clue in other logs and don't know how to resolve this.

regards

Christophe

---

### Post by Pjotr123 on 2012-12-20
Looks like partition sda5 has a problem: needed recovery... 

Maybe something to do with upgrade woes? Did you perform a clean upgrade with previous formatting, or did you upgrade from within an existing 12.04?

---

### Post by domak on 2012-12-20
sda5 is my system partition (I have a dual boot... even if I can't remember the last time I've started vista).

I did an upgrade from 12.04 (I've done that since the first install, long time ago).

What is puzzled me is the difference of time between the last message indicated that the sda5 is mounted and the swap mounted. 
May be the sda5 is not really monted when the message
```

[    4.636909] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)

```

is displayed?

In generated /etc/fstab, I have this entry:
```

# Entry for /dev/sda5 :
UUID=f6e51472-f0e4-4466-98c9-3f064ec4875f / ext4 errors=remount-ro 0 1

```

Do you see anything wrong?

---

### Post by Pjotr123 on 2012-12-20
I see nothing wrong, but I advise a clean reinstallation nevertheless. It will possibly fix this problem, and if not, will make debugging a lot easier...

It'll take you about 2 hours (30 minutes install, 90 minutes polishing). This is a how-to:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

---

### Post by domak on 2012-12-20
Well, it's not as easy... I've spent many days to have my computer working:
[LIST]
[*]I have 2 gpu on my sony laptop (this part was very hard to configure)
[*]I use Citrix client (the post install script is wrong and it must be manually updated)
[*]I have to install oracle java (for java fx)
[*]I need to install the driver for my scanner
[*]etc, etc. (I'm sure I forget a lot of post install operations)
[/LIST]

What I've discovered with bootchart is that ureadahead took more that 20s. I follow the advise here: [http://ubuntuforums.org/showthread.php?t=1434502]("http://ubuntuforums.org/showthread.php?t=1434502") and remove pack files in /var/lib/ureadahead but now I have the error:```

[    6.874423] EXT4-fs (sda5): recovery complete
[    6.885446] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    9.618837] init: ureadahead main process (326) terminated with status 5
[   10.761186] Adding 2096444k swap on /dev/sda6.  Priority:-1 extents:1 across:2096444k 
[   11.866977] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

```

and the pack files are not recreated.

---

### Post by domak on 2012-12-20
I reinstalled ureadahead package and the error disapear. The boot is still slow but now I know it is related to ureadahead files loading process.  

When I dump the process, I see there are a lot of file that may be not necessary to load at startup like chromium browser.

I let you know if I'm sucessfull to enhance that.

---

### Post by peterprettenhofer on 2013-02-27
@domak: thanks for investigating - I've noticed the same problem after upgrading to 12.10 - have you found a solution yet?

---

