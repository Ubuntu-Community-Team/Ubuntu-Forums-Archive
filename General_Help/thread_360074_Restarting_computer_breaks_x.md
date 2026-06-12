---
title: "Restarting computer breaks x"
date: 2007-02-12
forum: General Help
---

### Post by sharperguy on 2007-02-12
Hi

Ever since the last kernel update, I've been having a strange problem.

Every time I restart my computer (or shut-down the boot later), x doesn't come up.

What I then have to do, is go to the .run file for the latest nvidia-glx driver I am using (from the nvidia website) and resinstall it.

Then I can run "sudo gdm" and it works fine.

Also, its not a case of having to recompile the nvidia kernel module, because I used --add-this-kernel to make a new .run file with the kernel module built into it for the current kernel, and using that after boot works fine too.

Kinda strange.

Any help appreciated.

---

### Post by ~LoKe on 2007-02-12
```
sudo nano /etc/default/linux-restricted-modules-common
```
Make the last line look like...
> DISABLED_MODULES="nv"

---

### Post by sda5150 on 2007-02-12
Roll back to your previous version of xserver.conf (I think thats the right file name, someone else might verify this)
I'm not in front of a Linux machine right now so I can't detail the steps on how to do this. But whenever your X configuration changes, it renames the old config to: xserver.conf.2007.02.12.*whatever* If you roll back to that version of the conf file you get your old X configuration back.

---

### Post by sharperguy on 2007-02-13
> **~LoKe said:**
> ```
sudo nano /etc/default/linux-restricted-modules-common
```
Make the last line look like...

Oh yea...

Forgot about that

Just done it and restarting now

edit: yea, worked now thanks :)

---

