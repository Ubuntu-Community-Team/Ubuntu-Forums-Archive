---
title: "Never installed kernel keeps giving errors initramfs"
date: 2014-06-13
forum: General Help
---

### Post by markosjal on 2014-06-13
I keep seeing this error when using update-initramfs , although I have never installed the kernel mentioned, as mine are 3.13.x:

WARNING: missing /lib/modules/3.14.2-amdfixes5+
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.14.2-amdfixes5+: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_SqFQau/lib/modules/3.14.2-amdfixes5+/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_SqFQau/lib/modules/3.14.2-amdfixes5+/modules.builtin: No such file or directory

I am running trusty 64 bit
How do I get rid of this?

---

### Post by Bucky Ball on 2014-06-13
You could run these three commands, if you haven't already, and see if it fixes.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by markosjal on 2014-06-13
Did that last night before posting and agan just now seems to want to remove linux-headers-generic, not sure why

---

### Post by Bucky Ball on 2014-06-13
Probably to replace it with a newer version. I presume you are hitting 'n' when you see this so are not going ahead with the update/upgrade?

---

### Post by markosjal on 2014-06-18
at this point I have copied the image and borked it in several ways several times, including dist-upgrade. The kernel referenced is a testing version if I am not mistaken which I am certain have never installed 3.14.2. dist-upgrade installs 3.13.0-29 not 3.14.2 

Installed the kernel 3.14.2 and from what I can tell from the beginning even bewfore that kernel is installed I see references to 3.14.2-amdfixes5+ but have no clue where that comes from, and even with that kernel installed the errors are still present

---

### Post by Anti-Liberal on 2014-06-19
I have the exact same issue.

---

### Post by Bucky Ball on 2014-06-19
> **Anti-Liberal said:**
> I have the exact same issue.

Welcome. What exact same issue? You have a kernel installed which you didn't install yourself and you are getting the exact same errors the OP is getting when you update-initramfs? I.e.:

[QUOTE=markosjal ]I keep seeing this error when using update-initramfs , although I have never installed the kernel mentioned, as mine are 3.13.x:

```
WARNING: missing /lib/modules/3.14.2-amdfixes5+
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.14.2-amdfixes5+: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_SqFQau/lib/modules/3.14.2-amdfixes5+/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_SqFQau/lib/modules/3.14.2-amdfixes5+/modules.builtin: No such file or directory
```[/QUOTE]

If not, I suggest you start a new thread in the appropriate forum and with a descriptive title and keep an eye on this. Attempting to support two users gets confusing, is unfair to the OP, dilutes community effort and therefore is avoided here. Thanks.

---

### Post by Anti-Liberal on 2014-06-19
> **Bucky Ball said:**
> Welcome. What exact same issue? You have a kernel installed which you didn't install yourself and you are getting the exact same errors the OP is getting when you update-initramfs? I.e.:

Yes, exactly that issue. I thought it was obvious since that was the only issue the OP described.

---

### Post by Bucky Ball on 2014-06-20
Just checking. We have users crashing in and hijacking threads to outline problems that are not exactly the same as the one the original poster is asking for support about on a regular basis. Not the done thing here and they are moved to new threads of their own with appropriate thread titles.

And no, it wasn't obvious or I wouldn't have asked. If it was I'd presume that everyone that crashes a thread with a one-liner like 'I have exactly the same problem' was obviously the same problem as the OP's. 99% of the time they're not. ;)

---

### Post by markosjal on 2014-08-02
I solved this with 

[code]
sudo update-initramfs -d -k 3.14.2-amdfixes5+

{/code]

-d delete

- k <version>

---

### Post by fedupwithjunk on 2014-08-16
> **markosjal said:**
> I solved this with 

```

sudo update-initramfs -d -k 3.14.2-amdfixes5+


```


This solution worked for me, 

I have the same error, On a relatively fresh XBMCbuntu install I just ran an update and got this. Google reveals multiple instances of similar problems. Somebody got some code wrong ?
```
*update-initramfs: Generating /boot/initrd.img-3.14.2-amdfixes5+*
*grep: /boot/config-3.14.2-amdfixes5+: No such file or directory*
*WARNING: missing /lib/modules/3.14.2-amdfixes5+*
*Device driver support needs thus be built-in linux image!*
*depmod: ERROR: could not open directory /lib/modules/3.14.2-amdfixes5+: No such file or directory*
*depmod: FATAL: could not search modules: No such file or directory*

```

---

