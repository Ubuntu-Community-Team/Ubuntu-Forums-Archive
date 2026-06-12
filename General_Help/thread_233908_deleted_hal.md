---
title: "deleted hal"
date: 2006-08-10
forum: General Help
---

### Post by professor_chaos on 2006-08-10
In trying to fix a hal error I deleted user hal thinking reinstalling would restore that user. Anyone know how the best way to get him back. Or can someone post hal's properties so I can add him. Thanks :D

Also, do you have a hal group? If so, that info would help as hal's group is gone.

---

### Post by steve.horsley on 2006-08-10
This is the line from my /etc/passwd:
> haldaemon:x:108:108:Hardware abstraction layer,,,:/var/run/hal:/bin/false
And here are the entries in /etc/group:
> cdrom:x:24:haldaemon,steve
floppy:x:25:haldaemon,steve
plugdev:x:46:haldaemon,steve
haldaemon:x:108:
So haldaemon had its own group and also belonged to 3 other groups

---

### Post by mlind on 2006-08-10
I would probably purge hal package and then install it back. aptitude reinstall may work,
but I think in this case it will skip the postinstall part because hal settings are still present.

So, try reinstalling first
```

sudo aptitude reinstall hal

```

If this doesn't create haldaemon user/group, try purge and install
```

sudo dpkg -P --force-depends hal
sudo aptitude install hal

```

If you want to add hal properties manually, see /var/lib/dpkg/info/hal.postinst

---

### Post by professor_chaos on 2006-08-10
thanks steve

---

### Post by professor_chaos on 2006-08-10
aptitude wants to remove 250 packages that I would like to keep, so I did this instead....

```
sudo dpkg -P --force-depends hal
sudo apt-get install hal
```

Everything installed fine, but still no user=hal.

I will read the postinstall script and see how to do it manually. Thanks mlind

---

### Post by professor_chaos on 2006-08-10
I just reread this thread and it occured to me that you both are referring to haldemon and not hal. I have haldemon, its hal that I deleted. This machine I am on has been dist-upgraded from hoary. I looked at a coworkers machine with a fresh dapper install and there is no user hal there.

Either way, deleting hal, caused me not to be able to mount my usb device. 

> unable to mount the selected volume
error: could not execute pmount

---

### Post by mlind on 2006-08-10
> **professor_chaos said:**
> aptitude wants to remove 250 packages that I would like to keep, so I did this instead....

```
sudo dpkg -P --force-depends hal
sudo apt-get install hal
```

Everything installed fine, but still no user=hal.

I will read the postinstall script and see how to do it manually. Thanks mlind

That user should be called **haldaemon**.

---

### Post by mlind on 2006-08-10
> **professor_chaos said:**
> I just reread this thread and it occured to me that you both are referring to haldemon and not hal. I have haldemon, its hal that I deleted. This machine I am on has been dist-upgraded from hoary. I looked at a coworkers machine with a fresh dapper install and there is no user hal there.

Either way, deleting hal, caused me not to be able to mount my usb device.

There's no user hal anymore. You need to have group called **plugdev** and be on that group to be able to mount USB devices.

```

$ cat /etc/group | grep plugdev
plugdev:x:46:haldaemon,mlind

```

To add this group if it doesn't exist
```

sudo addgroup --gid 46 plugdev

```

---

### Post by professor_chaos on 2006-08-10
> There's no user hal anymore. You need to have group called plugdev and be on that group to be able to mount USB devices.

Thanks mlind, adding myself to plugdev did the trick.

---

