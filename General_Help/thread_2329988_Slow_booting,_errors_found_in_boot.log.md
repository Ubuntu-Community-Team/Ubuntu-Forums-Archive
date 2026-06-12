---
title: "Slow booting, errors found in boot.log"
date: 2016-07-06
forum: General Help
---

### Post by checoimg on 2016-07-06
I'm using **Ubuntu MATE 16.04 64 bit.**

My setup is a separate and encrypted **HOME** disk with **XFS** and a **BTRFS** for **ROOT** disk. Two **HDD's** with **EXTENDED** partition type.


[IMG]http://i1085.photobucket.com/albums/j436/checo_evo/blup2.jpg[/IMG]

[IMG]http://i1085.photobucket.com/albums/j436/checo_evo/blup1.jpg[/IMG]

Recently, I noticed a slow booting time an I checked the boot.log at [I]/var/log
[/I]
This is what I found :

```
Timed out waiting for device dev-disk-by\x2duuid-896874fe\x2d2dd8\x2d405e\x2d97c3\x2dc72b0db1b606.device.
[DEPEND] Dependency failed for Cryptography Setup for cryptswap1.
[DEPEND] Dependency failed for Encrypted Volumes.
[DEPEND] Dependency failed for dev-mapper-cryptswap1.device.
[DEPEND] Dependency failed for /dev/mapper/cryptswap1.
[DEPEND] Dependency failed for Swap.
...

```
I don't know what to look for or to ask about this. Any help appreciated. Happy Llamas! :)

---

### Post by wildmanne39 on 2016-07-06
Please use thumbnails or Url's when posting images because many people have slow internet conections and loading pages with large images is very difficult for them.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by checoimg on 2016-07-07
Got it!

---

