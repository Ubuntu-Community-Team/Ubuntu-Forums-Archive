---
title: "How to ricreate swap file?"
date: 2007-08-02
forum: General Help
---

### Post by mcastel on 2007-08-02
Hello,

I've istalled wubi on my system and it runs nicely, apart from the fact that it can't use the swap disk: I had to rename the file swap.virtual.disk to swap.virtual.disk.old in order to make the system to actually boot (following suggestions in this forum). Anyway, if I try to restore my old swap file, the system always stops during boot. Is there a way (from linux or windows) to generate a correct swap file?

Thanks in advance for any help ;)

---

### Post by tuxcantfly on 2007-08-03
if you want to have a 1 GB swapfile (adjust line 3 for size):

```
cd /media/host/wubi/disks
sudo rm swap.virtual.disk.old
dd if=/dev/zero of=extra.virtual.disk bs=1000 count=0 seek=$[1000*1000]
sudo mkswap -f ./swap.virtual.disk
```

Then, run this command :
```

sudo swapon ./swap.virtual.disk
```

And if there's any error messages, post them here.
Then type this command to see if it worked:

```
free
```

And if, under the "swap" column and "total" row, the number is above 0, then it worked.

---

### Post by mcastel on 2007-08-06
Hello,

first of all, thanks for your help :)

Yes there is in fact a problem while I run your procedure: namely,
when I give the command 

$sudo swapon extra.virtual.disk (I assume is "extra" and not "swap", is it correct?)
the system respond

"swapon: skipping file extra.virtual.disk - it appear to have holes."

Is something that depends on my hard disk, maybe?

Thanks in advance, ;)

[QUOTE=tuxcantfly;3127246]if you want to have a 1 GB swapfile (adjust line 3 for size):

```
cd /media/host/wubi/disks
sudo rm swap.virtual.disk.old
dd if=/dev/zero of=extra.virtual.disk bs=1000 count=0 seek=$[1000*1000]
sudo mkswap -f ./swap.virtual.disk
```

Then, run this command :
```

sudo swapon ./swap.virtual.disk
```

And if there's any error messages, post them here.

---

### Post by tuxcantfly on 2007-08-06
> "swapon: skipping file extra.virtual.disk - it appear to have holes."

Instead of using this dd command:

> dd if=/dev/zero of=extra.virtual.disk bs=1000 count=0 seek=$[1000*1000]

use this:

```
dd if=/dev/zero of=extra.virtual.disk bs=1M count=1k
```

do the rest the same

---

### Post by mcastel on 2007-08-07
Thanks again for your kind help, tuxcantfly ;)

Maybe I found a "workaround", meanwhile... I tried to mount as swap an old unused partition in my system, of 1 gb. I was not sure that I could use "external" partition in wubi, but I realized that I can mount/unmount other partition as the true Ubuntu installation. So  I simply made

$ sudo swapon /mnt/sda2

and the command "free" told me I was succesfull!

Anyway, I wonder, can I expect  some difference of performance, bewteen using a "virtual" swap or a true hard disk partition...?

Kind regards,

---

### Post by ago on 2007-08-07
If anything using a dedicated partition will be faster

---

