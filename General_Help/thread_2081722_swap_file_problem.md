---
title: "swap file problem?"
date: 2012-11-07
forum: General Help
---

### Post by watgrad on 2012-11-07
Hello - during boot of ubuntu there is a 23 second delay where ubuntu seems to be 'creating' a swap file. Dmesg shows:

[    6.583344] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   29.434501] Adding 4748040k swap on /dev/sda6.  Priority:-1 extents:1 across:4748040k

I have a dual boot Macbookpro 8,1 with OS X and Ubuntu 12.10.

Is there a way to permanently set the swap file so this delay doesn't happen for every boot?

Thanks for any help!

---

### Post by gacb on 2012-11-08
I have the same issue in 12.10. It would be appreciated to get some response.

---

### Post by watgrad on 2013-05-23
Still see this on 13.04, the creation of swap is faster...10 sec
[    5.840488] usb 1-1.1.3: Manufacturer: Apple Inc.
[   15.538489] Adding 4748040k swap on /dev/sda6.  Priority:-1 extents:1 across:4748040k

---

### Post by scbingham on 2013-05-23
When I installed 12.04 LTS, I chose the option to create a permanent swap partition. Did you not do that?
If not, have a look at this:
[http://askubuntu.com/questions/33697/adding-swap-partition-after-system-installation](http://askubuntu.com/questions/33697/adding-swap-partition-after-system-installation)

Hope this helps.

---

### Post by watgrad on 2013-05-24
Thank you for your reply.
Yes - I have a line like the one suggested in the article in fstab and the uuid matches my swap partition (which I created with installation).
I'm not sure why ubuntu wants to recreate the swap for every boot...

My fstab line for swap:
# swap was on /dev/sda6 during installation
UUID=db47b22a-7414-40bf-be55-2d2d1006ca60 none            swap    sw              0       0

output of  "sudo blkid /dev/sda6"  - sda6 is my swap partition:


/dev/sda6: UUID="db47b22a-7414-40bf-be55-2d2d1006ca60" TYPE="swap"

---

### Post by scbingham on 2013-05-24
That looks pretty much the same as mine, so from that point of view, all looks well.

Sorry I can't help further.

---

