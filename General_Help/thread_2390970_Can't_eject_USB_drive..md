---
title: "Can't eject USB drive."
date: 2018-05-04
forum: General Help
---

### Post by donsy on 2018-05-04
I have numerous USB drives over many brand names but I'm having trouble with one in particular. It's a Kingston USB 2.0 1GB drive and it won't eject. It will unmount just fine but when I eject I get the following message:


```
The device <volume name> is being ejected. This may take some time.

```And after a long delay I get a popup:

```
[SIZE=3]Failed to eject "<volume name>".[/SIZE]
Timeout was reached.

```

I checked the drive with **badblocks** and no errors were reported. And it happens even if I zero out the entire drive with ... ```
dd if=/dev/zero of=/dev/sdb
``` ... and create a new partition table, partition, and filesystem on it.


As I said before, it only happens with this one USB drive, all others will eject just fine.

xubuntu 18.04

---

### Post by HermanAB on 2018-05-04
Once it is unmounted, it is ejected.  

The 'eject' thing is a word for people who don't understand mount and unmount.

---

### Post by donsy on 2018-05-04
> **HermanAB said:**
> Once it is unmounted, it is ejected.  

The 'eject' thing is a word for people who don't understand mount and unmount.

Apparently it isn't ejected when unmounted. If I just unmount it and pull it out I still get the popup:
```
[COLOR=#000000][FONT=&amp][SIZE=3]Failed to eject "<volume name>".[/SIZE]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Timeout was reached.[/FONT][/COLOR]
```

---

### Post by Dennis N on 2018-05-04
If it is unmounted, you can select it again in file manager side pane and remount it. If it is ejected, then you cannot mount it again without reinserting.

---

### Post by Morbius1 on 2018-05-04
Could be this bug: [URL="https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1762595"]Thunar incorrectly thinks USB storage device hasn't finished ejecting 

[/URL]Also mentioned here:
[https://ubuntuforums.org/showthread.php?t=2390509](https://ubuntuforums.org/showthread.php?t=2390509)

---

### Post by donsy on 2018-05-04
> **Morbius1 said:**
> Could be this bug: [URL="https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1762595"]Thunar incorrectly thinks USB storage device hasn't finished ejecting 

[/URL]Also mentioned here:
[https://ubuntuforums.org/showthread.php?t=2390509](https://ubuntuforums.org/showthread.php?t=2390509)
Yes, that is exactly the problem. Thank you, now I know the bug can be fixed and I don't have to throw away a perfectly good USB drive.

---

